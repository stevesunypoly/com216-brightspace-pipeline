---
title: "Pipeline Test — Cartridge Provenance & Import Check (Sep 7, 2026)"
subtitle: "A test artifact, generated September 7, 2026. Not course content — the module holding this page is safe to delete."
tags: [com-216, pipeline-test]
doc-kind: pipeline-test
module: Pipeline Test
order: 10
purpose: "Single-topic cartridge that verifies a one-item import into a populated course shell without colliding with existing content; doubles as a plain-language explanation of what a Brightspace cartridge is."
source-html: null
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: students
version: v1
version-date: 2026-09-07
status: draft
note: "Pipeline test item per BRIGHTSPACE-PIPELINE-SETUP.md §7, narrowed to one topic at the instructor's request. Target: Ready-for-AI (org unit 2014086), which is populated, so this ships in its own dated container and reuses no existing module or topic name. Title deliberately carries an em-dash and an ampersand so the special-character check rides along. Lives outside brightspace-md/ so it never ships in a real build. Fidelity diff clean after adding subtitle: to frontmatter and the table caption line — the only remaining deltas are the <ol> numerals 1-4, which CSS generates in HTML."
---

## Why this page exists

This page was not written in Brightspace. It was written as a Markdown
file on a graduate assistant's laptop, rendered to HTML by a template, wrapped in
a package called a *content cartridge*, and imported here. If you are
reading it inside Brightspace, every step of that chain worked.

It is a test artifact. Nothing on this page is course content, and the
whole container it sits in is safe to delete.

## What a content cartridge actually is

A cartridge is a zip file with two kinds of thing inside it: the content
itself, and a manifest that says where each piece belongs.

| Part | What it is | What it controls |
|---|---|---|
| `imsmanifest.xml` | An index of every resource and its position | Module structure, topic order, titles |
| `*.html` | One flat file per topic | What a student sees when they open a topic |
| `*_d2l.xml` | Discussions, dropboxes, quizzes | Course tools, when included — omitted here |

Parts of a Brightspace content cartridge and what each one controls

The manifest is the interesting half. Cartridge files are stored flat, with
no folders, so the nesting you see in the Content sidebar is not a
reflection of how the files are stored — it is entirely described by
nested `<item>` elements in that one XML file.

## What this particular import proves

1.  A single new topic can be added to an **already populated** course
    without disturbing what is there. This course had 41 topics across
    10 modules before the import.
2.  A new module container is created by the import rather than having to
    exist first.
3.  The title survives intact — em-dash, ampersand, parentheses and all —
    in the sidebar, on this page, and in the browser tab.
4.  The course styling in this rendered file is preserved: the orange rule
    above, Georgia headings, a readable measure, and a visible focus
    outline if you tab through the link below.

## What is deliberately not tested here

An earlier five-item test cartridge also covered an external-link topic
and a topic nested two levels deep. Those were left out of this build,
because the container names they needed collide with real modules in this
course. The external-link case is the one still genuinely unverified —
its manifest structure was inferred rather than copied from a real
Brightspace export.

## Cleaning up

Delete the containing module. That removes this topic with it and leaves
no other trace, since this cartridge added nothing else.

Reference: [SUNY Poly](https://sunypoly.edu/)
