# Ogunquit Playhouse Docs

Public, rendered markdown for Ogunquit Playhouse production documentation.

**Status:** M0 bootstrap. Content tree empty. Engine not yet ported.
**Audience:** the folks at OPH. This is the only rendering link they know about.
**Live site (target):** `https://mawizorek.github.io/oph-docs/`

---

## 1. Read this first

**The architecture lives in one place and it is not this file.** The doc-tree rule, the frontmatter contract, the object declarations, the build-hook order, the size budget, and the cross-repo link mechanism are all specified in the URITP archive README, which is the current source of truth for how every one of these sites is built:

👉 **https://github.com/mawizorek/uritp-doc-archive/blob/main/README.md**

This README covers only what is TRUE OF THIS SITE AND NOTHING ELSE. That split is deliberate and it is the whole point of the design: shared architecture is stated once, site facts are stated locally, and nothing is duplicated between repos. **If you find yourself copying a paragraph out of the URITP README into this one, stop.** A copied paragraph is a paragraph that will be wrong here in three months while still being right there, and nobody will notice until it matters.

When the engine is extracted to its own repo, this pointer moves to the engine README. The pointer moves; the pattern does not.

---

## 2. What this site is

Venue information, technical standards, and production reference for Ogunquit Playhouse. Same shape as URITP: markdown in, styled public site out.

**Honest note about this repo's role in the wider plan:** OPH is structurally very close to URITP. Both are theatres, both document venues and spaces and production standards, both want the same object types. That makes this repo the EASY sibling, and it means a successful build here proves less than it looks like it proves. It confirms the engine can be pointed at a second site; it does not confirm the engine is free of theatre-shaped assumptions, because OPH is also theatre-shaped. The repo that actually tests that is `hml-docs`, which has no venues at all.

Worth stating plainly so nobody reads a green build here as the portability question being settled.

---

## 3. What is different here

Everything site-specific and nothing else. When the engine lands, these are the only files in this repo that will not be identical to their URITP counterparts:

| Thing | Value here |
|---|---|
| Site name | Ogunquit Playhouse |
| Base URL | `https://mawizorek.github.io/oph-docs/` |
| Audience | OPH staff and guest artists |
| Palette / theme | **Deliberately not URITP's.** See below. |
| Peers | `uritp` (and `hml` once it exists) |
| Object types | Expected to reuse the base set. Divergence gets logged, not silently added. |

**On the theme:** these two sites should NOT look identical. A shared palette is a trap already named in the architecture README, because the day someone edits a shared colour to fix URITP is the day this site breaks in a way nobody notices for a month. Look is local. Structure is shared.

---

## 4. The engine

This repo does not contain the renderer and should never contain a copy of it.

The target consumption model is a **pinned reusable workflow**: this repo's deploy workflow will be a handful of lines naming an engine version, and the hooks install as a pinned dependency. Two rules that come with that, both non-negotiable:

- **Pin by tag, never by branch.** The entire reason these are separate repos is that they fail separately. A floating reference re-couples them and one bad engine commit takes down every site at once.
- **URITP moves first.** URITP tracks the moving tag and is the canary, because it is Michael's own staff and the lowest-stakes audience. This repo pins an exact version and only advances after URITP has run on it. The people at OPH never see a bad Tuesday.

Until the engine repo exists, the render tree is copied in from URITP as a starting point and that copy is understood to be **temporary and tracked**, not the destination.

---

## 5. Access, stated honestly

This repo is public and so is the site. A GitHub Pages site is publicly reachable even when its repository is private, so the distinct link is **audience separation, not access control**. OPH people only know this URL; that is a routing fact, not a security boundary.

Fine for venue specs and production standards. Not a place for anything that would matter if a stranger read it.

---

## 6. Working in here

- Branch, commit, PR, self-merge. Never direct to `main`.
- The doc tree holds markdown and nothing else. Ever. (Architecture README, THE RULE.)
- Site-specific decisions get logged here. Architecture decisions get logged in the architecture repo. A decision recorded in the wrong repo is a decision the other two sites will never inherit.

---

*Bootstrapped 2026-08-03 alongside `uritp-doc-archive` and `hml-docs`. Filenames and conventions are pending the cross-repo naming lock; see the architecture README, section 12.*
