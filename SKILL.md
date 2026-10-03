---
name: film-image-prompts
description: Write, review, or fix prompts for Midjourney, FLUX.2, Wan 2.2, or LTX-2.5 stills and shots, including prompts that a model blocked.
---

# Film and image prompts

Use this skill to write a new prompt, to review a prompt, or to fix a prompt that a model blocked or rendered badly.

The method has two parts. First, fill one neutral source brief from the user's source. Then write the brief for the target model. The same brief can give a Midjourney prompt and a FLUX.2 prompt.

## Step 1: Identify the target

| Target | Input | The prompt must carry | Form |
|---|---|---|---|
| Midjourney (stills) | Text only | Medium, subject, look, parameters | Compact, medium first, `--no` for exclusions |
| FLUX.2 (stills) | Text, LoRA, optional img2img base | Subject, look, LoRA trigger, avoids in the positive text | Long, descriptive natural language |
| Wan 2.2 i2v | Start frame + text | Motion only | Short motion prompt |
| LTX-2.5 i2v | Start frame + text | Motion and performance only | Short motion prompt |
| Any text-to-video | Text only | Full visual information + motion | Full description + motion |

If the target is not clear, ask. Do not guess.

## Step 2: Select the style from the source

Do not use a default look. The style comes from the source that the user gives (a poem, a story beat, a character note, a reference, a mood).

- If the user names a style or a medium, use it.
- If the user does not name a style, select the medium that matches the tone, period, and subject of the source. Examples: a Victorian ghost poem can take a Victorian oil painting or a mezzotint; a fairy poem can take a storybook ink-and-watercolour illustration; a modern domestic poem can take American realist painting; a dramatic scene can take a photorealistic cinematic still.
- Photorealism is a valid style. Use it when the user asks for it or when the source needs it.
- State the selected style in one note after the prompt, so the user can change it.

Artist names:
- You can name a historical (deceased) artist as a style anchor ("in the style of Edward Hopper").
- Do not name a living artist. Describe the traits of the style (for example, "pop-surrealist big-eyed porcelain doll, soft unsettling sweetness").
- Do not name real people as subjects. Use "inspired by" an era or a role.

## Step 3: Fill the source brief

Fill these fields from the source. This is a checklist, not a style. Leave a field empty if the source and the shot do not need it.

1. INTENT: what the image must make the viewer notice.
2. MEDIUM AND STYLE: from Step 2.
3. SUBJECT AND ACTION: who is in the frame and what they visibly do.
4. KEY FEATURES: face, hair, body, age. Describe adult characters as clearly adult.
5. COSTUME, PROPS, ACCESSORIES.
6. SETTING: only the environment details that have an effect on the image.
7. LIGHT: source, direction, colour.
8. CAMERA: frame, angle, lens, aperture. For photorealism also give the film stock or the camera body.
9. RENDERING NOTES: where the detail is high, where the edges stay loose.
10. PALETTE: a short list of named colours.
11. MOOD: one mood. Remove words that pull in a different direction.
12. EXCLUSIONS: only items that protect the key idea or that the model tends to add.
13. ASPECT RATIO.

Rank the elements. In a busy scene the model drops some elements, so mark the important ones and put them first.

## Step 4: Apply the shot framework (film and video shots)

INTENT → SUBJECT + ACTION → FRAME → OPTICS → CAMERA → PERFORMANCE + PHYSICS → LIGHT + SPACE → CONTINUITY

A professional prompt answers these questions:
- What must the audience notice?
- Who is in the frame?
- What exactly do they do?
- Where is the camera?
- Which lens do we use?
- How does the actor perform?
- Where does the light come from?
- What physically reacts to the action?
- Where does the shot start and stop?

### 1. INTENT
Decide what the shot does before you write: reveal information, make tension, show scale, or capture a reaction. If the shot has no purpose, camera language does not help it.

### 2. SUBJECT + ACTION
Write visible behavior, not an emotion.
- Weak: "Man is scared."
- Strong: "He freezes at the doorway, eyes tracking toward the sound, shoulders tightening before he slowly steps backward."

