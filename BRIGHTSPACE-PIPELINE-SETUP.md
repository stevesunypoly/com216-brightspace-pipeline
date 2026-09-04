---
title: "Brightspace Content Pipeline — Portable Setup & Workflow"
tags: [directive, pipeline, brightspace, cowork-onboarding]
doc-kind: directive
audience: instructor-and-claude
version: v1
status: active
---

# Brightspace Content Pipeline — Portable Setup & Workflow

Hand this document to a new Cowork task for a *different* course. It sets up
the same drop-in-markdown → Brightspace-cartridge pipeline used for IDT 555,
generalized so it isn't tied to that course's architecture, vocabulary, or
file names. Read it once at the start of a new course project, before
touching any content files.

Fill in these four placeholders for the new course before doing anything
else — ask the instructor if any are missing rather than guessing:

- `{{COURSE_CODE}}` — e.g. IDT 555
- `{{COURSE_TITLE}}` — full course title
- `{{TERM}}` — e.g. Fall 2026
- `{{INSTRUCTOR}}` — instructor name, for attribution in generated docs

## 1. First-run directory setup

On the first message in a new course project, create this scaffold inside
the connected working folder (adjust the root name to the course):

```
design/
├── CONTENT-PIPELINE.md          ← a copy of this document, filled in
├── {{course-slug}}-architecture.md   ← optional: the course's own design/
│                                        decision-log doc, if the instructor
│                                        wants one (see §8)
├── brightspace-md/               ← source of truth, one .md per topic
│   ├── Module1/                  ← content for "Module1" in the cartridge
│   ├── Module2/
│   ├── Module3/                  ← add or rename module folders as the
│   │                                course's actual module structure needs
│   └── <flat files>               ← Welcome / Toolkit topics (no submodule)
├── brightspace-html-v2/          ← generated output, one .html per .md,
│                                     same base filename, always flat even
│                                     when the .md lives in a subfolder
│                                     (Module2/foo.md → Module2-foo.html)
├── brightspace-cartridge-base/    ← the *original* exported cartridge's
│                                     non-content files (imsmanifest.xml,
│                                     orgunitconfig/, course image, quiz/
│                                     discussion/dropbox/grades XML) — copy
│                                     this in once, from a real Brightspace
│                                     export, before generating anything
└── _archive/                      ← retired files land here, in both
                                       brightspace-md/ and brightspace-html-v2/
                                       trees — never delete, always archive
```

Do not invent the module/submodule structure — ask the instructor what the
course's actual modules are (weekly? thematic? cohort-based?) and name the
subfolders to match, before creating any content.

If no real Brightspace export exists yet for this course, ask the instructor
to export one (even an empty shell course) so `brightspace-cartridge-base/`
has real, valid non-content XML to build against. Don't hand-author
`imsmanifest.xml` from scratch — start from a real export's structure and
extend it.

## 2. Required YAML frontmatter

Every `.md` file under `brightspace-md/` opens with this frontmatter. Fields
marked *required* block generation if missing — ask rather than guess:

```yaml
---
title: "Human-readable title"        # required — becomes <title> and the D2L topic name
tags: [{{course-slug}}, ...]         # required
doc-kind: reading | prompt | instructions | assignment-brief | rubric | reflection | policy | toolkit-guide | toolkit-install | welcome | course-details | goals-matrix | ...
                                       # required — this list grows per course; a new,
                                       # specific doc-kind is fine, don't force-fit
course: {{COURSE_CODE}}
course-title: {{COURSE_TITLE}}
term: {{TERM}}
audience: students
module: Welcome | Toolkit | Modules   # required — top-level container in the cartridge
submodule: Module1 | Module2 | ... | null   # required when module: Modules; omit otherwise
week: "Week 3"                         # optional — for weekly module content
order: 10                              # required when submodule is set — controls position
                                        # within it; lower sorts first; gaps of 10 are fine
purpose: "One sentence: what this document is, for a model or student orienting itself."
source-html: null                      # set only if this .md was reverse-derived from HTML
version: v1
version-date: YYYY-MM-DD
status: draft | published
---
```

