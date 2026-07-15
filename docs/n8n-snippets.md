# n8n Snippets for Consistency Pipelines

These are small pieces I use to automate the boring parts of reference generation and review.

## Simple flow: Brief to locked reference

1. Webhook or form trigger with character description from client brief.
2. AI node: expand the description into full style block (physical + clothing + lighting).
3. Image gen node (Flux or SD via API): create the reference image from the style block.
4. Store the style block text and image URL in a Google Sheet or local file named by character.
5. Notify via Telegram: "Reference ready for [character]. Review image."

## Multi shot generator

- Trigger with number of shots + action list.
- For each shot: combine stored style block + this shot's action block.
- Call Kling or Veo API (or manual step if no API yet).
- Collect outputs.
- Notify for review with side by side links.

## Review loop

After generation batch:
- Node that posts frames to a review channel.
- Wait for approval reaction or reply "approved" or "regenerate shot 3".
- On approve: move files to final folder and trigger delivery workflow.

These are not full production workflows (see n8n-ai-creator-pipelines repo for that). These are the small focused pieces for the consistency problem.

Copy into your n8n and adapt the credential nodes for your image/video APIs.
