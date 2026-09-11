---
title: "Test 5: First Item in a New Module Container"
tags: [com-216, pipeline-test]
doc-kind: pipeline-test
module: Modules
submodule: Module1
order: 10
purpose: "Verifies that a module container absent from the original export is created on import, using the course's real weekly structure."
source-html: null
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: students
version: v1
version-date: 2026-09-04
status: draft
note: "Pipeline test item per BRIGHTSPACE-PIPELINE-SETUP.md §7. Sandbox verification only — not course content; lives outside brightspace-md/ so it never ships in a real build."
---

## What to check

1.  A top-level **Modules** container now exists in Content — the
    original export had only Welcome and Toolkit.
2.  **Module1** exists inside it, and this topic is inside Module1.
3.  Welcome and Toolkit are unchanged: same topics, same order, nothing
    duplicated and nothing missing.

<div class="note">

This is the real structural question behind the whole test build. Weekly
content for the term lands in Modules, then ModuleN, and none of that
scaffolding exists in the export the cartridge is built from, so it has
to be created correctly by import rather than assumed.

</div>
