# FIP-01 — film-image-prompts skill: add "Nano Banana by API"

**Repo:** `adamlozo/film-image-prompts` (public, MIT). **File:** `SKILL.md`.
**Why:** the Nano Banana section covers the Gemini app. Claude Code now calls Nano Banana through the Gemini API (Lost Ghost DEC-153, DEC-154). The skill needs the rules for scripted calls and for edits that must match a key of record.

## How to decide and when to ask

- **Ask only** for a real blocker.
- **Decide by rule, report the choice, and do not ask:** where the local clone is (Step 0.2); the line numbers of the three edits.

---

## Step 0 — Checks and save

1. Find the local clone of `adamlozo/film-image-prompts`. Look in this order: `C:\Claude\Projects\film-image-prompts`; then any folder under `C:\Claude\Projects\` that holds a `.git` with that remote. Report the path. If there is no clone, STOP and ask the director whether to clone it.
2. `cd` to the clone. The tree must be clean. `git fetch`, then the branch must equal its remote. If not, STOP and report.
3. Read `SKILL.md`. Check that it has a section `### Nano Banana (Gemini app, stills)` and a section `### FLUX.2 (stills)`, and that it has no section named `Nano Banana by API`. If a check fails, STOP and report.
4. Check that `docs/prompts/FIP-01-prompt.md` does not exist. Make the folder `docs/prompts/` if it is missing. Save this prompt there, word for word, with the Write tool.

## Step 1 — Edit 1: a row in the Step 1 target table

In the table under `## Step 1: Identify the target`, add this row directly after the `Nano Banana (Gemini app, stills)` row, word for word:

```
| Nano Banana (Gemini API, scripted) | Text + images in each API call | As Nano Banana, plus the image to edit in every call | Full natural sentences; the model ID is set in the call |
```

## Step 2 — Edit 2: the new section

Insert this section directly before the line `### FLUX.2 (stills)`, word for word, with one blank line before it and one after it:

```
### Nano Banana by API (scripted calls)

Use this section when a script (for example, Claude Code) calls Nano Banana through the Gemini API, not through the Gemini app.

Model:
- Select the model by its ID, from the API's own model list. The app names (Fast, Thinking, Pro) are not IDs.
- Use the Pro image model (an ID that contains `pro-image`) for final images, and a Flash image model for drafts. Prefer an ID that is not a preview.
- Record the model ID with each image.

Prompt:
- Write the prompt by the rules of the Nano Banana section: full sentences, no parameters, the avoids in positive words, one change for each edit, and a closing sentence that says what stays the same.
- Each API call is a new chat with no history. Send the image to edit in every call. For a chain of edits, send the last good image, not the first one.
- Give the aspect ratio in words. Also set it in the call when the API takes it.
- Name the plain parts of the object you change ("a plain door with only a dark knob and a keyhole plate"). The model adds fittings and details that the text does not name.

Edits that must match a key of record (a film plate or a set state):
- The model changes the whole frame, not only the named area. It can shift the light, the colour and the grain everywhere (a mean shift of 9 to 14 levels outside the edit in one test).
- Align the edit to the key before you use it. The model can change the size or the framing by a few pixels.
- Match the edit's light and colour to the key, measured on the area outside the edit. Without this step, a seam shows at the edge of the edit.
- Keep only the edited area: comp it over the key inside a mask, and keep the key's own pixels outside the mask. Check that nothing outside the mask changed.

Safety and cost:
- Read the API key from an environment variable. Never print it, log it, or write it to a file or a repository.
- Check the data terms of your billing tier before you send unreleased material.
- Set a cap on image calls for each run. Log each call: the model ID, the input file, the time and the result.
- On an API error, stop and record the error. Do not retry in a loop.
```

## Step 3 — Edit 3: a line in the Step 6 checklist

Under `## Step 6: Review before you deliver`, add this line directly after the line that starts with `- For Nano Banana:`, word for word:

```
- For Nano Banana by API: the model ID comes from the model list, each call sends its image, and an edit that must match a key is aligned, colour-matched and comped inside a mask.
```

## Step 4 — Check, commit, STOP

1. Show the diff of `SKILL.md`. It must hold only the three additions, with no other line changed. If it holds anything else, STOP and report.
2. Search the staged files for an API key pattern (`AIza` followed by 30 or more characters). If one is found, STOP and report, without the text.
3. Stage by name only: `SKILL.md` and `docs/prompts/FIP-01-prompt.md`.
4. Commit message in a file written with the Write tool (UTF-8, no BOM): `Add "Nano Banana by API" section`. `git commit -F <file>`, push, and check that the remote equals HEAD.
5. **STOP.** Report: the clone path, the commit, the three line numbers where the edits went, and the diff stat.

## Rules

- STOP on a real blocker or a tool failure. Use no workaround without the director's approval.
- Change only the three places named above. Do not reword, reformat or reorder any other line of `SKILL.md`.
- Files written only with the Write or Edit tool. No inline Python of any kind. No heredoc text, no sed edits.
- Never overwrite a file other than `SKILL.md`.
