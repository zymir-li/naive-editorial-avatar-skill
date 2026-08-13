---
name: naive-editorial-avatar
description: Generate one identity-preserving square avatar from an uploaded real-person photo in a calibrated naive hand-drawn editorial style. Use for naive editorial avatars, 稚拙感极简手绘头像, 真人照片转手绘头像, or this compact white-background portrait look with soft imperfect black lines, flat colors, economical features, and recognizable personal traits.
---

# Naive Editorial Avatar

Turn a real person into the same *drawing family* as the synthetic calibration avatars while keeping the person specific. The photo decides **who** is drawn. The synthetic style anchor decides **how** that person is drawn.

## Load the calibration resources

Before generating:

1. Read [references/prompt-blueprint.md](references/prompt-blueprint.md).
2. Inspect `assets/synthetic-style-anchor.png`. This fictional AI-generated character is the primary finished-look and layout authority.
3. Inspect `assets/synthetic-style-range-anchor.png`. This second fictional AI-generated character proves that age, gender presentation, hairstyle, skin tone, and clothing may change while the drawing family stays coherent. It is a range check, not an anatomy template, and is not passed during normal generation.

Never use a bundled character as another person's anatomy template.

## Protect private source material

Keep the reusable Skill privacy-safe. Its bundled images must be purpose-made synthetic characters that are not derived from the user's identity.

- Never copy an uploaded photograph, contact image, private screenshot, UI crop, or identity-derived avatar into this Skill, its examples, its recovery archive, or its distributable package.
- Never retain a user source image as a calibration asset, even after cropping, blurring, redrawing, or converting it into an avatar.
- Keep temporary identity sources scoped to the active generation task only.
- Before packaging, inspect the complete archive file list and image metadata for personal names, local paths, account identifiers, or unexpected images.

## Prepare the identity source

If the person is distant in a full-body or environmental photo, make a non-destructive head-and-upper-shoulder crop. Preserve the whole hair silhouette, face, eyewear, ears when visible, neck opening, and a little shoulder. Use the crop for generation and the original for verification.

Describe only 3–5 high-value identity anchors in ordinary visual language, for example:

- overall face silhouette;
- hairstyle silhouette and part;
- eyewear shape;
- eye expression or another distinctive facial feature;
- skin tone and dominant clothing color.

Treat a clearly visible, intentional small accessory as one identity anchor when it materially helps recognition. Prefer at most two: earrings, nose jewelry, facial piercings, a thin necklace, a small pendant, a hair clip, or a head accessory. Preserve only what the photo clearly proves; do not infer a hidden matching earring or complete an occluded necklace.

Do not turn the face into a list of measurements. Do not prescribe generic “attractive” proportions. Ignore scenery, bags, phones, logos, and text unless the user asks to keep them.

## Keep image roles minimal and strict

For the first generation, pass exactly two images in this role order:

1. `synthetic-style-anchor.png` — the visual canvas, complete drawing-language authority, and layout authority;
2. the cropped real person — exclusive identity and appearance authority;

Do not pass the range-check character during normal generation. More references are not automatically better.

The synthetic style anchor must not donate its face, hair, ears, skin tone, clothing, accessories, or identity-specific pose to the new person.

## Generate one finished avatar

Use the image-generation tool and the concise primary prompt in the blueprint. Generate exactly one image, never a comparison grid or unsolicited batch.

Preserve from the real person:

- recognizable face and jaw silhouette;
- hairstyle silhouette, part, and volume;
- eyewear and visible-eye character;
- expression, skin tone, and important distinguishing marks;
- dominant clothing color or simple neckline cue.

Translate into the approved drawing family:

- square head-and-shoulders portrait on pure white;
- calm natural pose, allowing slight asymmetry from the source rather than forced passport symmetry;
- soft near-black hand-drawn contours with mild wobble and raster softness;
- flat softly textured color shapes without lighting, gradients, or modeled volume;
- economical brows, eyes or eyewear, short nose mark, tiny mouth, and minimal ear marks;
- hair built as a cohesive silhouette with only a few directional interior marks;
- subtle irregular blush only when it integrates naturally into the skin fill;
- the same portrait footprint and white-space rhythm as the rendering anchor, or slightly smaller when the person's hair needs room; never enlarge the character beyond the anchor's footprint.

