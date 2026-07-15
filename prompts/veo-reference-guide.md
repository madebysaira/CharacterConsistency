# Veo Reference Guide for Consistency

Veo responds better to detailed text than most models, but still drifts on faces without the right structure.

## Core prompt structure for Veo

"Commercial product video, [character full description from style block], [exact action], clean studio or location lighting,  cinematic composition, sharp focus, natural motion, 24fps"

Include the full physical + clothing + lighting from the locked style block every time.

## Reference image use

Attach the reference image generated from the style block. Set reference strength high (around 0.8). Veo respects the image more when the text also repeats the key traits.

## Negative prompt

"face morph, different face, clothing change, hair length change, inconsistent skin tone, blurry, low quality, cartoon, deformed"

## When Veo wins for consistency

- When the brief has specific dialogue or text on screen that must match exactly.
- When budget allows and you need semantic understanding over wild motion.

## Cost reality

Veo generations cost more. I use it for hero shots where the face must read as the same person from the first frame to the last. For B-roll I fall back to Kling with the same style block.

## Tuning tip

If the face still shifts, add "exact same woman as reference image, identical facial features across all shots" at the end of the style block. It helps the model anchor.
