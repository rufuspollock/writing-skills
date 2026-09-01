# A Pattern for Creating Talks

This is how I build a talk — a lecture, a conference session, a recorded video
script. It is a pipeline of plain markdown files in one directory, each one
derived from the one before it. The value of writing it down is that the stages
are separable: you can stop early, loop back, or hand a middle stage to someone
else, and regenerating a later stage after an earlier change is cheap.

The other reason to name the stages: most of the work needs nothing but text.
No slide template, no brand kit, no image library, no theme. Those only enter at
the very end. Keeping them out until then stops the fiddly design questions from
crowding out the thinking.

## The chain

1. **README** — internal scratch and rationale
2. **Notes** — rough ideas (often just part of the README)
3. **Script** — skeleton arc, then full script (often via dictation)
4. **Slides brief** — the talk turned into a slide-by-slide spec
5. **Artwork pass** — actually go and find the images
6. **Visual direction** — optional, a note on look and feel
7. **Slide build** — handoff to the `frontend-slides` skill

## 1. README

The README is written first and stays internal. It never ships. It holds:

- A short statement of the talk's core claim and arc.
- **What We're Producing** — a table with one row per deliverable: the item, its
  format (e.g. "~6 min recorded video"), and its purpose.
- **Key Design Debates and Conclusions** — for every question I had to settle
  about the talk, the options I weighed, the conclusion I reached, and *why*.
  This is the part I come back to. Six months later the talk's shape only makes
  sense if the reasoning is written down.
- A **parking lot** of unresolved conceptual questions.

It is allowed to be long and messy. It is a thinking space, not a document.

## 2. Notes

Fragments, half-arguments, links, things someone said. If there is a lot of it,
it goes in `notes.md`; otherwise it is just a `## Notes` heading in the README.
Not for publication, ever. This is usually the first place raw material lands
before it has any shape.

## 3. Script

Two steps.

**Skeleton first.** A bulleted list at the top of `<talk>-script.md`: the arc,
the beats, the order they come in. This is what you pressure-test — is the
sequence right, does the argument land, is anything missing — before spending
effort on prose.

**Then the full script.** The skeleton expanded into near-spoken prose,
detailed enough to deliver from. I often don't read it on the day — delivery is
frequently ad hoc — but writing it out forces the flow to be real.

Increasingly the full script starts as dictation. I outflow into a raw file,
`ref/raw-<topic>-<date>.md`, talking it through unstructured, and then edit that
down into the script. Keep the raw file. Don't overwrite it — it often has
phrasings worth going back for.

State the target length as a comment at the top of the script, e.g.
`# Target: ~6 min (~900 words spoken)`.

## 4. Slides brief

The script becomes a slide-by-slide specification in `<talk>-slides-brief.md`.
This is a separate file, not annotations on the script. For each slide:

- **Title** and **body text**, written verbatim as it should appear.
- **Animation / behaviour** — what moves and when. "Reveal one row per beat."
  "The four-layer diagram builds across four beats; speaker narrates each layer
  as it appears." Include speaker cues where the timing of a reveal matters to
  the delivery.
- **Image prompt** — where a picture belongs, say *what kind*, not which one.
  "Photo here, probably a 19th-century engraving of a factory floor." "We want a
  human-made illustration of the medical analogy."

There is a global **Design Notes** block at the top: background, one or two
colours only, large text, and the dominant animation mechanic for the whole
deck (e.g. "sequential reveal throughout — never show content before it is
discussed").

What you do *not* do here is go and find the actual images. That is the next
stage, deliberately.

## 5. Artwork pass

A dedicated, separate pass over the brief whose only job is to source the
images. Two reasons it is its own stage:

- Searching for artwork while writing the brief breaks the flow of the brief.
- The slide build is much faster and cheaper when the images are already chosen
  and in hand.

For each image slot in the brief:

- Find a real, decent-quality image.
- **Prefer human-made art over AI.** The exception is when AI produces a strong,
  faithful pastiche of an existing style and nothing suitable exists otherwise.
- **Prefer open sources** — public domain, open-licensed, or otherwise
  permissively licensed. Record the **source URL and the licence** next to the
  slide in the brief.
- If the slide build needs to run locally or offline (often the case), download
  the file into `assets/` and record in `assets/README.md` which file is which
  and where it came from.

The output of this stage is: the brief updated with concrete image choices, plus
either explicit links or files in `assets/`.

### Where to look

Wikimedia Commons, The Public Domain Review, The Met Open Access, NYPL Digital
Collections, Rijksmuseum, Smithsonian Open Access, the British Library and
Internet Archive collections on Flickr, Flickr Commons, Old Book Illustrations,
Yale's open collections. These beat stock-photo sites and beat AI generation for
this kind of talk.

## 6. Visual direction (optional)

The `frontend-slides` skill carries its own themes and will mostly choose its
own. But sometimes it helps to have thought, beforehand, about mood, era,
reference points, a colour feeling. A few sentences in
`<talk>-visual-direction.md`. Skip it entirely if you have no opinion — the
build will still produce something coherent.

## 7. Slide build

Handoff to the `frontend-slides` skill, giving it the slides brief and the
chosen assets. This is the only stage where shared design inputs matter: common
logos, a shared brand or design-style brief if one exists. None of the earlier
stages need them.

## Directory layout

From a real session (`2r-course/s2-metacrisis/`):

```
s2-metacrisis/
  README.md                          # stage 1 — internal
  ref/
    raw-reflections-...-2026-04-17.md # stage 3 — dictation, source material
    paper-summary.md
  pre-session-video-script.md         # stage 3
  pre-session-slides-brief.md         # stage 4
  pre-session-slides.html             # stage 7
  session-climate-case-study-script.md
  session-climate-slides-brief.md
  session-climate-slides.html
  assets/
    README.md                        # which file is which, and its source
    4-layers.jpg
    correct-diagram.jpg
```

The `pre-session-` and `session-climate-` prefixes are the `<seg>` segment
markers — this session ships several deliverables, each gets its own script,
brief, and slide file. A single-deliverable talk drops the prefix.
