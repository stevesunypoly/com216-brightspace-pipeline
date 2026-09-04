---
title: "Browser Extension: Exporter"
tags: [com-216, toolkit]
doc-kind: toolkit-install
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: students
module: Toolkit
order: 80
purpose: "Install instructions for the Claude Interaction Exporter browser extension."
source-html: "Toolkit-Exporter-Install.html"
version: v1
version-date: 2026-09-03
status: published
note: "Reverse-derived from the live Brightspace export (D2LExport_2939842_2026FA-UTI-COM216-1594_20269346.zip, 2026-09-03) per pipeline \u00a76."
---

<div class="note">

Repository:
[github.com/StrivenWord/Claude-Interaction-Exporter<span class="visually-hidden">
(external
site)</span>](https://github.com/StrivenWord/Claude-Interaction-Exporter).
It has no backend — it calls the same Claude.ai API the site itself uses
and writes files straight to your computer. No account, no analytics, no
third-party server.

</div>

## 1\. Download the code

1.  Open the repository page:
    [github.com/StrivenWord/Claude-Interaction-Exporter<span class="visually-hidden">
    (external
    site)</span>](https://github.com/StrivenWord/Claude-Interaction-Exporter).
2.  Click the green **Code** button → **Download ZIP**.
3.  Unzip it somewhere you won't move or delete — Chrome loads the
    extension directly from this folder, not a copy of it. It should
    contain `manifest.json` at the top level.

## 2\. Turn on Developer mode in Chrome

1.  Go to `chrome://extensions/` (paste directly into the address bar).
2.  Flip the **Developer mode** toggle in the top-right corner. This
    unlocks the buttons needed to load an extension that isn't from the
    Web Store.

## 3\. Load it as an unpacked extension

1.  With Developer mode on, click **Load unpacked** (top-left of the
    extensions page).
2.  Select the unzipped folder — the one containing `manifest.json` —
    and confirm.
3.  The extension appears in the list and in the toolbar. Click the
    puzzle-piece icon and pin it for easy access.

## 4\. Connect it to your Claude account

One-time setup so the extension knows which organization's conversations
to read:

1.  Sign in to [claude.ai<span class="visually-hidden"> (external
    site)</span>](https://claude.ai).
2.  In a new tab, open `https://claude.ai/api/organizations` — this
    returns raw JSON, which is expected.
3.  Find the value after `"uuid":` (a string like
    `1a2b3c4d-5e6f-7890-abcd-ef1234567890`) and copy it, without the
    quotation marks.
4.  Right-click the extension's toolbar icon → **Options**.
5.  Paste the ID into **Organization ID**, click **Save Settings**, then
    **Test Connection** — it should report how many conversations it
    found.

## 5\. Use it

  - **Single export**: open a conversation or Cowork session, click the
    extension icon, pick a format (Markdown, plain text, or JSON), and
    click Export.
  - **Bulk export**: click the icon → **Browse All Conversations** to
    search, filter, select rows, and export several at once as a ZIP.

## Keeping it updated

Since it's loaded from a folder rather than the Web Store, updates
aren't automatic. To update: download the latest ZIP from the
repository, replace the folder's contents, then go to
`chrome://extensions/` and click the reload icon on the extension's
card.

<div class="warn">

Chrome will label this "unpacked" and may warn about extensions not from
the Web Store — expected for anything loaded this way, not a sign of a
problem specific to this extension. Only load unpacked extensions from a
source you trust; the code has full read/write access to your data on
`claude.ai` while active.

</div>
