# Frame and caption audit, 2026-09-09

Seven blind reviewers audited the atlas. Six opened every screenshot in two
stages each, 245 frames in total, with no sight of each other's work. The
seventh read all 360 claim cells and reviewed the stage names.

The reviewers were told to report only. They made no changes.

## What the audit covers

| Reviewer | Stages | Frames |
|---|---|---|
| 1 | Onboarding, Ingestion | 44 |
| 2 | Orientation, Task selection | 53 |
| 3 | Generation, Feedback | 51 |
| 4 | Regeneration, Source traceability | 37 |
| 5 | Re-engagement, Accessibility | 27 |
| 6 | Personalisation, Authorship | 33 |
| 7 | The 12 stage names and 4 group labels | text only |

Full reports are in the session scratchpad, one file per reviewer.

## Priority 1: personal data on a public page

Four captures carried personal data that the caption said was already removed.

| Frame | What was exposed | State |
|---|---|---|
| copilot-study-learn, all 10 frames | Microsoft tenant GUID, a `client-request-id`, two presenters by name and face, a teacher name on 12 cards | Fixed. Cropped as the caption promised. |
| helperbird/authorship | A Google Docs document id, a signed-in profile chip, sitcom dialogue with sexual innuendo | Fixed. Redacted. |
| magicschool-iep, all frames | A bookmarks bar naming a doctoral program and a school district, a downloads strip of dated filenames | Open |
| jamworks, lernabl, knowt | Presenter names, a third-party bookmark, a live recording URL | Open |

## Priority 2: the picture contradicts the sentence beside it

The evidence class grades the claim, not the picture, so these are not class
errors. They are worse: a reader sees the atlas deny something its own
screenshot shows.

- `gemini-classroom/feedback` — graded "none found" for what happens after a
  student answers, beside a frame showing the answer marked and explained.
- `gemini-classroom/signal` — "Nothing derives from the individual learner",
  while its own caption calls the frame the clearest sign of adaptation.
- `century-tech/signal` — "No learning-styles claim was found", beside a
  tooltip reading "based on how you learn best".
- `helperbird/access` — "no conformance claim was located", beside Helperbird's
  own VPAT.
- `mindview/access` — "no auditor located", beside a DAC certification badge.
- `studyfetch/return` — "no resume observed", beside a "Jump back in" card with
  a progress bar.
- Six more in Regeneration and Source traceability, where a visible control
  undercuts a "none found" sentence.

## Priority 3: Onboarding is the wrong column

Only 4 of 20 Onboarding frames show account setup or control. The rest are
product home screens, vendor marketing art, or frames belonging to other
stages. The taxonomy reviewer found the cause independently: 21 of the 30
Onboarding cells are about licensing and admin control, not first-run
experience. The stage is really **Provisioning**, and the wrong name invited
the wrong pictures.

## Priority 4: invented caption text

Captions that name UI text which is not in the image.

- `studycog/select` — a "Step 3 of 5" counter and a Continue button, graded
  "seen in use". Neither exists.
- `studycog/return` — "Step 2 of 5". Not in the image.
- `studycog/access` — "opened with Shift+S". Not in the image.
- `mindview/select` — a bare headshot captioned with a persona page, a picker,
  a learner name and three named disabilities.
- `genio-notes/generate` — the caption names a question about H.G. Wells. The
  on-screen question is about the forgetting curve.
- `helperbird/generate` — the caption names a cream background, larger text and
  taller lines. The image shows a plain white page at standard size.
- `helperbird/orient` — "more than 30 toggles". Seven rows are visible.
- `lernabl/return` — "Rivers of the world". The dropdown is closed.
- `blackboard-ally/access` — three button labels that are not on screen.
- `studyfetch/entry` — a nine-item navigation that is in a different frame.

## Priority 5: Accessibility does not hold up

Accessibility is the least captured stage, 10 frames of 30, on a product funded
by the Disabled Students' Allowance. Of those 10:

- Four prove nothing about accessibility: studyfetch (chatbot personas),
  magicschool-iep (a teacher's Text Leveler), caption-ed (a transcription
  dictionary), mindview (an undated vendor badge).
- One is borderline: blackboard-ally, where the product is not identifiable in
  the crop.
- Two are clear: lernabl and aspire-student-portal.
- Three of the six DSA products have no Accessibility frame at all.
- `genio-notes/access` is the strongest accessibility claim in the atlas and
  has the least evidence: a third-party WCAG audit graded "seen in use", with
  no frame, sourced from a help article titled for a different brand.

## Priority 6: evidence classes that overstate

Roughly 20 cells are graded above what their source supports. Every error runs
the same way, towards more confidence.

- Four Onboarding cells graded "in vendor docs" while their own text says the
  source returned 403 or 404.
