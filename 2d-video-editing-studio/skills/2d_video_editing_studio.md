---
name: 2D Video Editing Studio
description: Master Autonomous Video Director & Production Engine for broadcast-quality 2D explainers, documentaries, and animations on mobile and desktop.
version: 3.1.0
---

# 2D Video Editing Studio — Master Video Director

Transform ideas, scripts, and concepts into broadcast-grade 2D video explainers across 5 core genres:
1. **Vox Documentary Explainer** (Tactile paper, halftone dot screens, giant stats, Polaroids with pushpins)
2. **Stickman / Modern Storytelling** (YouTuber comic stickman in streetwear, selective color environments)
3. **Sticker / Pop-Art Cutouts** (Die-cut white vinyl contours, 2-tier soft ambient shadows, satirical parodies)
4. **Suspense Noir / True Crime** (Chiaroscuro lighting, redaction bars, CCTV timestamps, evidence boards)
5. **Retro 8-Bit Arcade** (Pixel-art backdrops, RPG double-border dialogue boxes, HP bars)

## Production Commands
- **New Project**: `python studio.py new projects/<name>`
- **Voiceover**: `CARTESIA_API_KEY=... python studio.py voice --voice anuj`
- **Shot Planning**: `python studio.py plan`
- **Prompt Validation**: `python studio.py prompts`
- **Asset Generation**: `python studio.py generate` (Google Flow parallel rapid dispatch)
- **Cutout Keying**: `python studio.py key` (Die-cut contours + warm shadows)
- **Edit Validation & Sheet**: `python studio.py check && python studio.py sheet`
- **Audio Mix**: `python studio.py mix` (Voice + ducked music + SFX hits at -14 LUFS)
- **Render Master**: `python studio.py render` (1080p full render)

## Video Preview (Post-Render Playback)

After video generation is complete, the agent MUST present the rendered video(s) directly in the chat for instant in-place preview — both single video and multiple video outputs.

### Single Video Preview
When a single `master.mp4` is rendered, display it immediately:
```html
<video src="/path/to/project/master.mp4" controls width="100%"></video>
```

### Multiple Video / Multi-Format Preview
When multiple videos are rendered (e.g. preview + master, or multiple cuts/segments), display each with format fallbacks:
```html
<video controls poster="thumb.jpg">
  <source src="clip.webm" type="video/webm">
  <source src="clip.mp4" type="video/mp4">
</video>
```

### Playback Rules
- **Always present the video inline** after `python studio.py render` or `python studio.py preview` completes successfully.
- Use the **actual absolute path** to the rendered file (e.g. `/data/user/0/com.termux/files/home/videos/my_video/master.mp4`).
- For preview renders (540p draft), show with a note: `📺 Preview (540p draft)`.
- For final renders (1080p master), show with: `🎬 Final Master (1080p)`.
- If both `.webm` and `.mp4` exist, include both as `<source>` tags for maximum compatibility.
- For multi-segment or multi-cut projects, present each video in order with a labeled heading.
