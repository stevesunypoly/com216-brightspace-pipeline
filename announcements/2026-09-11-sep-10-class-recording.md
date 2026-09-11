---
title: "Announcement — Sep 10 class recording is posted"
doc-kind: announcement-draft
course: COM 216
course-title: Digital Media, Information, and Society
term: Fall 2026
audience: students
version: v1
version-date: 2026-09-11
status: ready-to-post
posted: false
purpose: "Paste-ready Brightspace announcement publishing the September 10 class recording. Kept here as the archive of what was posted, since announcements are live-managed in Brightspace per pipeline §5 and the Brightspace MCP server is read-only."
note: "Post via Course Admin > Announcements > New Announcement. Switch the editor to source view (</> button) and paste the HTML block below. Set posted: true and record the real date once it is live."
---

## Headline

```
Thursday's class recording is posted
```

## Body — paste into the announcement editor's HTML source view

```html
<p>The recording of Thursday's class (September 10) is up. It plays in Microsoft Stream &mdash; sign in with your SUNY Poly account if you are prompted.</p>
<p><a href="https://sunypoly.sharepoint.com/:v:/s/team-COM216/IQDyef1JDF3HRZrF9W-C2b27AT9uzxgDPkZhOOjaZU5EzeI?e=tI7gUb&amp;nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D" target="_blank" rel="noopener"><strong>Watch the September 10 class recording</strong></a></p>
<p>Two things worth knowing before you sit down with it. Stream shows a transcript beside the video, so you can search the session for a term rather than scrubbing for it, and you can raise the playback speed. Use the recording to recover something specific &mdash; a link, an instruction about the workbench, a thread you want to quote &mdash; rather than replaying the hour end to end.</p>
<p>From now on recordings will also live in Content, under <strong>Class Recordings</strong>, so you do not have to dig back through announcements to find an old one.</p>
<p>If the link does not open for you, tell me what you saw: a sign-in loop, an access-denied page, or a video that will not play. Those are three different problems.</p>
```

## Suggested settings

- **Start date:** now
- **End date:** leave empty — this one should stay up, unlike the dated
  "bring a laptop" notices
- **Show date posted:** yes, matching every existing item in `news_d2l.xml`

## After the cartridge is imported

Once the **Class Recordings** module exists in Content, Brightspace will
generate a quicklink rcode for the recording topic. At that point the
paragraph beginning "From now on recordings will also live in Content" can
be turned into a real internal link, the way the existing announcements
link to Assignment 0 and to the Workbench. The rcode cannot be written in
advance — it does not exist until import creates the topic.
