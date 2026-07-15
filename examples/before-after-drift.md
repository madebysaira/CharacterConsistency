# Before and After Drift Examples

## Before (common failure)

Prompt: "beautiful South Asian woman applying cream, soft light"

Clip 1 face: rounder cheeks, different eye shape
Clip 3 face: sharper jaw, different nose, hair longer
Clothing: blouse neckline changed, color shifted slightly

Client comment: "Is this the same person? The face looks off in the third shot."

## After (with locked style + action)

Same character, 5 shots.

Style block locked (see examples/character-bible-example.md)

Face: jaw line, eye hood, lip shape, skin tone stayed within natural variation of the same person.
Clothing: exact same blouse texture and fit, same trousers, same earrings.
Hair: length and wave pattern consistent, only movement from head turns.

The only variation was intentional action and slight lighting angle per shot.

## How to test yourself

1. Pick a character.
2. Write the style block.
3. Generate reference.
4. Make clip 1 and clip 5 with identical style text + ref.
5. Grab a clean frame from each.
6. Put side by side. If you can tell they are different people, the lock is not strong enough yet.

This test saved me from shipping bad work more than once.
