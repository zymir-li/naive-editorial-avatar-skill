# Prompt blueprint

Keep the first-generation prompt short. The image references already carry most of the visual information; prose should clarify their roles and protect identity, not micromanage geometry.

## Primary generation prompt

```text
Create exactly one square head-and-shoulders avatar.

REFERENCE ROLES
- Image 1 is a fictional AI-generated style anchor and is the visual canvas. It controls only the illustration language, mark economy, texture, character footprint, white-space rhythm, and overall presentation. None of its colors are authoritative.
- Image 2 is the real person and the exclusive authority for identity and every appearance color. Replace the person shown in Image 1 with this person.

Using Image 1 as the visual canvas, replace its character with the person from Image 2 so they look like an original character from the exact same illustrated series.

Keep the person from Image 2 recognizable. Preserve the real person's face and jaw silhouette, hairstyle silhouette and part, eyewear, eye expression, skin tone, distinguishing features, and dominant clothing color. Do not beautify, genericize, age-shift, or replace their face.

COLOR OWNERSHIP IS STRICT: derive skin tone and undertone, hair color, eye color, clothing color, eyewear color, and accessory color exclusively from Image 2. Image 1 contributes no palette. Match the visible source skin after only minimal flat-illustration simplification. Do not warm, tan, darken, lighten, desaturate, or shift the person toward Image 1's orange-brown skin, black hair, coral shirt, turquoise jewelry, or any other anchor color.

Most important identity anchors from Image 2:
- [ANCHOR_1]
- [ANCHOR_2]
- [ANCHOR_3]
- [OPTIONAL_ANCHOR_4]
- [OPTIONAL_ANCHOR_5]

If a clearly visible small accessory is an identity anchor, preserve only its proven type, visible count, position, and dominant color. Abstract a stud as one tiny flat dot, a hoop as one simple loop, a nose or facial piercing as one tiny flat dot at the real location, a thin necklace as one quiet line, a pendant as one tiny flat geometric mark, and a hair clip as one small flat shape. Do not invent hidden matching jewelry or enlarge it.

Preserve Image 1's complete drawing language: soft slightly imperfect near-black hand-drawn outlines, simple flat softly textured color shapes, economical facial marks, cohesive block-massed hair with only a few directional strokes, restrained natural expression, subtle irregular blush only if it belongs naturally, pure white background, and compact shoulders. Keep the complete character at the same visual footprint as Image 1 or slightly smaller, never larger; preserve its comfortable top and side margins.

Use exactly the same low detail density and mark budget as Image 1 for every ethnicity, age, gender, and hairstyle. Express identity through silhouette, placement, curve, and flat color—not by adding more facial parts. Keep the nose to one short identity-aware mark and the mouth to one restrained identity-aware mark. No separate nostril loops, fully outlined lips, lower-lip contour, lashes, wrinkles, highlights, face shading, or neck shadow.

The same mark budget applies to clothing and accessories. Do not draw collar ribbing, fabric seams, jewelry chain links, gemstones, facets, engravings, sparkles, highlights, shadows, or metallic realism. Accessories must remain subordinate to the face.

If the person's hair or headwear has much greater volume than Image 1, scale the entire person down so the complete hair-and-shoulder silhouette fits within Image 1's outer visual envelope. Render high-volume hair as one dominant cohesive mass plus a few loose direction marks, never repeated scalloped rows, tiled curls, decorative bands, or a field of individual strands.

Preserve the real eye opening and emotional tone from Image 2. When the source expression is neutral or gently smiling, keep the illustrated gaze calm, attentive, and approachable: softly arched upper lids and small matte pupils naturally centered beneath them. Do not create flat lowered lids, downward-shifted pupils, or a contemptuous, bored, smug, sleepy, or suspicious gaze unless that expression is truly present in Image 2.

Use a natural portrait pose derived from Image 2. Slight asymmetry is welcome; do not force a front-facing ID-photo pose or a dramatic turn. Simplify incidental details and remove the photographed environment, bags, text, and logos.

Avoid retaining Image 1's face, hair, glasses, ears, skin tone, clothing, palette, or identity-specific proportions. Avoid generic corporate vector art, Notion style, anime or kawaii eyes, crayon or charcoal texture, fields of spiky hair, gradients, shadows, 3D modeling, scenery, text, frame, logo, and watermark.

The final image must satisfy both conditions at once: unmistakably the person from Image 2 and unmistakably the drawing family and layout from Image 1.
```