Keep the same **mark budget** as the rendering anchor for every ethnicity, age, gender, and hairstyle. More visually distinctive features must be expressed through silhouette, placement, curve, and flat color—not by adding nostril outlines, lip outlines, eyelids, lashes, wrinkles, highlights, shading, or extra contours. Identity specificity and drawing simplicity must coexist.

Abstract small accessories within that same mark budget:

- a stud earring becomes one tiny flat dot at the visible earlobe;
- a small hoop becomes one simple imperfect loop;
- a nose stud or facial piercing becomes one tiny flat dot at its proven location;
- a thin necklace becomes one quiet single line following the neckline;
- a visible pendant becomes one tiny flat geometric mark in its main color;
- a hair clip becomes one small flat shape aligned to the real hair placement.

Preserve accessory type, visible count, position, and dominant color. Remove chain links, gemstones, facets, engravings, shine, highlights, shadows, and realistic metal rendering. Never enlarge jewelry for legibility, invent symmetry, or let accessories compete with the face.

For high-volume hair such as coils, curls, afros, turbans, or large updos, scale the whole person down until the complete hair-and-shoulder silhouette fits comfortably inside the anchor's outer visual envelope. Build the hair as one dominant mass with a few loose direction marks. Never tile the mass with repeated scalloped rows, individual curls, braids, spikes, or decorative pattern bands unless a specific large braid or accessory is itself an identity anchor.

Do not force numeric canvas occupancy, face ratios, ear size, strand counts, or head turn. Derive those from the person and the overall balance of the approved rendering anchor.

## Protect recognizability

Style transfer must not become face replacement. Do not beautify, age-shift, feminize, masculinize, thin, widen, or “correct” the person. Preserve asymmetries that help recognition. Simplify a feature only after preserving its relationship to the rest of the face.

Clear glasses remain clear glasses. Opaque sunglasses remain opaque sunglasses. Hair remains the person's hairstyle, expressed as broad masses rather than spikes or scribbles.

When eyes are visible, derive their opening, spacing, and gaze from the real person. For a neutral or gently smiling source, the illustrated gaze must read calm, attentive, and approachable: use a softly arched upper-lid mark with a small matte dark pupil naturally centered beneath it. Do not lower a flat lid onto the pupil or shift the pupils downward, because that changes a neutral expression into contempt, boredom, or suspicion. Preserve genuinely sleepy, skeptical, or asymmetric eyes only when that expression is actually present in the source. Avoid glossy anime construction, dot-only eyes, and fused eyelids.

For the nose and mouth, preserve identity through their relative width, placement, and curve while staying within the anchor's economy: one short nose mark and one restrained mouth mark. Do not add separate nostril loops, fully outlined lips, a lower-lip contour, or cosmetic lashes merely because the real features are broad, full, mature, or culturally distinctive.

## Apply two hard acceptance gates

Reject the image if either gate fails:

1. **Same drawing family** — it should sit naturally beside `synthetic-style-anchor.png`: soft imperfect ink, simple flat fills, cohesive hair, economical face, quiet white background. Reject vector polish, anime, crayon, charcoal, spiky hair fields, gradients, long modeled necks, or detailed scenery.
2. **Same person** — the face silhouette, hair, eyewear, expression, skin tone, and distinguishing anchors should still read as the uploaded person. Reject genericization or leakage from either synthetic bundled character. For a neutral source, reject eyes that introduce contempt, boredom, smugness, sleepiness, or suspicion that the real person does not show.

Also check that the avatar is neither crowded nor tiny and that blush, if present, is soft and embedded rather than two pasted circles.

When accessories matter, check that the few proven items remain recognizable at avatar size without increasing the overall detail density.

## Revise without compounding failure

The default delivery is one finished image. Revise only after explicit user feedback or an obvious hard failure.

- If the overall style or identity is wrong, restart from the real-person crop plus the synthetic style anchor with a cleaner prompt. Do not edit the failed image.
- If an otherwise accepted image has one local defect, edit that accepted image and change only the named defect.
- Never accumulate every previous correction into the next prompt.
- An accepted output is authoritative only for that same person. Across people, reuse the drawing grammar, never that person's geometry.

## Deliver

Save the result and prompt. Report the image path, the identity anchors used, the reference-role mapping, and any meaningful remaining deviation.
