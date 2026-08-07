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

## Model notes from real tests (August 2026 Update)

### Kling 3.0
Excellent motion with native 4K. Needs higher image prompt strength (**0.75-0.85**) and the drift negatives. Great when the shot has strong action. **New**: Multi-shot storyboarding works for character consistency across sequences.

### Veo 3.1
Better at following complex text descriptions. **Native audio sync** including lip-sync for dialogue scenes. Still drifts on faces without the reference + repeated style block. Use when the character has dialogue — the lip-sync is industry-leading. More expensive, so I save it for hero shots.

### Runway Gen-4.5
**#1 ranked for character consistency** (1,247 Elo on Artificial Analysis). Superior multi-shot character locking with native lip-sync. The go-to for character-driven commercial content. Premium pricing but worth it for high-stakes client work.

### LTX 2.3 with ID-LoRA
**Game changer for character consistency**. The IC-LoRA workflow includes three separate groups:
- **Canny IC-LoRA**: Edge preservation for structure
- **Depth IC-LoRA**: Spatial understanding  
- **Character ID-LoRA**: Identity locking across shots

Train a character LoRA on 10-20 reference images, then apply with the style block. This combination gave me **95%+ consistency** across the last 3 client projects.

### Wan 2.1
Open-source option with strong character adherence when using ComfyUI workflows. 14B parameter version available. Good for self-hosted projects requiring privacy or high-volume batch generation.

### Luma Dream Machine 1.6
Updated with 12 camera motion presets. Useful for moodier pieces. The same locked style block helps, but expect more variation than Runway or Veo. Good for inserts where perfect identity lock matters less.

### Hybrid approach (My Current Workflow):
1. **Generate reference**: Flux/SD3 for initial character images
2. **Train ID-LoRA**: If budget allows, train LTX 2.3 ID-LoRA on references (10-20 images)
3. **Lock with style block**: Full style description + reference image in every prompt
4. **Generate**: Kling 3.0 for motion-heavy shots, Runway Gen-4.5 for dialogue, Veo 3.1 for lip-sync scenes
5. **Review**: Side-by-side frame comparison before final render

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

---

## August 2026: What's New

**ID-LoRA for LTX 2.3**: The biggest breakthrough in character consistency this year. Train custom LoRAs on your character references and get 95%+ consistency across shots.

**Kling 3.0 Multi-Shot Storyboarding**: Native support for consistent characters across multiple shots in one generation pass.

**Runway Gen-4.5 Character Consistency**: #1 ranked on Artificial Analysis benchmark for character locking across sequences.

**Veo 3.1 Lip-Sync**: Characters can now speak with synchronized mouth movements — a game changer for dialogue-driven content.

**New in prompts/**:
- `ltx-id-lora-training.md` — Step-by-step LoRA training guide
- `runway-gen4-character-workflow.md` — Multi-shot consistency with Runway
- `veo31-lipsync-prompts.md` — Dialogue scene prompts with sync techniques
- `canny-depth-ic-lora-template.md` — Structured control prompts

*Last updated: August 2026*
