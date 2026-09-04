---
title: "Brightspace Content Pipeline — COM 216 Setup & Workflow"
tags: [directive, pipeline, brightspace, cowork-onboarding]
doc-kind: directive
audience: instructor-and-claude
version: v1
status: active
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
instructor: Steve
---

# Brightspace Content Pipeline — COM 216 Setup & Workflow

This is the course-specific copy of the portable Brightspace pipeline
directive, filled in for COM 216. See the original portable version at
`brightspace-cart-exports-for-claude/BRIGHTSPACE-PIPELINE-SETUP.md` for the
generic template used to set this up.

Placeholders for this course:

- `COURSE_CODE` — COM 216
- `COURSE_TITLE` — Digital Media, Information, and Society
- `TERM` — Fall 2026
- `INSTRUCTOR` — Steve

## 1. First-run directory setup

Scaffold lives at `216-111/brightspace-pipeline/` — a sibling of `design/`,
kept separate from the course's other pre-existing design content
(architecture doc, source reservoir, chat-riffs, bibs, etc., which stay
under `design/`, untouched):

```
216-111/
├── design/                            (course architecture, chat-riffs, bibs, ... — unrelated to this pipeline)
└── brightspace-pipeline/
    ├── CONTENT-PIPELINE.md            (this file)
    ├── BRIGHTSPACE-PIPELINE-SETUP.md  ← portable template, for reuse on other courses
    ├── brightspace-md/                ← source of truth, one .md per topic
    ├── brightspace-html/              ← generated output
    ├── brightspace-cartridge-base/    ← non-content files from the real
    │                                     Brightspace export, seeded below
    ├── from-brightspace/              ← raw D2L export zips (Brightspace's
    │                                     exports, coming in)
    ├── to-brightspace/                ← built cartridge zip(s), ready to
    │                                     import into Brightspace (going out)
    └── _archive/
        ├── brightspace-md/
        └── brightspace-html/
```

Naming is anchored to Brightspace, not to Claude or the instructor, since
both people and tools sit in the middle of this pipeline and "export"/
"import" are ambiguous relative to either — `from-brightspace/` and
`to-brightspace/` are unambiguous regardless of who's asking.

Module structure: **weekly** (Module1, Module2, ... map to weeks of the
term), per instructor confirmation.

`brightspace-cartridge-base/` was seeded from
`brightspace-cart-exports-for-claude/D2LExport_2939842_2026FA-UTI-COM216-1594_20269346.zip`
(the export current as of 2026-09-03). Only non-content files were copied in:
`imsmanifest.xml`, `orgunitconfig/`, `courseimage_d2l.xml`,
`discussion_d2l_1.xml`, `discussion_d2l_2.xml`, `dropbox_d2l.xml`,
`quiz_d2l_5719521.xml`, `questiondb.xml`, `basic_lti_link_4091613.xml`,
`basic_lti_link_4311596.xml`, `news_d2l.xml`, `syllabus_d2l.xml`.

**Note:** this export is not an empty shell — it already contains populated
content items (Welcome-*.html, Toolkit-*.html, images) that look like they
came from a prior run of this same pipeline. Those content files were
deliberately **not** copied into `brightspace-cartridge-base/` — per §5,
`brightspace-md/` should be the source of truth going forward, not the
exported HTML. Flagged for a decision rather than assumed (see chat).

## 2. Required YAML frontmatter

Every `.md` file under `brightspace-md/` opens with:

```yaml
---
title: "Human-readable title"        # required
tags: [com-216, ...]                 # required
doc-kind: reading | prompt | instructions | assignment-brief | rubric | reflection | policy | toolkit-guide | toolkit-install | welcome | course-details | goals-matrix | ...
                                       # required — grows per course
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: students
module: Welcome | Toolkit | Modules   # required
submodule: Module1 | Module2 | ... | null   # required when module: Modules
week: "Week 3"                         # optional
order: 10                              # required when submodule is set
purpose: "One sentence: what this document is, for a model or student orienting itself."
source-html: null                      # set only if reverse-derived from HTML
version: v1
version-date: YYYY-MM-DD
status: draft | published
---
```

## 3–9. Workflow, staging, assembly, reconciliation, verification, housekeeping

Unchanged from the portable directive — see
`brightspace-cart-exports-for-claude/BRIGHTSPACE-PIPELINE-SETUP.md` §3–9 for
the full text (drop-in workflow and frontmatter validation; stage ~5 changes
before asking to rebuild; `imsmanifest.xml` assembly rules; reconciling live
edits back to source; ~5 test items after a build; archive-don't-delete).