## Local edit prompt

Use only when the existing image is already accepted for identity and style and has one isolated defect.

```text
Edit this accepted avatar. Change only [ONE_LOCAL_DEFECT]: [CORRECTION].

Preserve exactly the existing face, pose, expression, hairstyle, eyewear, eyes, nose, mouth, ears, neck, shoulders, colors, scale, line character, white background, and every other accepted feature. Do not redraw or reinterpret the person. Output one image with no text or frame.
```

If identity or the overall drawing family is wrong, do not use the local edit prompt. Restart from the real-person crop and synthetic style anchor.

## Diagnostic reference routing

- Vector-clean or over-polished: inspect `synthetic-style-range-anchor.png` to recover the shared loose line and flat-color logic, but do not add it as an image input by default.
- Eye construction alone is wrong: restate the source person's actual eye opening and emotional tone in words. Do not add an entire character or private screenshot as an eye reference.
- Identity is being replaced by the synthetic anchor: strengthen Image 2 as exclusive identity authority and restate that Image 1 is the visual canvas only.
- Another person inherits the synthetic anchor's face: Image 1 leaked anatomy. Restart from the two original references, prohibit its identity-specific geometry, and keep numeric facial geometry out of the prompt.

## Failure diagnosis

| Symptom | Correction |
|---|---|
| Looks like a generic avatar | Restart from the person crop; name only the 3–5 most distinctive anchors and prohibit beautification |
| Looks unlike the person | Shorten the prompt and strengthen Image 2 as exclusive identity authority |
| Looks unlike the approved style | Strengthen Image 1 as complete drawing-language and layout authority; remove unrelated style references |
| Skin or clothing inherits Image 1's colors | Restart from the original two references; state that Image 1 contributes zero palette and Image 2 exclusively owns every appearance color |
| Hair is spiky or scribbled | Ask for the same real hairstyle as one cohesive mass with a few direction marks |
| Curly or coily hair becomes a repeated decorative pattern | Restart from source and express it as one dominant silhouette with only a few loose direction marks |
| Darker skin, age, or fuller features cause extra detail | Enforce the same mark budget as the synthetic style anchor; preserve identity via silhouette and placement, not extra nostril, lip, lash, wrinkle, or shadow lines |
| Large hair crowds the square | Scale the entire character down until hair and shoulders fit inside Image 1's outer envelope |
| Earrings or necklace disappear | Preserve only type, visible count, location, and main color as minimal flat marks |
| Jewelry becomes decorative or realistic | Remove links, facets, shine, shadow, and metal rendering; reduce to a dot, loop, line, or tiny geometric pendant |
| Model invents a matching hidden earring | Keep only the accessories that are actually visible or clearly established in the identity source |
| Neutral eyes look contemptuous, bored, or smug | Restart from the person source; preserve the real eye opening, use gently arched lids and naturally centered pupils, and prohibit invented emotional tone |
| Eyes are sleepy or cute | Request simple awake eyes with a relaxed upper lid and small matte pupil; no gloss |
| Blush is pasted on | Request lower-contrast irregular warmth integrated into the skin fill, or omit it |
| Avatar is crowded or tiny | Ask only to match Image 1's overall visual scale and white-space rhythm; do not specify percentages |
| A local edit changes the face | Reject it and return to the last accepted image; never use a failed edit as the next baseline |

## Calibration note

Both bundled calibration avatars are fictional AI-generated characters selected only to demonstrate a reusable drawing family. They contain no user photograph, private screenshot, identity-derived crop, or user-likeness conversion. Neither defines a reusable face shape, feature layout, hairstyle, clothing, pose, or numeric proportions for other people.
