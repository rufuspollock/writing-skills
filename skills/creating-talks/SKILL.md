---
name: creating-talks
description: Use when preparing a talk, presentation, lecture, keynote, conference session, or recorded video script — from first notes through script and slide brief to the slide build handoff.
---

# Creating Talks

## Overview

A talk is built as a chain of markdown files in one directory, each derived from
the previous. Stop or loop at any stage; later stages are cheap to regenerate
when an earlier one changes. Everything before the slide build is plain text —
no design assets, logos, or themes needed until stage 7.

## The artifact chain

| # | File | What it is |
|---|------|------------|
| 1 | `README.md` | Internal. Purpose, audience, "What We're Producing" table, design debates + conclusions, parking lot. First place notes land. Never published. |
| 2 | `notes.md` *(optional)* | Rough ideas, sketches, dictation dumps. Unpublished. Fold into README if small. |
| 3 | `<seg>-script.md` | Skeleton bullet arc → full near-spoken script. Often dictated into `ref/raw-<topic>-<date>.md` first, then edited down. State target length as a top comment. |
| 4 | `<seg>-slides-brief.md` | Per-slide: title, body text, animation / transition / behaviour, image prompt. Plus global design notes. |
| 5 | artwork pass → `assets/` | Separate pass: find real usable images, record source URLs + licence, download locally if the build must run offline. Update the brief with the choices. |
| 6 | `<seg>-visual-direction.md` *(optional)* | Theme / visual direction notes before build. |
| 7 | `<seg>-slides.html` | Build. Handoff to the `frontend-slides` skill. |

`<seg>` = segment prefix when a session has several deliverables
(`pre-session-`, `session-climate-`). Drop it for a single-deliverable talk.

## Stage detail

**1. README** — the thinking space; allowed to be long and messy. "What We're
Producing" is a table: item | format | purpose. "Key Design Debates and
Conclusions": per open question, list the options considered, the conclusion,
and the reason.

**3. Script** — first a bulleted skeleton (the arc, the beats, the order) to
pressure-test; then expand to prose detailed enough to deliver from even when
delivery is ad hoc. If dictating, outflow into `ref/raw-<topic>-<date>.md`
first and edit that down — keep the raw file, don't overwrite it.

**4. Slides brief** — derived from the script. Per slide: title, body text
(verbatim), animation / behaviour ("reveal one row per beat", "diagram builds
across 4 beats"), and — where an image belongs — an explicit prompt for *what
kind* ("photo here, probably a 19th-c. engraving of a factory floor"). Do not
hunt for the actual image yet. Global design notes at the top: palette hint,
one or two colours, text size, the dominant animation mechanic.

**5. Artwork pass** — a dedicated second pass. Searching for art while writing
the brief is inefficient, and the build goes faster with images already chosen.
Per image slot: find a real, decent-quality image; prefer human-made art over
AI (exception: a strong pastiche of a known style); prefer public-domain /
open-licensed / permissively-licensed sources. Record the source URL and licence
beside the slide. If the build must run offline, download into `assets/` and
note in `assets/README.md` which file is which and where it came from.

**6. Visual direction** *(optional)* — `frontend-slides` carries its own themes
and will mostly pick its own, but a few sentences on mood / reference / era
beforehand help. Skip if you have no opinion.

**7. Build** — invoke the `frontend-slides` skill with the brief + chosen
assets. Optional extra inputs, this stage only: common logos, a shared
brand / design-style brief.

## Sources for open artwork

Wikimedia Commons, The Public Domain Review, The Met Open Access, NYPL Digital
Collections, Rijksmuseum, Smithsonian Open Access, British Library / Internet
Archive on Flickr, Flickr Commons, Old Book Illustrations. Prefer these over
stock sites and over AI generation.

## Example

Worked example: `2r-course/s2-metacrisis/` in the `life-itself` repo —
`README.md`, `pre-session-video-script.md`, `pre-session-slides-brief.md`,
`pre-session-slides.html`, `assets/`.

## Common mistakes

- Hunting for images while writing the brief → do the artwork pass separately.
- Overwriting the raw dictation file → keep it in `ref/`.
- Publishing the README → it is internal; it holds debates and half-formed notes.
- Thinking about themes or logos before the build → nothing before stage 6 needs them.
- Writing full prose before the skeleton → pressure-test the arc first.
