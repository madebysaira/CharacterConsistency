# Reference Image Weight Tuning

The reference image is only half the battle. How you weight it per model matters.

## Kling

Image prompt strength: 0.75 to 0.85
Text prompt weight on style block: high
If face still drifts: raise image strength to 0.9 and add "exact match to reference" in text.

## Veo

Reference strength: 0.7-0.8 (Veo can overfit if too high)
Rely more on repeating the full style block text.

## General rule

Generate the reference from the style block text first. Never use a random photo of a similar person. The reference must be built from your locked description or the model has nothing solid to lock to.

## Quick test

Generate clip 1 and clip 3 with identical style block + same reference. Compare the face in a frame grabber. If the jaw or eye shape moved, adjust weight or add more specific negatives before wasting more credits.
