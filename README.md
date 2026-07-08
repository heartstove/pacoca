# Paçoca

An unofficial, searchable index of Lineage II update notices, split by which
servers each change applies to.

Covers all seven servers the update board speaks about: **Main, Eva, Wolf,
Valakas, Ilseom, Baldo** and **Talking Island**.

Korean and English.

**https://heartstove.github.io/pacoca**

---

## What this is

The official update board files each weekly maintenance notice under one server
family: `[본서버]` (Main, Eva, Wolf, Valakas, Ilseom, Baldo) or `[말하는섬]`
(Talking Island). Inside a notice, some subheadings name specific servers, like
`[... - 에바&울프&발라카스/일섬&발도 서버]`, while the rest apply to every server
in that notice.

This site pulls those apart so you can answer "what changed for *my* server"
without reading every notice end to end.

Colour is semantic, not decorative:

- **Oxblood**: the subheading names your server explicitly.
- **Steel**: the subheading names no server, so it applies to every server in
  that notice, yours included. These are easy to miss and are *not* filler.

Talking Island notices never name servers in their subheadings, since there is
only one server in that family. Filtering to Talking Island and then asking for
"only items naming a server" is therefore empty by construction, and the page
says so rather than showing a blank list.

## What this is not

- **Not official.** No affiliation with NCSOFT. All source content is theirs.
- **Not a mirror.** Each subheading shows at most six items and then links to
  the original notice. Exact figures, full item lists and tables stay on the
  official board, where they belong.
- **Not complete history.** The site carries a rolling window of recent
  notices. Older ones remain on the official board, linked from the header.
- **Not authoritative in translation.** See below.

## On the translation

Korean is the source of truth. English is **machine translation**, generated
once and reviewed only by spot check.

Item, skill and monster names are the weak point. The translator works from a
fixed glossary for recurring terms (`기란의 인장` becomes Giran Seal, `정기점검`
becomes scheduled maintenance, and so on), but names outside that glossary are
rendered literally and will **not** match the official localised names used in
Western Lineage II clients. Treat them as pointers, not as canonical.

The English view has a **"Show Korean original"** toggle that prints the source
line beneath each translated one. If a translation looks wrong, it probably is.
Check the Korean, then follow the link to the notice.

## Known quirks in the source data

Some notices tag their subheadings **without Wolf**, for example
`[본/에바/발라카스 서버]`. Whether that is a typo on NCSOFT's part or a genuine
scope difference is not something the notices make clear. Those sections carry a
**"Wolf not listed"** flag rather than being silently normalised. Verify in game
before relying on them.

`본 서버` (Main) is its own server, distinct from Eva, Wolf and Valakas, even
though all four are filed under the `[본서버]` board tag.

Dates are the KST posting date. The API serves UTC, and notices post at 23:00
UTC, so a naive read shifts every notice back by a day.

## Rebuilding

The page is a single self-contained `index.html`: no build step, no
dependencies, no external requests, no tracking. It is generated from crawled
data by a separate crawler project:

```sh
python3 scripts/crawl.py            # refresh the rolling window
python3 scripts/build_site.py ~/pacoca
```

Data comes from the public JSON API behind `lineage2.plaync.com`, fetched
serially with a delay between calls.

## Licence

Site code: MIT.

Everything quoted, summarised or translated from the update notices remains the
copyright of **NCSOFT Corporation**. This is a fan-made index published in the
belief that a linked, capped summary is fair use. If NCSOFT disagrees, open an
issue and it comes down.
