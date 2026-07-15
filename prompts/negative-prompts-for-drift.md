# Negative Prompts for Drift

These are the negative prompt fragments that actually moved the needle on face and clothing consistency. Add them to every generation.

## Base negative (always)

face change, different person, another woman, clothing shift, outfit change, hair style change, hair length change, body proportion change, extra limbs, deformed face, inconsistent lighting, skin tone shift, eye color change

## Kling specific

"blurry face, morphing, identity shift, reference image ignored, low face similarity"

## Veo specific

"face morphing, character inconsistency, different identity, prompt drift"

## Runway / Luma

Add "inconsistent character, face swap, clothing warp" to the standard list.

## Weighting note

Put the strongest drift terms first. On Kling I sometimes double the weight on "face change, different person" as --2 or equivalent.

Test one clip with and without these. The difference is visible in side by side frames.
