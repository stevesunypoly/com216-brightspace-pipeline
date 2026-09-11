---
title: "Test 3: Ampersand & Em-Dash — Special Characters"
tags: [com-216, pipeline-test]
doc-kind: pipeline-test
module: Pipeline Test
order: 30
purpose: "Verifies that a topic title containing an ampersand and an em-dash survives XML escaping and D2L import unmangled."
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

The topic title in the Brightspace content list should read exactly
"Test 3: Ampersand & Em-Dash — Special Characters".

1.  The ampersand shows as a single ampersand character, not as an
    escaped entity and not stripped to a space.
2.  The em-dash shows as a long dash, not as a question mark, mojibake,
    or a plain hyphen.
3.  The same two characters render correctly here in the page body:
    Ampersand & Em-Dash — like this.

<div class="note">

Mangling here points at either XML escaping in the manifest or a
character-encoding mismatch on import, and the two look different: an
escaping bug shows a literal entity as visible text, an encoding bug
shows mojibake.

</div>
