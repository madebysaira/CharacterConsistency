# CharacterConsistency

Practical toolkit for locking characters across shots in commercial AI video.

The problem that kept breaking client work for me: the face or clothing would drift between clip 1 and clip 3 even when I used the same seed, the same reference image, and nearly identical prompts. It made multi-shot campaigns feel cheap. Clients noticed. I was burning credits and hours in post just to make one person look like one person.

This repo is the system I use now. It is not a magic button. It is a repeatable way to build a character bible that survives the quirks of Kling, Veo, Runway, and Luma. I tested it on real briefs for product explainers and luxury style videos.

## Quick decision tree

Need the same character across three or more shots?

Start with a locked style block that describes physical features, clothing, lighting, and palette in detail.

Generate one strong reference image from that style block text.

In the video prompt, use the reference image plus the full style block text.

Swap only the action and camera per clip.

Add model-specific negative prompts for drift.

See docs/decision-tree.md for the full flow.

## The technique that actually worked

Separate what stays fixed from what changes.

**Style Block (locked across the entire sequence)**
- Physical description down to small details like a mole or lip shape.
- Exact clothing: fabric, cut, accessories.
- Lighting and color palette.
- Hair length, texture, part.

**Action Block (changes per shot)**
- The specific motion or gesture.
- Camera move.
- Duration.

I generate the reference image once using the style block. Then every video prompt contains the identical style block text plus the reference image plus the action for that clip. The separation is what dropped my regeneration rate from around 60% to under 15% on multi-shot jobs.

Full templates are in the prompts/ folder.

## Model notes from real tests

Kling: Excellent motion. Needs higher image prompt strength (0.75-0.85) and the drift negatives. Great when the shot has strong action.

Veo: Better at following complex text descriptions. Still drifts on faces without the reference + repeated style block. Use when the character has dialogue or the prompt has precise details. More expensive, so I save it for hero shots.

Runway and Luma: Useful for moodier or dreamier pieces. The same locked style block helps, but expect more variation. Good for inserts where perfect identity lock matters less.

Hybrid approach: Create the reference in Flux or SD3, then feed it into the video model with the style block. This combination gave me the most reliable results across the last few client projects.

See docs/ for the comparison table and tuning notes.

## Full case study

Look at examples/client-case-study.md. It walks through a 5-shot product explainer for a skincare brand. Every prompt, the reference notes, what drifted before the system, and the final client-approved version. I also included the before/after frame descriptions in examples/before-after-drift.md.

This is the kind of work I actually ship, not demo reels.

## What is inside

- prompts/
  - kling-character-lock.md (full style + action template)
  - veo-reference-guide.md
  - negative-prompts-for-drift.md (the ones that moved the needle)
  - reference-image-weight-tuning.md

- examples/
  - character-bible-example.md (complete locked description for a campaign character)
  - client-case-study.md (real multi-shot job with prompts and results)
  - before-after-drift.md (side by side failure vs locked)

- docs/
  - decision-tree.md (start here)
  - n8n-snippets.md (small automation pieces for reference gen and review)
  - analysis-tips.md (how I check frames quickly and common fixes)

## How to use it

1. Pick or write a style block for your character. Be specific.
2. Generate the reference image from the style block text.
3. For each shot, paste the full style block + the action for that shot + attach the reference.
4. Keep the style block text identical. Change only the action block.
5. Use the negatives. Test clip 1 and clip 3 side by side before running the whole sequence.

## What this means for client work

Consistent characters mean the video can go into ads, explainers, or campaigns without the viewer thinking "who is that in the third shot". Less time fixing faces in After Effects. More time on the story and the sell.

I use this on every multi-shot commercial project now. It is the piece that makes the rest of the pipeline reliable.

If you are shipping paid AI video work and consistency is costing you, this should help. Star it if it saves you generations or review rounds. Open an issue with your own before and after if you have one that still breaks the lock.

The prompts and examples are pulled from actual client timelines. They are not theoretical.
