---
title: "Pipeline Test Build — Sandbox Verification Checklist"
tags: [com-216, pipeline-test, directive]
doc-kind: pipeline-test
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: instructor
purpose: "Checklist for the §7 sandbox import of COM216-pipeline-test-2026-09-04.zip, before any cartridge goes near the live course."
version: v1
version-date: 2026-09-04
status: active
---

# Sandbox Verification Checklist

**Cartridge:** `to-brightspace/COM216-pipeline-test-2026-09-04.zip`
**Import into:** a sandbox or test course shell — **not** the live COM 216 section.

Import, then walk Content top to bottom and check each line.

## The five test items

| # | Item | Where it should land | What to confirm |
|---|------|----------------------|-----------------|
| 1 | Test 1: Plain Content Page | Pipeline Test → first | Opens; course styling intact; title keeps its colon |
| 2 | Test 2: External Link (SUNY Poly Home) | Pipeline Test → second | Behaves as a **link** off-site to sunypoly.edu, not a content page |
| 3 | Test 3: Ampersand & Em-Dash — Special Characters | Pipeline Test → third | `&` and `—` both render correctly in the title *and* in the body |
| 4 | Test 4: Nested Two Levels Deep | Pipeline Test → Test Submodule → | Stays two levels down; not flattened up |
| 5 | Test 5: First Item in a New Module Container | Modules → Module1 → | Both containers were created by the import |

## Regression check on existing content

- **Welcome** still has its 5 topics, same order, nothing duplicated.
- **Toolkit** still has its 10 topics, same order, nothing duplicated.
- No stray "exporter" or "teams" topics (those stubs were folded into the
  fuller guides and are archived).

## Known soft spots to watch

1. **Item 2 is the one to watch.** No COM 216 export contains an
   external-link topic, so its manifest structure
   (`material_type="link"` with the URL in `href`) was inferred rather
   than copied from a real export. If it imports wrong, item 2 is why.
2. New items carry no `d2l_2p0:resource_code` — omitted deliberately
   rather than inventing values that might collide with real content
   objects. Watch for import warnings about missing resource codes.
3. Three pre-existing D2L platform links in *course* pages (not test
   items) point at this specific course instance and will not resolve in
   a sandbox — see the report in chat. Not a test failure.

## After verifying

Report which items passed. Only then does a real cartridge get built for
the live course — and that build drops the whole **Pipeline Test** and
test-item set, keeping only real content.
