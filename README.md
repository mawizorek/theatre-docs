# Ogunquit Playhouse Docs

Public, rendered markdown for Ogunquit Playhouse production documentation.

**Status:** M1. Content tree STARTED: six authored pages (`practice/paper-tech`, `venues/index`, `venues/ogunquit-playhouse/index`, two lighting references, plus the site index) and two TSV data sidecars. Engine extracted to `doc-render-engine`; **not yet pinned here.**
**Audience:** the folks at OPH. This is the only rendering link they know about.
**Live site (target):** `https://mawizorek.github.io/theatre-docs/` ⚠️ derived from the repo name; Pages configuration has not been read and may carry a custom domain.

---

## 1. Read this first

**The architecture lives in one place and it is not this file.** The doc-tree rule, the frontmatter contract, the object declarations, the build-hook order, the size budget, and the cross-repo link mechanism are specified by the engine and the template site:

👉 **Renderer, schema and build law:** https://github.com/mawizorek/doc-render-engine/blob/main/README.md and the executable contract at https://github.com/mawizorek/doc-render-engine/blob/main/objects/_base.yml
👉 **Authoring contract (frontmatter, links, markers, callouts, data tables):** https://github.com/mawizorek/template-docs/blob/main/authoring/index.md

🪦 **This pointer used to name `mawizorek/uritp-doc-archive`.** That repo no longer exists; it was renamed to `mawizorek/uritp-docs` and is now 🔒 PRIVATE. **GitHub's rename redirect means reads against the dead name still succeed,** so that pointer did not fail, it silently served a different repo. Corrected 2026-10-10. The engine extraction this README anticipated has HAPPENED, which is why the destination is the engine now and not a sibling site's README.

This README covers only what is TRUE OF THIS SITE AND NOTHING ELSE. That split is deliberate and it is the whole point of the design: shared architecture is stated once, site facts are stated locally, and nothing is duplicated between repos. **If you find yourself copying a paragraph out of the engine or template docs into this one, stop.** A copied paragraph is a paragraph that will be wrong here in three months while still being right there, and nobody will notice until it matters.

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
| Base URL | `https://mawizorek.github.io/theatre-docs/` (unverified) |
| Audience | OPH staff and guest artists |
| Palette / theme | **Deliberately not URITP's.** See below. |
| Peers | `uritp-docs`, `hml-docs` |
| Object types | Reusing the base set so far: `procedure`, `venue`, `reference`, `index`. Divergence gets logged, not silently added. |

**On the theme:** these two sites should NOT look identical. A shared palette is a trap already named in the architecture docs, because the day someone edits a shared colour to fix URITP is the day this site breaks in a way nobody notices for a month. Look is local. Structure is shared.

---

## 4. The engine

This repo does not contain the renderer and should never contain a copy of it.

The target consumption model is a **pinned reusable workflow**: this repo's deploy workflow will be a handful of lines naming an engine version, and the hooks install as a pinned dependency. Two rules that come with that, both non-negotiable:

- **Pin by tag, never by branch.** The entire reason these are separate repos is that they fail separately. A floating reference re-couples them and one bad engine commit takes down every site at once.
- **URITP moves first.** URITP tracks the moving tag and is the canary, because it is Michael's own staff and the lowest-stakes audience. This repo pins an exact version and only advances after URITP has run on it. The people at OPH never see a bad Tuesday.

⚠️ **Current state, stated honestly:** `doc-render-engine` now exists and is active, but **no workflow is checked in here and no engine version is pinned.** This repo publishes through Pages with `.nojekyll` and nothing else. The pinned-workflow model above is still the target, not the situation.

---

## 5. Access, stated honestly

This repo is public and so is the site. A GitHub Pages site is publicly reachable even when its repository is private, so the distinct link is **audience separation, not access control**. OPH people only know this URL; that is a routing fact, not a security boundary.

Fine for venue specs and production standards. Not a place for anything that would matter if a stranger read it.

---

## 6. Working in here

- Branch, commit, PR, self-merge. Never direct to `main`.
- **The doc tree holds markdown, plus the TSV data sidecars a page declares in its `data:` slot.** A sidecar sits beside its page and shares the page's filename stem. Nothing else. Ever.
  - 🪦 This rule previously read *"markdown and nothing else. Ever."* while `circuits-and-dimmers.tsv` and `where-dimmers-run.tsv` already sat in the tree and were addressed by live `!!! data` blocks. The data-slot design is correct; the sentence was not, and a rule a cold agent would obey to the letter had to be made true. Corrected 2026-10-10.
- Site-specific decisions get logged here. Architecture decisions get logged in the engine or template repo. A decision recorded in the wrong repo is a decision the other two sites will never inherit.

---

*Bootstrapped 2026-08-03 alongside `uritp-docs` (then named `uritp-doc-archive`) and `hml-docs`. Filenames and conventions are pending the cross-repo naming lock.*

*Currency pass 2026-10-10 under DOC REVIEW 001 (Documentation Team): status line, architecture pointer, markdown-only rule, base URL and peer repo names. Nothing in the content tree was touched.*
