---
title: "Test 4: Nested Two Levels Deep"
tags: [com-216, pipeline-test]
doc-kind: pipeline-test
module: Pipeline Test
submodule: Test Submodule
order: 40
purpose: "Verifies that a topic nested inside a submodule inside a module keeps its full two-level position on import."
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

1.  This topic sits two container levels down from the top of Content:
    Pipeline Test, then Test Submodule, then this topic.
2.  It is *not* flattened up into Pipeline Test alongside Tests 1 to 3.
3.  The **Test Submodule** container itself appears, named exactly that,
    after Test 3 in the Pipeline Test module.

<div class="note">

Flattening here would mean the weekly Modules to Module1 to topic
structure the course actually plans to use will not survive import, so
this case matters more than its size suggests.

</div>
