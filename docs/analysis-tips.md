# Analysis Tips and Common Failure Modes

## How I check consistency fast

1. Generate the sequence.
2. Export 1-2 clean frames per clip (no motion blur).
3. Put them in a grid in Figma or Photoshop.
4. Flip between them. Look for:
   - Jaw line movement
   - Eye shape or spacing change
   - Nose or lip difference
   - Clothing seam or button position
   - Hair length or part shift
   - Skin tone or lighting inconsistency

If any of those jump, the lock failed.

## Common failure modes

**Reference image too generic**
Fix: The reference must be generated from your exact style block text. A stock photo of a similar woman will not lock.

**Style block text changed between clips**
Fix: Copy paste only. No "improving" the description mid sequence.

**Image weight too low**
Fix: Raise to 0.8+ on Kling. Test one pair of clips.

**Not enough negatives for the model**
Fix: Use the lists in prompts/. Add "face change, different person" with weight if the interface supports it.

**Lighting not locked**
Fix: Add specific lighting description in the style block ("soft diffused daylight from camera left, no strong shadows on face").

## When to give up and fix in post

Sometimes one shot just will not lock no matter what. In that case I generate the best I can and fix the face in After Effects or Runway inpaint. The locked system reduces how often this happens, but it does not eliminate it 100%.

Document the shots that still needed post. It helps you improve the style block for the next job.
