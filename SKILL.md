---
name: poetic-print-poster
description: Turn a user's photograph into a poetic 3:4 vintage editorial print poster, or refine an existing poster while preserving its subject and scene. Use when the user asks for a halftone poster, large serif typography integrated with a photo, a warm ivory/pale-color print look, an original-photo inset, or iterative poster edits such as changing palette, subject scale, foliage overlap, or print texture.
---

# Poetic Print Poster

Create or refine one complete portrait poster from the user's photograph. Use the image-generation tool for raster output. Make the design feel like a continuous editorial print, not a collage or mockup.

## Workflow

1. **Identify the target and inspect it.** For a new poster, inspect the uploaded photo. For an edit, identify the exact current poster to modify and inspect it before generating. If the conversation also contains style references, treat them as guidance only; never substitute a reference image for the edit target. When local file paths are available, prefer the exact target path over “most recent image” selection.
2. **Choose the visual anchor.** Select the most recognizable subject or scene element that can rise through the typography without distorting it. Preserve the original subject, pose, scale relationships, viewpoint, and key setting. Do not invent objects or people.
3. **Set the composition.** Use a 3:4 portrait canvas. Reserve roughly the upper third for relatively clean warm ivory or pale cool-toned negative space and two short English poetic lines in a small, restrained typewriter face. Place a small, proportional, uncropped thumbnail of the exact original photo at the upper right, about 15–18% of poster width, with a fine border and the exact label `ORIGINAL`; keep it clear of the poem and focal subject.
4. **Choose one central word.** Select a short English word that fits the photo. Set it in very large uppercase high-contrast serif lettering across the middle. Sample its ink color from the photo and maintain legibility. Let the photographed subject naturally overlap a limited part of the letters and extend above their tops where the scene permits. Adjust type placement and framing before changing subject proportions.
5. **Unify image and type.** Keep the poster a continuous image. Blend using the actual scene's silhouette, light, background color, and halftone density. Avoid a straight horizontal seam, rectangular photo block, cutout halo, hard gradient band, floating subjects, and excessive occlusion. Use fine, clearly visible circular CMYK halftone dots, slight color-ink misregistration, dense in shadows and sparse in highlights. Preserve photographic material qualities.
6. **Write exact copy.** Use two brief, grammatically correct English lines that echo the photo's mood. Keep them short enough for the quiet upper field. Include no extra headline, watermark, or unrelated decoration.
7. **Iterate narrowly.** For follow-up edits, change only the requested dimension (for example, palette, subject scale, letter texture, overlap, or removing a sign). Explicitly lock all approved elements in the edit prompt. Do not redesign from scratch unless asked. If a previous generation changed the wrong subject, return to the exact correct source image and regenerate.
8. **Inspect before finishing.** Check subject identity and pose, 3:4 composition, exact poem and main word, thumbnail completeness and label, readability, requested palette, and whether the requested overlap/texture behaves correctly. If a result violates a key constraint, make a targeted correction rather than claiming it is correct.

## Typography and background interaction

- Keep the central word readable and visually connected to the photograph.
- For botanical scenes, foliage may sit in front of the letters and cover a few strokes when requested. Do not let foliage show through letter interiors unless explicitly requested.
- For glass, water, fur, or other textured subjects, use subtle matte, frosted, paper-grain, or halftone treatments only when they suit the source. Do not apply a texture that obscures the subject or text.
- To create “breathing room,” vary spacing and let the subject and background contour shape the word's edges; avoid arbitrary distortion or excessive transparency.
- Color should come from the photograph. Do not default to blue or sepia. Keep warm ivory relatively clean; a pale green or pale blue paper tone is acceptable when it better suits the scene.

## Prompt construction

For new work, state these parts clearly in the generation prompt:

- **Target/source:** exact uploaded photo; clarify whether it is the edit target or only a style reference.
- **Preserve:** subject identity, scene, perspective, pose, proportions, and relevant objects.
- **Composition:** portrait 3:4, upper negative space, type placement, overlap, original inset.
- **Exact text:** quote the poem, central word, and `ORIGINAL` label verbatim.
- **Print treatment:** sampled palette, circular CMYK halftone, desired material texture, and clean upper field.
- **Avoid:** new objects, extra text, collage/mockup, seams, halos, distortion, and any specifically rejected treatment.

For edits, start with: “Edit this exact poster. Preserve [approved elements] unchanged. Change only [requested elements].” If there are multiple images in the thread, explicitly identify the edit target and each reference image's role. Prefer a direct file reference to the exact edit target when supported; do not rely on the latest conversation image when a separate reference image is present.

## Finish

Return the generated poster directly. Keep the final note concise and say what changed. Do not offer multiple options unless requested.