- Four Authorship cells graded "seen in use" on quotes from marketing pages.
- `notebooklm/trace` graded "seen in use" while its caption says the team could
  not confirm the behaviour.
- Both StudyCog frames are vendor tour artwork, graded "seen in use".
- Several Generation and Feedback cells graded "seen in use" on vendor renders.

## Priority 7: duplicate frames

Byte-identical files, undisclosed unless noted.

- `notebooklm/select` = `notebooklm/trace`
- `jenni-ai/select` = `jenni-ai/return`
- `jenni-ai/orient` = `jenni-ai/switch` (disclosed)
- `turnitin-clarity/entry` = `turnitin-clarity/signal`
- `packback/trace` = `packback/feedback` (disclosed)
- `knowt/ingest` = `knowt/generate` (disclosed)
- `studiosity/trace`, `studycog/feedback` reuse (disclosed)
- `magicschool-iep` signal and authorship are the same screen 10 seconds apart,
  undisclosed

## Priority 8: undeclared image edits

A paint-out in `jamworks/select`, a background blur in `studyfetch/select`, a
second black bar in `podsie/select`, an editorial yellow arrow in
`gemini-classroom/select`, and a painted-out header in
`turnitin-clarity/authorship` where the note claims a crop.

## Stage names

The taxonomy reviewer judged 8 of 12 display names wrong. The stage ids never
change. Two reviewers reached "Adaptation signal" for stage 11 independently.

| Now | Recommended | Reason |
|---|---|---|
| Onboarding | Provisioning | 21 of 30 cells are licensing and admin control |
| Ingestion | Import | Ingestion is data-engineering vocabulary |
| Orientation | Overview | "Orientation" collides with course induction |
| Task selection | Learner control | Four cells answer "the educator" |
| Generation | Activity formats | Names the mechanism, not the output |
| Feedback | Feedback | No change |
| Regeneration | Control and recovery | Regeneration is 1 of the 4 things filed here |
| Source traceability | Citation and grounding | Mixes three different questions |
| Re-engagement | Resume and review | Growth-marketing term for session continuity |
| Accessibility | Accessibility | No change |
| Personalisation | Adaptation signal | Only 4 of 18 frames show self-directed change |
| Authorship | Authorship | No change |

Group labels: **Getting set up** (entry, ingest), **Deciding what to do**
(orient, select), **The study loop** (generate, feedback, switch, return),
**Fit and integrity** (trace, access, signal, authorship).

Orientation and Task selection overlap most. Seven products describe the same
screen in both columns. StudyFetch describes it three times.

Authorship is nearly empty: 18 of 30 are "none found", and 12 of those are
boilerplate for products that are not writing tools. Those must read "not
applicable", not "none found".

## What was applied, 2026-09-09

Every finding above is either fixed or listed below as still open. Three
commits carry the work: `8caa69a`, `ef7dd2c` and `9f6fad5`.

**Fixed.**

| Area | Count | What changed |
|---|---|---|
| Personal data | 22 frames | Cropped the presenter tile, the bookmark bars, the tenant GUID, the teacher name and the recording URL out of Jamworks, Lernabl, Knowt, MagicSchool and Copilot frames. |
| Picture against sentence | 8 cells | Where the frame won, the sentence changed. |
| Evidence grades | 15 cells | Nine overstated their source. Five entry cells rested on a 403 or a 404. One accessibility claim rested on a single help article. |
| Invented caption text | 15 captions | Removed the named things that are not in the picture. |
| Frames that show another screen | 8 frames | Pulled from the record. The empty state is the honest one. |
| Duplicate frames | 10 pairs | Both sides now name the other. |
| Undeclared edits | 6 frames | The black bars, the blur, the yellow arrow and the composite are all declared. |
| Stage merge | 2 stages into 1 | Orientation and Task selection describe one screen. The id `orient` is an alias, thus every old link resolves. |
| Evidence classes | 4 into 5 | "Not applicable" replaces 14 boilerplate "none found" cells in Authorship. |
| The chip beside a picture | all cells | A `not-found` cell that holds a frame now reads "not on this screen". |

**Still open.**

- Accessibility holds 7 frames of 30 on a DSA-funded product. Capture is the
  only fix. Authorship, Source traceability and Re-engagement come next.
- The remaining stage renames wait on a decision. Task selection and
  Personalisation are settled and keep their names.
- The stage loupe misses the focus trap that the lightbox uses. Panning is
  mouse-only. The plate hairline sits at 1.48:1 in light and 1.29:1 in dark.
  `--ink-3` sits at 3.36:1.
- Century Tech holds frames with no caption.
- Jenni AI needs a frame that shows the web clipper. The old one was a
  publisher page with no product in it.
