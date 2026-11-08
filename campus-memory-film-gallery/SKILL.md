---
name: campus-memory-film-gallery
description: Design or implement a campus-memory photo entry as a responsive continuous film-strip gallery. Use when a portfolio, personal site, alumni page, or education timeline needs a location-triggered photo preview, cinematic reel motion, pointer-controlled speed and direction, hover emphasis, or full-image lightbox. Do not use for ordinary static image grids or unrelated carousels.
---

# Campus Memory Film Gallery

Create a restrained editorial memory experience that preserves the surrounding page structure. Treat the gallery as a progressive layer: location trigger, hover preview, continuous reel, then full-image focus.

## Workflow

1. Inspect the host page, existing motion language, image aspect ratios, performance budget, and mobile behavior before changing layout.
2. Preserve the education timeline or source content. Add the gallery through a compact location-style trigger beside the institution name.
3. Build a hover preview with one representative image, institution label, image count, and a short invitation. Do not expose a large gallery before activation.
4. On activation, keep the page in place and apply a light, warm glass blur. Open the reel from the viewport center rather than navigating away.
5. Render one continuous dark film base with sprocket holes on the top and bottom. Size desktop frames so about three to four images are visible at once. Keep the images adjacent with no card-grid gaps.
6. Center the first frame at entry, then move the full reel left at a calm default velocity. Duplicate the reel only for seamless looping; hide duplicate semantics from assistive technology.
7. While the pointer is inside the gallery, use the viewport center as zero. Pointer movement right drives the reel left; movement left drives it right. Increase speed non-linearly with distance from center. Resume the default leftward velocity when the pointer leaves.
8. On frame hover, lift and straighten only that frame. Reduce brightness and saturation of the remaining frames; keep the reel motion smooth.
9. On frame click, pause reel movement and open a warm-glass focus layer. Read the selected image's natural dimensions, fit it inside the viewport without cropping, and resize the film frame to the image aspect ratio. Retain the dark base and top/bottom sprocket holes.
10. Close focus on a second click, backdrop click, or Escape. Escape from the reel closes the gallery and restores focus to the trigger.

## Non-negotiable invariants

- Never crop the focused image. Use natural width and height to calculate its fitted dimensions; use `object-fit: contain` as a safeguard.
- Do not stretch images, force every focused photo into a landscape frame, or hide content behind fixed-height overflow.
- Optimize copies for delivery without changing aspect ratio or discarding source pixels through cropping.
- Keep decorative duplicate frames `aria-hidden`; keep the trigger labeled and focus-restoring.
- Respect `prefers-reduced-motion`: stop automatic reel motion and remove large transforms while preserving browsing and focus behavior.
- Avoid heavy black modal chrome. The film itself may be dark; the surrounding overlay should remain light and visually compatible with an editorial portfolio.
- On touch devices, preserve complete images, provide swipe/drag behavior when practical, and never depend on hover.

## Tuning defaults

- Desktop frame width: `clamp(270px, 26vw, 390px)`.
- Desktop frame height: `clamp(280px, 44vh, 430px)`.
- Default travel velocity: about `38 px/s` leftward.
- Pointer velocity: signed distance from center raised to approximately `1.5–1.7`, capped near `190 px/s`.
- Hover lift: `10–14px`; hover scale no more than `1.03`.
- Side-edge blur: subtle, approximately `1–2px`, applied only near viewport edges.
- Focus content bounds: roughly `88vw` by `78vh`, minus film padding; calculate final width and height from the natural aspect ratio.

Read [references/implementation.md](references/implementation.md) when writing or reviewing the HTML, CSS, and JavaScript implementation.