### 3. FRAME
Define what the camera sees.
- Wide = geography and scale
- Medium = action and relationships
- Close-up = emotion and reaction
- Insert = important detail

Add angle, height, and composition only when they are important.

### 4. OPTICS
The lens changes the image. Give a lens only when you know why.
- 24mm = environment, perspective, speed
- 35mm = natural spatial energy
- 50mm = balanced human perspective
- 85mm = compression and intimacy
- Macro = tactile detail

### 5. CAMERA
Use one motivated camera behavior: static, push-in, pull-back, tracking, handheld, pan, tilt, crane, or orbit. Move the camera only when the story gets something from the move.

### 6. PERFORMANCE + PHYSICS
Many AI shots fail here. Direct these items:
- eyelines
- breathing
- hesitation
- posture
- weight shifts
- foot contact
- momentum
- clothing response
- object interaction
- balance and recovery

- Weak: "Runs fast."
- Strong: "Accelerates, loses traction for half a step, catches his balance and keeps moving."

### 7. LIGHT + SPACE
Describe motivated light with a source, a direction, and a colour.
- Weak: "Beautiful cinematic lighting."
- Strong: "Warm sodium light from camera-right, cool ambient rain fill, hard reflections across wet asphalt."

Describe only the environment details that have an effect on the shot.

### 8. CONTINUITY
Each shot is between two states. Define:
- start position
- screen direction
- costume
- props
- injuries
- scale
- geography
- end position

This is more important when you make many clips of the same scene.

### Text-to-video and image-to-video are different
- Text-to-video needs more visual information.
- Image-to-video already has the character, composition, light, and environment. Do not describe the reference image again.
- For image-to-video, prompt only: camera motion, subject motion, performance, environmental motion, timing, and continuity.

## Step 5: Write the brief for the target

### Rules for all targets

- Remove Stable Diffusion tokens. They have little effect: "masterpiece", "best quality", "8K", "highly detailed", "hyper-detailed", "bad anatomy", "extra limbs".
- Remove repeated content. A keyword list that repeats the body text adds nothing.
- Remove contradictions (for example, "matte-glossy", "digital illustration" with "3D-rendered finish", "crisp vector edges" with "soft airbrushed gradients"). Keep one term.
- Do not exclude things that the crop does not show (for example, "extra fingers" on a head-and-shoulders crop).
- Keep exclusions that protect the key idea (for example, "open eyes" for a closed-eyes portrait, "plain hat" when the hat is the subject, unwanted colours for a limited palette).

### Midjourney (stills)

Structure, in this order:
1. Medium and style first (for example, "Stylized editorial fashion illustration, hand-painted in watercolor and gouache" or "Cinematic film still, photorealistic").
2. Subject and pose.
3. Key features, costume, props.
4. Rendering notes (where the detail is high, where the edges stay loose).
5. Setting, light, camera, palette, mood.
6. Parameters: `--ar` `--v` `--style raw` (for photorealism) `--s` then `--no` last.

Rules:
- Midjourney gives the most weight to the first words. Put the medium first. Do not put the style at the end.
- Keep the prompt compact. A long prompt loses control of the later text.
- Do not write a "Negative Prompt" section. Midjourney reads those words as positive. Use `--no`.
- Do not use section labels ("Art Style", "Lighting"). They join the text near them.
- `--iw 1.5` holds identity but drags the composition. Use about 1.2 for a re-light.
- Use `--no eyeglasses` if glasses appear when you do not want them.

Moderation:
- Remove these trigger words: seductive, sensual, smoldering, sultry, exotic, provocative, and similar words. Use "commanding", "regal", "self-possessed", or "intense".
- Remove intimacy cues when they are not necessary: parted lips, a glance over the shoulder, "romantic" together with bare-shoulder costume.
- Describe adult characters as clearly adult. In anime or doll styles, do not use "Lolita", schoolgirl, or lingerie cues (garters, bustier). Use the fashion-subculture words that carry the look without them.
- For an illustrated face: make the image clearly an illustration in the first words ("stylized", "hand-painted", "illustration"), and do not add realism cues ("photorealistic", "pores", "skin glow", "studio light", close lip detail). Do not put "photograph" or "3d render" in `--no`. Words about realism can increase the moderator score.
- For a photorealistic face: keep the realism cues. Ground them in camera language (lens, aperture, film stock or camera body, `--style raw`). Keep the costume and pose neutral, and keep the makeup and lip detail short.

