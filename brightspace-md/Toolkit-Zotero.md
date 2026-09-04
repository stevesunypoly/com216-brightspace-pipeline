---
title: "Zotero"
tags: [com-216, toolkit]
doc-kind: toolkit-install
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: students
module: Toolkit
order: 90
purpose: "Setup guide for Zotero as the course's reference-management tool."
source-html: "Toolkit-Zotero.html"
version: v1
version-date: 2026-09-03
status: published
note: "Reverse-derived from the live Brightspace export (D2LExport_2939842_2026FA-UTI-COM216-1594_20269346.zip, 2026-09-03) per pipeline \u00a76."
---

<div class="note">

This is a walkthrough to follow yourself: Zotero is desktop software and
a browser extension, and installing or running either happens on your
own machine, not inside this document. Follow the steps below, then fill
in the two timestamps at the bottom as your proof.

</div>

## 1\. Download

<div class="table-scroll">

| Component                            | Where                                                                                                                                                                                                                                                                      |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Zotero desktop app                   | [zotero.org/download<span class="visually-hidden"> (external site)</span>](https://www.zotero.org/download/) — choose the build for your OS (Windows, macOS, or Linux) and install it normally.                                                                            |
| Zotero Connector (browser extension) | Offered on the same download page, or install directly from your browser's extension store (Chrome Web Store, Firefox Add-ons, or Edge Add-ons — search "Zotero Connector"). It adds a save button to the toolbar that saves whatever page you're on directly into Zotero. |

Zotero components and where to get them

</div>

## 2\. Installation

1.  Run the Zotero installer and open the app once to let it finish
    setup.
2.  Install the Zotero Connector in whichever browser you use for
    research.
3.  In Zotero, go to **Edit → Preferences → Advanced** and note the data
    directory — this is the local Zotero database, separate from any
    export you'll place in the Workbench.
4.  In **Preferences → General → File Handling**, tick **Automatically
    attach associated PDFs and other files when saving items**. This
    makes the Connector pull down a PDF of the page (when one is
    available) at the same moment it saves the citation.
5.  Optional but recommended: create a free account at
    [zotero.org/user/register<span class="visually-hidden"> (external
    site)</span>](https://www.zotero.org/user/register) and sign in
    under **Preferences → Sync** so the library backs up online, not
    just locally.

## 3\. Create your first library and save an entry

1.  Open Zotero. The default library ("My Library") is created
    automatically — this is your first library.
2.  Visit the first source with the Connector installed:  
    [Exotic Mind-like Entities: A New Vocabulary for Artificial
    Intelligence<span class="visually-hidden"> (external
    site)</span>](https://levysoft.medium.com/exotic-mind-like-entities-a-new-vocabulary-for-artificial-intelligence-be1511915cb9)
    — Antonio Troise, Medium, May 6, 2025.
3.  Click the Connector icon in the browser toolbar to save the page
    into the library. Zotero will pick up the title, author, and date
    automatically, and — with the file-handling preference above enabled
    — attach a PDF snapshot of the page as a child item underneath it.
4.  Click the disclosure triangle next to the new entry in Zotero's
    middle pane and confirm a PDF attachment is listed underneath it. If
    none appears (some pages don't offer a direct PDF), open the item
    and use **right-click → Add Attachment → Attach Link/File to
    Snapshot** to attach one manually.
5.  **Export the library**: right-click the library in Zotero → **Export
    Library…** → choose a format (BibTeX or CSL JSON both work well for
    a growing library). In the export dialog, tick **Export Notes** so
    any notes attached to items are included, and tick **Keep Updated**
    — this turns the export into a live file that Zotero automatically
    rewrites whenever the library changes, instead of a one-time
    snapshot. Save it into the `zotero/` subfolder of the Workbench.
6.  **Note the timestamp** on that exported file (its "date modified,"
    visible in Finder/Explorer or via `ls -l`). Record it below — this
    is proof-of-state \#1.

## 4\. Add a second entry and confirm it updates itself

1.  Visit the second source:  
    [Talking about Large Language Models<span class="visually-hidden">
    (external site)</span>](https://dl.acm.org/doi/pdf/10.1145/3624724)
    — Murray Shanahan, *Communications of the ACM*, Vol. 67, No. 2,
    pp. 68–79, Jan 25, 2024 (DOI: 10.1145/3624724).
2.  Save it into the same library with the Connector, the same way as
    the first entry, and again confirm a PDF attachment appears
    underneath it. The ACM Digital Library page may be paywalled
    depending on your access — if the Connector can't fetch the PDF
    automatically, download it yourself while logged into your
    institution's ACM access and attach it to the item the same way as
    above.
3.  With **Keep Updated** ticked, Zotero rewrites the exported file in
    `zotero/` on its own within a few seconds — no manual re-export
    needed.
4.  Check the file's timestamp again. If it moved forward from step 3,
    that's the proof: the library changed, and the live export in the
    Workbench picked it up automatically.

## Proof-of-state log

<div class="table-scroll">

| Step       | Library contents                           | PDF attached? | Exported file timestamp |
| ---------- | ------------------------------------------ | ------------- | ----------------------- |
| 1st export | 1 entry — Troise (2025)                    | \[\[ Y/N \]\] | \[\[ fill in \]\]       |
| 2nd export | 2 entries — Troise (2025), Shanahan (2024) | \[\[ Y/N \]\] | \[\[ fill in \]\]       |

Proof-of-state log for the two Zotero exports

</div>

## Reference: what the export should contain

A BibTeX export with both entries looks roughly like this:

<div class="bib">

@misc{troise2025exotic, author = {Troise, Antonio}, title = {Exotic
Mind-like Entities: A New Vocabulary for Artificial Intelligence}, year
= {2025}, month = {5}, url =
{https://levysoft.medium.com/exotic-mind-like-entities-a-new-vocabulary-for-artificial-intelligence-be1511915cb9},
note = {Medium} } @article{shanahan2024talking, author = {Shanahan,
Murray}, title = {Talking about Large Language Models}, journal =
{Communications of the ACM}, volume = {67}, number = {2}, pages =
{68--79}, year = {2024}, doi = {10.1145/3624724}, url =
{https://dl.acm.org/doi/10.1145/3624724} }

</div>

## Where it lives

Per the Workbench layout, the exported file (e.g. `library.bib`) sits in
`Workbench/zotero/` alongside any other Zotero exports, and gets swept
up automatically each week when the whole Workbench folder is zipped for
Brightspace.
