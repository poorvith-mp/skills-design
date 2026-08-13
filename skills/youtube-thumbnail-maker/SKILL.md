---
name: youtube-thumbnail-maker
description: >-
  Designs YouTube thumbnails with high-contrast focal points and text legible at small sizes. Use
  when making a thumbnail for a video. Not for in-video overlays - use youtube-popup-graphic.
---

# Thumbnail Maker
You generate a YouTube-style thumbnail from two software names using the \*\*Higgsfield MCP\*\*. All image generation happens through Higgsfield — never use local tools (no ffmpeg, ImageMagick, etc.).
## Required Inputs
- \*\*Two software names\*\* from \`\$ARGUMENTS\` or the user's message (e.g. "claude and stripe"). If only one or zero, ask once and stop.
- \*\*Headline text\*\* — if not provided in the message, ask once via AskUserQuestion. Never invent it: text is the most visible element of the thumbnail and a wrong guess wastes a generation. Accept explicit "you pick" / "no headline" as consent to skip.
- \*\*Style reference\*\* — defaults to \` (1).jpg\`. User can override by pasting a different image path.
## Workflow
### 1. Load Higgsfield MCP tools via ToolSearch
These are deferred MCP tools and \*\*must\*\* be loaded before calling:
```plain text
select:mcp__claude_ai_Higgsfield__media_upload,mcp__claude_ai_Higgsfield__media_confirm,mcp__claude_ai_Higgsfield__generate_image,mcp__claude_ai_Higgsfield__job_status,mcp__claude_ai_Higgsfield__job_display,mcp__claude_ai_Higgsfield__models_explore,mcp__claude_ai_Higgsfield__balance
```
Also load \`WebSearch\` and \`WebFetch\` via ToolSearch if not already available.
### 2. Find high-res icons for both apps
For each software name (run in parallel):
- \`WebSearch\` query: \`"\<software\> app icon png high resolution"\`. Prefer official sources: the brand's press/asset page, the App Store, Wikipedia, then \`cdn.simpleicons.org/\<slug\>\` as last resort.
- Pick the most square, highest-resolution PNG from results.
- Download: \`curl -L -o /tmp/\<slug\>.png "\<icon_url\>"\`. Verify with \`file /tmp/\<slug\>.png\` that it's a real PNG/JPEG and \`\[ -s /tmp/\<slug\>.png \]\` that it's non-empty. If the download is broken HTML or 0 bytes, try the next candidate URL.
### 3. Upload all three images to Higgsfield
Single batched \`media_upload\` call with \`files\[\]\`:
- Reference JPG (\`content_type: "image/jpeg"\`)
- Icon 1 (\`content_type\` matches downloaded file)
- Icon 2 (same)
For each returned \`upload_url\`, PUT the bytes:
```plain text
curl --upload-file <local_path> "<upload_url>"
```
(or run the curl command provided in the response verbatim).
Then \`media_confirm\` with \`media_ids: \[\<all 3 ids\>\]\`, \`type: "image"\`. Capture every returned \`media_id\` UUID \*\*and\*\* CloudFront URL.
### 4. Discover the model's media roles
Call \`models_explore\` once with \`action: "get"\`, \`model_id: "nano_banana_2"\` to see the exact \`medias\[\].roles\` strings the model accepts. Use those role names in step 5. If the response is ambiguous, fall back to \`"reference"\` — the server returns \`adjustments\` for auto-coercion.
### 5. Generate the thumbnail
Call \`generate_image\`:
```plain text
params:
  model: "nano_banana_2"          # Nano Banana Pro — best for text + multi-reference, 4K
  aspect_ratio: "16:9"
  count: 1
  prompt: |
    YouTube thumbnail, 16:9. Dark navy-to-black radial gradient background with a subtle
    green stock-market line chart running horizontally through the middle. Centered
    composition: two large 3D rounded-square app icons (iOS-style, glossy, soft drop
    shadow, depth) — first icon on the left, a bold chunky white "+" symbol in the
    middle, second icon on the right. Above the icons, large bold sans-serif white
    headline text: "<HEADLINE>". Match the lighting, depth, color palette, font weight,
    and composition of the reference image exactly. High contrast, premium, cinematic.
  medias:
    - { value: "<reference_media_id>", role: "<role-for-style-reference>" }
    - { value: "<icon1_media_id>",     role: "<role-for-subject-reference>" }
    - { value: "<icon2_media_id>",     role: "<role-for-subject-reference>" }
```
### 6. Poll for the result
Call \`job_status\` with the returned \`jobId\` and \`sync: true\` — the server polls internally up to \~25s, and Nano Banana Pro images typically finish in 10–20s. If still pending, wait \`poll_after_seconds\` then call again. Use \`ScheduleWakeup\` if it'll take longer than a few seconds.
### 7. Deliver
Return the resulting image URL(s) to the user as a clickable link. Optionally call \`job_display\` with the \`jobId\` to surface the generation in the Higgsfield UI widget.
## Critical Rules
1. Always use the \*\*Higgsfield MCP\*\* — never local image-gen tools.<br>2. Always load deferred MCP tools via ToolSearch before calling them.<br>3. Always upload via \`media_upload\` → curl PUT → \`media_confirm\`. Never pass local file paths to \`generate_image\`.<br>4. Never invent the headline text. Ask once, or accept explicit "you pick".<br>5. Validate downloaded icons are non-empty real image files before uploading.<br>6. Prefer official icon sources over random Google results.<br>7. Reference image path defaults to \` (1).jpg\` but is user-overridable.<br>8. Use \`aspect_ratio: "16:9"\` and \`model: "nano_banana_2"\` unless the user explicitly asks otherwise.
## Quick Template — Final Delivery
```plain text
Thumbnail ready — <App A> + <App B>, "<headline>":

<image_url>

(Higgsfield job: <jobId>)
```
Use \`\$ARGUMENTS\` as the two software names when present.


## Output format
- Lead with the result the user asked for.
- Use clear headings and bullet lists where helpful.
- Call out assumptions and open questions at the end.
- Stay specific to the YouTube Thumbnail Maker workflow; avoid generic filler.

## Verification & Quality Checklist

- [ ] Contrast and legibility verified at the smallest intended display size.
- [ ] Dimensions, bleed, and safe areas match the named output medium.
- [ ] Colour is never the sole carrier of meaning - icons or text accompany it.
- [ ] Asset licensing and font embedding rights confirmed for the intended use.

## Anti-Patterns & Constraints

- NEVER deliver a design without stating the medium and its constraints.
- NEVER rely on colour alone to convey state, status, or meaning.
- NEVER hand off exports without confirming the target platform's specs.
