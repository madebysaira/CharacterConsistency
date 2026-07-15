# Client Case Study: Multi-shot Product Explainer

**Client:** Skincare brand (similar to previous Tanishq style luxury feel but product focused)

**Brief:** 45 second explainer showing the same woman using the serum in morning routine, applying, and talking to camera. 5 shots. Must feel like one continuous person for brand trust.

**What I tried first (failed):**

- Same seed + same reference photo across clips.
- Full prompt repeated.
- Result: Face changed between shot 1 and shot 3. Clothing hem moved. Client flagged it in review.

**What worked (this repo method):**

1. Built one locked style block from the brief (physical + clothing + lighting + palette).
2. Generated single reference image from the style block text in Flux.
3. For each shot: pasted full style block + specific action block + attached the reference.
4. Used Kling for motion heavy shots, Veo for the dialogue close up where text adherence mattered.
5. Negative prompt from the drift list in prompts/.

**Full prompts used (abbreviated for privacy):**

Shot 1 (establishing):
[full style block] + "walks into bright bathroom, reaches for serum bottle on counter, calm morning light" + reference image weight 0.8

Shot 3 (application):
[full style block identical] + "applies two drops of serum to cheek, gentle circular motion, soft smile" + same reference

And so on for all 5.

**Results:**

- Face consistency: 90%+ match across frames (measured by eye and client approval).
- Clothing stayed exact.
- One minor hand position fix in post.
- Total generations: 7 instead of the previous 20+.

**What I would do differently next time:**

- Generate the reference at higher resolution from the start.
- Add a "micro expression" note in the style block for dialogue shots (subtle smile vs neutral).
- The n8n snippet in docs/ would have caught the review step earlier.

**Files in this folder for this job:**

- character-bible-priya.md (the locked text)
- all 5 full prompts saved as text
- frame grabs of before/after (text descriptions here)
- client feedback notes

This is the exact workflow I now run for any multi-shot commercial video.
