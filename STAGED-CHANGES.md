---
title: "Staged changes awaiting the next cartridge build"
doc-kind: staging-log
course: COM 216
term: Fall 2026
version-date: 2026-09-11
status: active
purpose: "Running list of content changes made since the last cartridge build, per CONTENT-PIPELINE.md §4. Cleared when a build ships."
---

# Staged changes — not yet built

Per pipeline §4, changes accumulate here until roughly five have collected
or the instructor asks for a build. **"Build", "regenerate", "make the
cartridge" are the trigger phrases.** Rendering HTML is not permission to
repackage.

## Since last build (last build: COM216-single-topic-test-2026-09-07.zip)

| # | Date | Change | Files |
|---|---|---|---|
| 1 | 2026-09-11 | **New:** Sep 10 class recording topic, in a **new top-level `Class Recordings` module container** | `brightspace-md/Class-Recordings/2026-09-10-class-recording.md`, `brightspace-html/Class-Recordings-2026-09-10-class-recording.html` |

Staged changes since last build: **1 of ~5**

## Decisions needed at build time

- **New module container.** `Class Recordings` does not exist in the
  2026-09-03 export. Import must create it. This is the verified test-05
  case, so the path is known-good, but it is a structural change to a live
  course and worth a deliberate confirmation rather than a silent one.
- **Manifest identifiers.** Highest existing `d2l_2p0:id` in
  `brightspace-cartridge-base/imsmanifest.xml` is **19**; the container and
  its first topic continue from **20**. Existing `identifier` values are in
  the `656…`/`657…` range, so a fresh prefix is needed for the new items.
- **Announcements stay out of the cartridge.** Per §5, `news_d2l.xml` is
  excluded from packaging. The Sep 10 announcement is posted live in
  Brightspace; its text is archived under `announcements/`.

## Related, not part of the build

- `announcements/2026-09-11-sep-10-class-recording.md` — paste-ready
  announcement, posted by hand in Brightspace. Set `posted: true` in its
  frontmatter once it is live.
