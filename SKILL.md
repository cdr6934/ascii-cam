---
name: ascii-cam
description: Take a photo with the camera and turn it into colorful ASCII art.
---

# ASCII Cam

Opens the device camera in an interactive view. The user snaps a photo, and the skill renders the
whole image as colorful ASCII art, with each character tinted by its source pixel.

## Examples

- "Make ASCII art with my camera"
- "Turn a photo into ascii art"
- "ascii cam"
- "Take a picture and asciify it"

## Instructions

Call the `run_js` tool with the following exact parameters:

- script name: `index.html`
- data: An empty JSON string `{}` (this skill needs no input).

After the tool returns, briefly tell the user to tap **Capture** in the view to take the photo.
