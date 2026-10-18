# film-image-prompts

A Claude skill that writes, reviews, and fixes prompts for AI image and video models:

- **Midjourney** (stills)
- **Nano Banana** in the Gemini app (stills and exact edits)
- **FLUX.2** (stills, with LoRA and img2img)
- **Wan 2.2** and **LTX-2.5** (image-to-video)

## What it does

- Selects the visual style from your source (a poem, a scene, a character note). It has no default look. Photorealism and illustration are both supported.
- Fills one source brief, then writes it for the target model. Midjourney gets a compact prompt with `--no`. Nano Banana gets full sentences, a stated job for each attached image, and follow-up edit messages. FLUX.2 gets long, natural language with the avoids as positive statements.
- Applies a shot framework for film work: intent, action, frame, lens, camera, performance, light, continuity.
- Removes common problems: Stable Diffusion tokens, repeated keywords, contradictions, and "Negative Prompt" sections that Midjourney reads as positive.
- Gives a step-by-step fallback ladder when Midjourney blocks a prompt.

## Install

**Claude (web, desktop, mobile):** Download `film-image-prompts.zip`. In Claude, open Settings, find the Skills section, and upload the zip.

**Claude Code:** Copy the `film-image-prompts` folder into `~/.claude/skills/`. Start a new Claude Code session.

## Use

Ask Claude for a prompt and name the target. Example:

> Write a Midjourney prompt for this poem: ...

If you do not name the target, Claude asks.

## Author

[@adamlozo](https://github.com/adamlozo)
