# Paçoca

An unofficial, searchable index of Lineage II **Main Server** update notices for the
**Eva / Wolf / Valakas** and **Ilseom / Baldo** servers, covering
**11 February to 27 May 2026**.

Available in Korean, English, Portuguese, Spanish, and French.

**https://heartstove.github.io/pacoca**

---

## What this is

The official update board splits its weekly maintenance notices into `[본서버]`
(Main Server) and `[말하는섬]` (Talking Island). Eva, Wolf, Valakas, Ilseom and
Baldo all live under `[본서버]`, and each notice separates server-specific changes
in its body using subheadings like `[... - 에바&울프&발라카스/일섬&발도 서버]`.

This site pulls those apart so you can answer "what changed for *my* server"
without reading sixteen notices end to end. It covers 17 notices and 1,412
change items.

Colour is semantic, not decorative:

- **Oxblood**: the change names your servers explicitly.
- **Steel**: the change carries no server tag, so it applies everywhere, your
  servers included. These are easy to miss and are *not* filler.

## What this is not

- **Not official.** No affiliation with NCSOFT. All source content is theirs.
- **Not a mirror.** Each section shows at most six items and then points at the
  original notice. Exact figures, full item lists and tables stay on the
  official board, where they belong.
- **Not authoritative in translation.** See below.

## On the translations

Korean is the source of truth. Everything else is **machine translation**,
generated once and reviewed only by spot check.

Item, skill and monster names are the weak point. The translator was given a
fixed glossary for recurring terms (`기란의 인장` becomes Giran Seal, `정기점검`
becomes scheduled maintenance, and so on), but names outside that glossary are
rendered literally and will **not** match the official localised names used in
Western Lineage II clients. Treat them as pointers, not as canonical.

Every non-Korean view has a **"Show Korean original"** toggle that prints the
source line beneath each translated one. If a translation looks wrong, it
probably is. Check the Korean, then follow the link to the notice.

## Known quirks in the source data

Some notices tag their subheadings **without Wolf**, for example
`[본/에바/발라카스 서버]`. Whether that is a typo on NCSOFT's part or a genuine
scope difference is not something the notices make clear. Those sections carry a
**"Wolf not listed"** flag rather than being silently normalised. Verify in game
before relying on them.

Dates are the KST posting date. The API serves UTC, and notices post at 23:00
UTC, so a naive read shifts every update back by a day.

## Rebuilding

The page is a single self-contained `index.html`: no build step, no
dependencies, no external requests, no tracking. It is generated from crawled
data by a separate crawler project:

```sh
python3 scripts/build_site.py /path/to/pacoca
```

Data comes from the public JSON API behind `lineage2.plaync.com`, fetched
serially with a delay between calls.

## Licence

Site code: MIT.

Everything quoted, summarised or translated from the update notices remains the
copyright of **NCSOFT Corporation**. This is a fan-made index published in the
belief that a linked, capped summary is fair use. If NCSOFT disagrees, open an
issue and it comes down.
