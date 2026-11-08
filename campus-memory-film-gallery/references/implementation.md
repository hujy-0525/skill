# Implementation reference

## Recommended markup

Use one modal shell per page. Populate its reel for the selected institution.

```html
<button class="campus-trigger" data-campus="school-key" aria-haspopup="dialog">...</button>
<div class="campus-modal" hidden>
  <div class="campus-modal-backdrop"></div>
  <section role="dialog" aria-modal="true">
    <div class="campus-film-stage"><div class="campus-film-track"></div></div>
    <div class="campus-photo-focus" hidden>...</div>
  </section>
</div>
```

Each real frame and seamless duplicate uses the same film structure:

```html
<figure class="campus-film-frame">
  <i class="film-perf top"></i>
  <span class="film-image"><img></span>
  <i class="film-perf bottom"></i>
</figure>
```

Generate sprocket holes with a repeating linear gradient. Place them on top and bottom because the browsing direction is horizontal; left/right holes make each photo feel like a separate portrait frame.

## Reel motion

Keep a continuous `travel` value and set the track transform inside one `requestAnimationFrame` loop. The reel contains two copies of the same frame sequence. When travel reaches the width of the first sequence, wrap it with modulo arithmetic.

```js
const velocity = pointerInside
  ? (Math.abs(pointerBias) < .07 ? 0 : Math.sign(pointerBias) * Math.pow(Math.abs(pointerBias), 1.55) * .19)
  : .038;
travel = (travel + delta * velocity + cycleWidth) % cycleWidth;
track.style.transform = `translate3d(${origin - travel}px, -50%, 0)`;
```

`pointerBias` is the pointer x-position normalized to `-1..1` around the viewport center. Positive velocity moves the reel left; negative velocity moves it right.

## Full-image fitting

Never infer the focus frame from the thumbnail box. Wait for the selected image to load and use its natural dimensions.

```js
const ratio = image.naturalWidth / image.naturalHeight;
const maxW = innerWidth * .88 - horizontalFilmPadding;
const maxH = innerHeight * .78 - verticalFilmPadding;
let width = maxW;
let height = width / ratio;
if (height > maxH) {
  height = maxH;
  width = height * ratio;
}
film.style.setProperty('--focus-w', `${width}px`);
film.style.setProperty('--focus-h', `${height}px`);
```

The focus image must also use `width:100%`, `height:100%`, and `object-fit:contain`. The surrounding film frame should use the computed custom properties rather than a fixed landscape ratio.

## Image preparation

- Preserve aspect ratio and EXIF orientation.
- Create delivery copies with a longest edge around 2000–2400px unless the product requires zoom detail.
- Prefer WebP/AVIF when the current project pipeline supports them; otherwise use quality-controlled JPEG.
- Do not overwrite the user's source images.
- Preload the first visible frames and lazy-load the rest.

## Verification checklist

- First frame starts at the viewport center.
- Three to four frames are visible on a typical desktop viewport.
- Default motion is leftward and seamless.
- Left pointer position reverses the reel; right position accelerates leftward motion.
- Hover affects one frame and dims the rest.
- Every focused image is complete at landscape, portrait, and square ratios.
- Second click, backdrop, and Escape exit focus.
- Escape from reel closes the modal and returns focus.
- Reduced-motion users can still open, inspect, and close images.
- Mobile layout fits within safe areas and does not crop focused images.

