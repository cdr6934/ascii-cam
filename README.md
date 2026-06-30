# ASCII Cam

Take a photo with the device camera and turn it into colorful ASCII art.

![type](https://img.shields.io/badge/JS-0a9396)
![type](https://img.shields.io/badge/Webview-ee9b00)
![type](https://img.shields.io/badge/Camera-656d4a)

A standalone [AI Edge Gallery](https://github.com/google-ai-edge/gallery/tree/main/skills) Agent
Skill for on-device Gemma models. This whole repository **is** the skill folder.

## Add to the Gallery app

Skills chip → **+** → **Load skill from URL** → paste:

```
https://cdr6934.github.io/ascii-cam
```

(Grant the in-app webview **camera permission** when prompted.)

## What it does

1. The model invokes the skill via `run_js`, opening an interactive view in chat.
2. The view shows a live camera preview with a **Capture** button.
3. On capture, the **entire frame** is sampled to a character grid and rendered as ASCII art where
   **each glyph is tinted by its source pixel color**. A **Retake** button restarts the camera.

The camera is opened with `getUserMedia()` **inside the webview** — no image passes through the
model, keeping it fast and private on-device.

## Usage

- "Make ASCII art with my camera"
- "Turn a photo into ascii art"
- "ascii cam"

## Layout

```
.
├── SKILL.md            # frontmatter + instructions the model reads
├── scripts/
│   └── index.html      # run_js entry point; returns the webview
├── assets/
│   └── webview.html    # camera capture + ASCII rendering (the interactive view)
└── .nojekyll           # makes GitHub Pages serve SKILL.md raw
```

## Notes

- The luminance→glyph ramp runs light→dense (`" .:-=+*#%@"`) so bright pixels render as visible
  glyphs and dark pixels fade into the black background.
- The live preview is mirrored (selfie-style); the captured frame is mirrored to match.
- Hosting must serve raw MIME types (GitHub Pages with `.nojekyll`), **not**
  `raw.githubusercontent.com`, which serves `text/plain` and won't execute the webview.

---

Authored with the [gemma-skills](https://github.com/cdr6934/gemma-skills) creator toolkit.
