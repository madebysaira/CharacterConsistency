# Decision Tree for Character Consistency

Start here when you need the same person across multiple shots.

## Question 1: How many shots?

- 1-2 shots: You can often get away with a good reference image + repeated prompt. Still use the style block for safety.
- 3+ shots: Use the full locked system in this repo.

## Question 2: Which model?

**Kling** - Best motion. Use when action is important. Pair with high image weight (0.8+) and the negatives from prompts/negative-prompts-for-drift.md

**Veo** - Best text and semantic understanding. Use when the character must say specific lines or the prompt has complex details. Repeat the style block text heavily.

**Runway / Luma** - Good for mood and dreamy motion. Use the same style block but expect more variation. Good for B-roll where perfect lock is less critical.

**Hybrid** - Generate reference in Flux/SD, lock with Kling or Veo for hero shots, fill with cheaper model for inserts.

## Question 3: Is this commercial client work?

Yes → Invest the time in one strong reference image + verbatim style block. The client will notice drift.

No → You can relax the lock a bit, but the same structure still saves time.

## Quick start checklist

- [ ] Write one style block with physical, clothing, lighting, palette, hair.
- [ ] Generate reference image from that block.
- [ ] Test clip 1 and clip 3 with identical style text.
- [ ] Compare faces.
- [ ] Add negatives if drift appears.
- [ ] Only change the action block for new shots.

If the face is still drifting after weight and negative tuning, the style block is not specific enough. Add more details (mole position, exact lip shape, fabric texture).
