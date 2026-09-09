# Instructions for agents working in this repository

This repository is the **public shop window** for competitor research. The research itself lives in the private repository `AiBiSolutions-uk/bubblewrap`. Nothing sensitive goes here.

Read this whole file before you change anything.

## What this repository is

One static site, served by GitHub Pages at https://aibisolutions-uk.github.io/journey-atlas/.

The main page is the **Journey Atlas**. It shows how each competitor learning app takes a student from uploaded material to practice. It shows one app at a time, one stage at a time.

```
index.html                     the atlas, one self-contained file
frames/<product-id>/<stage-id>.png   screenshots, one per stage
AGENTS.md                      this file
README.md                      short human introduction
```

There is no build step. There is no framework. There is no package manager. A commit to `main` publishes in about one minute.

## Rules that never change

1. **Static only.** Plain HTML, CSS and one inline script. No bundler, no npm install, no server.
2. **No `fetch()` and no ES module imports.** The page must also work when a person opens the file from disk. Put all data inline in the JavaScript.
3. **The page is public.** Do not commit a screenshot that shows a real student name, real coursework, an email address, a licence key or any personal data. Crop it or blur it, and say in the commit message that you did.
4. **Do not copy private research prose into this repository.** Put the finding in the atlas cell, in your own short words. Link to the vendor's own page as the source.
5. **Deep links are a contract.** The private tracker links into this page. Never rename a product id or a stage id that already ships. Add new ones instead.

## The deep-link scheme

- `#/<product-id>` — the whole journey of one product.
- `#/<product-id>/<stage-id>` — one stage of one product. The page scrolls to it and highlights it.
- `#/stage/<stage-id>` — the same stage for every product, side by side.

Both forms must work on first load, not only after a click. Test a deep link by pasting it into a fresh tab.

## The stages

The stage list is fixed and ordered. Do not reorder it and do not rename an id.

| Id | What the stage records |
| --- | --- |
| `entry` | How a student gets an account, and who configures it |
| `ingest` | What sources it accepts, and what happens when ingestion fails |
| `orient` | The screen immediately after upload finishes |
| `select` | Who chooses the next activity, the student or the system |
| `generate` | What activity formats it produces |
| `feedback` | What happens when the student answers |
| `switch` | How the student changes approach, regenerates or rejects a bad activity |
| `trace` | Whether an activity links back to the exact place in the source |
| `return` | What a second session looks like |
| `access` | Accessibility controls and any conformance claim, with auditor and date |
| `signal` | What drives adaptation: stated preference, observed performance, teacher assignment, diagnosis, or none |
| `authorship` | Who writes the submitted text. Essay products only |

`orient` is the most important stage. Almost no product does anything there. That gap is why this atlas exists.

## Evidence classes

Every cell carries exactly one class. Never write a claim without one.

| Class | Means |
| --- | --- |
| `observed` | Seen in the running product, a screenshot, a public API, or the shipped JavaScript |
| `documented` | Stated in the vendor's own help centre, policy or guide |
| `vendor-claim` | A marketing assertion with no independent support |
| `not-found` | Could not be established from public sources |

**`not-found` is never proof of absence.** It means "not found in public documentation". A client-rendered site defeats a documentation sweep. StudyCog proved this: its whole site returns a placeholder to any fetcher, and the first survey therefore missed five decision-relevant findings. Always write `not-found` text that says what specifically could not be established.

A missing stage is a finding. Render it. Do not hide it.

---

# How to add a new journey

Follow these steps in order.

## 1. Choose the product id

Use the kebab-case product name. Examples: `notebooklm`, `everway-writing-helper`, `century-tech`.

Make sure that the id is not already in use. Once an id ships, it is permanent.

## 2. Research the product

Use the cheapest source that shows the real running product. Do not create a paid account. Do not cross a paywall.

1. **Frames from public video.** Demo, review and vendor footage. This shows the authenticated product with no account. It is the highest-yield route.
2. **Vendor screenshot endpoints and tour APIs.** Some vendors serve full-size product images from a public URL.
3. **A free tier, captured live.** Ask a human before you create any account.
4. **Marketing screenshots.** Last resort. The vendor staged them. Mark them `vendor-claim`.

If a vendor site returns a short placeholder to a fetcher, the site is client-rendered. Read the shipped JavaScript bundle and any public JSON endpoint instead. Do not record `not-found` until you have done this.

## 3. Add the entry to `PRODUCTS`

Find the `PRODUCTS` array in `index.html`. Add one object. Use this shape:

```js
{
  id: 'example-app',
  name: 'Example App',
  url: 'https://example.com/',
  tracks: ['revision'],          // 'revision', 'essay', or 'boundary'
  dsa: false,                    // true if it is distributed through UK DSA
  summary: 'One or two sentences. What it is, and why it matters to us.',
  stages: {
    orient: {
      e: 'not-found',
      t: 'No first-run screen after upload is documented. The help centre covers uploading and generating, but never the screen between them.',
      src: [{ label: 'Help centre', url: 'https://example.com/help' }],
      quote: ''
    }
    // ... one key per stage id you can fill
  }
}
```

Fill every stage you can. Leave a stage out only when the stage does not apply to that product. If you looked and found nothing, that is `not-found`, not an omission.

Keep each `t` between one and three sentences. Use `quote` for a short verbatim vendor sentence when the exact wording matters.

## 4. Add the screenshots

Save each frame at `frames/<product-id>/<stage-id>.png`.

- Downscale to **1280 px wide**.
- Use PNG for user interfaces.
- Do not commit a file larger than 500 KB. Downscale it again instead.

The atlas shows a dashed placeholder for every frame that does not exist, and the placeholder names the exact path it wants. So you can always see what is missing.

Capture these five stages first: `orient`, `select`, `generate`, `feedback`, `return`.

## 5. Test

1. Open `index.html` in a browser.
2. Make sure that the new product appears in the left rail, under the right track.
3. Paste `#/<your-product-id>/orient` into a fresh tab. The page must open on that stage.
4. Open the matrix view. Make sure that the new row renders and that the page body does not scroll sideways.
5. Switch your operating system between light and dark. Both must be readable.

## 6. Commit

One product per commit. Write the product name in the commit message. Say where the evidence came from.

```
Add Example App to the atlas

Nine stages from the vendor help centre and two demo videos.
orient and return are not-found: no first-run screen is documented.
Frames captured for orient, select and generate.
```

Push to `main`. The site updates in about a minute.

## 7. Tell the private tracker

Post a comment on the relevant ticket in `AiBiSolutions-uk/bubblewrap` with the deep link to the new journey. Feature-triage decisions must link to a journey, not to a description.

---

# How to add a new stage

Do this only when a real journey step exists that no current stage records.

1. Add the id to the end of the stage list in `index.html`. Never insert it in the middle and never renumber.
2. Add a row to the stage table in this file.
3. Set the stage to `not-found` on every existing product until somebody researches it.

# How to add a second page

Put it at `<name>/index.html`. It is then live at `https://aibisolutions-uk.github.io/journey-atlas/<name>/`.

Follow the same rules: static only, no build step, no personal data.