## 3. The drop-in workflow

The instructor works two ways, and both should just work:

- **Drops a `.md` file** directly into `brightspace-md/` (or a subfolder).
  Nothing needs to be announced — the presence of a new or changed file is
  the trigger.
- **Pastes content from a Claude.ai chat** directly into the conversation —
  usually with a title and body but no proper frontmatter, sometimes with
  broken absolute links left over from the chat context. In this case:
  write it to `brightspace-md/` yourself, first, with the required
  frontmatter filled in (asking about any *required* field you can't infer),
  and fix any links that should be relative to this course's own files
  rather than pointing back at claude.ai.

For each new or changed `.md` file:

1. **Validate frontmatter.** If `title`, `doc-kind`, `module`, or (when
   applicable) `submodule`/`order` are missing, stop and ask rather than
   inventing values.
2. **Render to HTML** using one shared template for the whole course — same
   `:root` CSS variables, same page shell (skip-link, `<main id="main">`,
   `:focus-visible` outline, `@media print`), same table pattern
   (`<caption class="visually-hidden">` + `scope="col"`/`scope="row"` on
   every table). The first file you render sets the template; every file
   after reuses it verbatim. Don't invent a new visual style per document.
3. **Save output** to `brightspace-html-v2/<same-base-filename>.html`,
   mirroring the `.md` file's relative path into a flat name.
4. **Run the accessibility check**: every text/background color pair ≥
   4.5:1 (AA normal text), any decorative-only color ≥ 3:1 non-text
   contrast and never used for text or links on white, `lang="en"`, a
   `viewport` meta tag, exactly one `<h1>`, a skip-link, `:focus-visible`
   styles, `@media print`. Fix and re-check rather than shipping a failure.
5. **Run a content-fidelity diff** against the source `.md` (a word-set
   comparison is enough). Known false-positive patterns to recognize rather
   than chase as real bugs: the H1 living outside `<main>` (in `<header>`);
   markdown link syntax (`[text](url)`) leaving URL fragments as extra
   "md-not-html" words; hyphenated multi-word slugs collapsing into one
   token if your checker doesn't split on hyphens; and angle-bracket
   placeholder fields inside fenced template blocks (`<need>`, `<harm>`)
   getting misread as HTML tags and stripped from the markdown side — strip
   `<`/`>` as plain punctuation when the source is a fenced placeholder
   template, not as a real tag pattern.

## 4. Stage changes, then ask before regenerating

Don't rebuild the cartridge after every single edit. Instead:

- Keep a running mental (or written, in a scratch file) list of staged
  changes as they come in — new files, edits to existing files, renames,
  archived files.
- Once roughly **five** changes have accumulated, or the instructor
  explicitly asks for a build, stop and summarize the staged batch back to
  them in plain language before touching the cartridge: what changed, in
  which files, and anything you noticed that looks like it needs a decision
  rather than a silent fix.
- If two staged changes conflict with each other (e.g. two incompatible
  edits to the same field, or a vocabulary rename that collides with
  something else in flight), do not silently pick one. Flag the conflict
  and ask the instructor to resolve it — one question at a time if there
  are several independent conflicts, never batched into a single
  many-part question.
- Only regenerate the cartridge once the instructor confirms the batch.
  "Build", "regenerate", "make the cartridge" are the trigger phrases —
  generating rendered HTML is not itself permission to repackage.

## 5. Cartridge assembly (`imsmanifest.xml`)

- Copy `brightspace-cartridge-base/`'s non-content files into the build
  output untouched (manifest gets rewritten; XML for syllabus/course-image/
  org-unit-config/discussion usually doesn't, unless asked).
- Exclude announcements, assignments (D2L dropbox), quizzes, and grades XML
  from packaging unless the instructor explicitly asks for them included —
  those are typically live-managed directly in Brightspace, not through
  this pipeline, unless told otherwise.
- Maintain a `RENAME` map from each `brightspace-html-v2/` source filename to
  its destination filename inside the cartridge (Brightspace cartridges are
  flat; this is also where you rewrite internal `href`s to match).
- Add one `<resource type="webcontent" material_type="content" href="...">`
  per new HTML file, plus one `<item>` per topic nested under the right
  module container in `<organizations>`. Item identifiers must be unique
  against every existing `identifier` and `d2l_2p0:id` in that manifest —
  pick a fresh prefix per module and continue the numeric `d2l_2p0:id`
  sequence from whatever the highest existing value is.
- If the target module container doesn't exist yet as an `<item>`, create
  it; if it exists as an **empty** container, add children to it freely.
- Never edit or remove `<item>`/`<resource>` entries that already point at
  populated content in a *live* course export — that's the unsafe,
  duplication-prone case. When in doubt, ask before touching an existing
  populated item.
- Order children within a container by each file's `order` field, ascending
  (or by the instructor's explicit re-order instructions — see below).
- Validate the resulting `imsmanifest.xml` parses before rezipping, and run
  a broken-internal-link check across every rendered HTML file (watch for
  false positives on absolute `https://` links that happen to end in
  `.html` — those aren't internal, don't flag them as missing).

## 6. Reconciling a live export back to source

Sooner or later the instructor will edit content directly in Brightspace
after import (wording tweaks, reordered items, a swapped-in link), then ask
you to compare a fresh export against what you generated. When that
happens:

- Diff each changed file's rendered text against the export, and name the
  specific edits found (don't just say "it differs").
- Ask the instructor, per finding, whether to pull the live edit back into
  the `.md` source as a new version (most common), match a live reorder in
  the next manifest build, or drop something the export shows was replaced.
  Don't assume the answer — a live edit might be a deliberate improvement
  worth keeping, or a formatting artifact Brightspace's editor introduced
  that shouldn't be reproduced (e.g. a trailing non-breaking space from a
  rich-text editor — note it, don't chase reproducing whitespace noise).
- Bump the source `.md`'s version and log what changed and why in its
  frontmatter `note:` field, the same way any other edit is logged.

## 7. After a build: test-item verification

Once a new cartridge is generated and before treating it as ready for a
real import, stage roughly **five** small test items covering different
D2L material types (a plain content page, an item nested two levels deep in
a module, an external-link item, an item in a newly-added module container,
and one item whose title contains a special character like an ampersand or
em-dash) and ask the instructor to import the cartridge into a sandbox or
test course shell and confirm each one lands correctly — right module,
right order, right title, working internal links — before it goes anywhere
near a live, populated course.

## 8. Optional: a course-architecture decision log

If the course has its own evolving pedagogical design (axes, rubrics,
vocabulary, sequencing) separate from the Brightspace content itself,
keep it in one running `{{course-slug}}-architecture.md` file rather than
scattering design decisions across content files. Conventions worth
adopting if you start one:

- Number every substantive decision (`decision-locked-N`) and never edit or
  renumber a past one — new decisions get new numbers, even if they reverse
  an earlier one; the old entry stays as a historical record.
- Keep a version-history table at the bottom, newest row on top, and never
  edit an existing row when adding a new one.
- Bump the document's own `version` field (e.g. `v0.4-draft`) on any
  substantive change, with a `version-note` describing what changed and why.
- Before shipping an edit, diff the file against its prior version to
  confirm every historical `decision-locked-*` entry and version-history row
  is still byte-identical — catching an accidental edit to history is worth
  the extra diff.

## 9. Housekeeping conventions

- **Archive, don't delete.** Retiring a live file means moving it into a
  sibling `_archive/` folder in both the `brightspace-md/` and
  `brightspace-html-v2/` trees, never deleting it.
- **Path-mirroring.** `brightspace-md/Modules/Module2/Foo.md` becomes
  `brightspace-html-v2/Modules-Module2-Foo.html`; flat Welcome/Toolkit docs
  stay flat (no subfolder) in both trees.
- **Ask rather than invent.** Any required frontmatter field that's missing
  or ambiguous stops the pipeline for that file until the instructor answers
  — never fill it with a guess.