Fallback ladder when Midjourney blocks the prompt. Do one step at a time:
1. Remove trigger words.
2. Remove pose cues that add intimacy (glance over the shoulder, parted lips).
3. Remove the makeup and lip detail.
4. Illustrated target: remove realism cues on the face. Photorealistic target: ask the user before you remove realism cues.
5. Add a stronger medium cue after the subject ("gouache sketch"). On a photorealistic target, ask the user first.

Scope: Midjourney is strong for one-off images and look exploration. For a character that must stay the same across many shots, a local model with a character LoRA (for example, FLUX.2) gives more control.

### FLUX.2 (stills)

- Write long, descriptive natural language. FLUX.2 handles long prompts well. Write the brief in full sentences, in the order of Step 3, with no section labels.
- If you use a LoRA, put its trigger word in the prompt. Give the LoRA weight in the workflow, not in the text.
- At cfg 1.0, FLUX.2 ignores a true negative prompt. Write the avoids as positive statements in the prompt (for example, "clean-shaven", not "no beard"; "eyes closed", not "no open eyes").
- For img2img, the denoise value controls how much changes:
  - About 0.35: a re-pass that keeps the image and changes a detail.
  - About 0.55: a strong push (for example, a ruin or aging pass) that keeps identity.
  - About 0.60: still keeps the pose. A new pose needs a new base image or a video engine.
- Describe the held pose and the frame. A still has no motion.

### Wan 2.2 and LTX-2.5 (image-to-video)

Engine choice: Wan holds, LTX acts.
- Use Wan for objects, cloth, and held near-stills.
- Use LTX for a face that speaks, a face that must hold in the dark, and body action.

Prompt rules:
- Do not describe the start frame again. Prompt the motion.
- Give one camera behavior (or "locked-off camera").
- Give the subject motion as physical steps with timing ("at 2 s she lifts the cloth").
- Give environmental motion on near-stills (candle flicker, dust, breath, cloth settle). A near-still with no motion reads as frozen.
- Give the end position.
- If your workflow has separate fields, put the held pose in the prompt field, the motion in the motion field, and the failure modes in the negative field.

Known engine behavior:
- Wan makes dark faces brighter and more beautiful. Use LTX for faces in the dark.
- Wan moves dark-red velvet toward magenta over a take. Fix it in the grade.
- Wan adds hands to cloth close-ups without a prompt. Put hands in the negative if you do not want them.
- LTX animates faces too much. On a held reaction, state the stillness: "face still, eyes fixed, only the breath moves".
- LTX loses fine embroidery when the cloth moves.
- Frame limits: Wan 81 frames. LTX 121 frames at 24 fps, frame count 8n+1.

## Step 6: Review before you deliver

Check each item:
- The style comes from the source or from the user, not from a default.
- The image or shot has an intent.
- The action is visible behavior, not an emotion.
- The frame, the lens, and the camera each have a reason.
- Performance and physics are directed (video).
- The light has a source, a direction, and a colour.
- The important elements come first.
- There are no repeats, no contradictions, no Stable Diffusion tokens, and no exclusions outside the crop.
- The start and end states agree with the shots before and after (video).
- For i2v: the prompt does not describe the start frame again.
- For Midjourney: medium first, compact, `--no` used, no trigger words, no section labels.
- For FLUX.2: long natural language, LoRA trigger present if a LoRA is used, the avoids are in the positive text.

## Output format

- Give the prompt in one code block, ready to paste.
- If the user asks for more than one target, give one code block for each target, each with a label.
- After the code block, give a maximum of three short notes: the selected style and why, what changed, and the next fallback step if the prompt fails.
- Recommend one prompt for each target. Do not give alternatives unless the user asks.
