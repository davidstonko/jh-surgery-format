# JH Surgery Format

**A Claude formatting skill for the Johns Hopkins Department of Surgery** — The Johns Hopkins Hospital & Johns Hopkins Bayview Medical Center.

Maintained by David P. Stonko, MD, MS. Version 2.1 — August 2026. Installed-skill command: `/jhsurgeryformat`.

## What this is

Tell Claude what you're presenting — *"I'm giving an M&M on Tuesday," "my poster got accepted to ACS," "I need a grand rounds on AAA repair"* — and this skill turns that into a properly branded rough-draft file you finish yourself: a real PowerPoint deck, a correctly sized conference poster, or a letter on official letterhead.

It knows the department's design system (Heritage Blue and gold, the standard title-slide layout, logo rules, footer conventions), the structure of each presentation type, and it **never touches patient information** — case-based drafts are built entirely from bracketed placeholders you fill in on a hospital computer.

## Quick start (no experience with Claude needed)

1. Download **[`JH-Surgery-Format.md`](JH-Surgery-Format.md)** (click the file, then the download icon).
2. Go to [claude.ai](https://claude.ai), start a new chat, and **attach the file**. Works on every plan, including Free (enable "Code execution and file creation" under Settings → Capabilities).
   *Prefer the installed skill?* Download [`jhsurgeryformat.zip`](jhsurgeryformat.zip), go to Customize → Skills → **+ Create skill**, upload the zip, then type **`/jhsurgeryformat`** in any chat.
3. Say what you need in one or two sentences: the type of presentation, your topic, and where/when you're presenting.
4. Answer the couple of questions Claude asks (talk length, background style). You'll get a draft file with `[bracketed placeholders]` wherever your content goes.

That's it. No patient data ever goes into the chat.

## What it can produce

| Format | What you get |
|---|---|
| Grand rounds | Full 16:9 deck: title → disclosure → objectives → body → take-home points |
| M&M conference | The department's rigid case format, entirely from placeholders |
| Conference poster | Sized to your conference's spec (Claude looks it up), navy/gold three-column system, IRB + contact footer |
| Podium / plenary talk | Findings-first slides, methods as a visual timeline, one message per slide |
| Invited case presentation | Imaging-led narrative with decision-point slides and TEACHING POINTS closer |
| Journal club | PICO → methods → results → critical appraisal → discussion questions |
| Letter on letterhead | Official JHH letterhead layout, optional grammar audit with redline edits |
| Anything else | The adaptability rule: Claude builds it from the same colors, fonts, and logo rules |

## Already a Claude power user? Install the skill anyway

The installed skill is the token-efficient path, not just the beginner path:

- **Near-zero standing cost:** until invoked, only the skill's one-line description sits in context; the reference files (brand catalog, image library, CME language) load only when a task needs them.
- **Cache-friendly by construction:** the skill text is identical in every session, so it lives in the cached prompt prefix rather than being re-tokenized and reprocessed each conversation — unlike instructions you paste fresh each time, which are never cache-identical twice.
- **Replaces the expensive habit:** attaching an old deck as a style reference costs 10–100× the tokens of this entire skill on every use. The skill is that deck's design system, pre-extracted once.
- **Fewer turns:** intake is one round of questions; hex codes, slide geometry, logo rules, and per-format structures are pre-computed, so Claude doesn't spend turns (and context) rediscovering them — and consistent rules mean fewer revision cycles, which are the real token sink.

## What's in this repository

| Path | Purpose |
|---|---|
| [`JH-Surgery-Format.md`](JH-Surgery-Format.md) | **The attachable single file** — everything inlined; this is what most people need |
| [`jhsurgeryformat.zip`](jhsurgeryformat.zip) | Installable skill package for claude.ai (Customize → Skills → upload) |
| [`jh-surgery-format.skill`](jh-surgery-format.skill) | Same package in .skill form (for Claude Code / Cowork) |
| [`skill/SKILL.md`](skill/SKILL.md) | The skill source (same content, package form) |
| [`skill/references/`](skill/references/) | Brand asset catalog, approved image library, CME language (reference only) |
| [`skill/assets/`](skill/assets/) | Official logo PNGs (JHM · JHH · Bayview; color/reversed/BW, H/V) and approved campus photos |

## The rules the skill enforces (summary)

- **No PHI, ever.** Placeholders only; clinical details get added on hospital machines.
- **Logos:** plain Johns Hopkins Medicine logo on deck title slides only; no logo on content slides; full hospital lockup (JHH or Bayview, by where the work was done) on posters; official letterhead for letters. Never redraw, recolor, or stretch a logo.
- **Design:** Heritage Blue `#002D72` + gold `#F1C400`, Arial, 16:9 at 13.33"×7.5", findings-first titles, auto-updating date and slide-number fields (no macros).
- **CME/accreditation language stays out of decks** — the department handles it separately.

## Contributing / updating

This is a living document. If a conference changes its poster specs, the department updates a template, or you find something the skill gets wrong, open an issue or PR — or send it to Dr. Stonko. The brand assets come from the [Johns Hopkins Brand Portal](https://assets.jh.edu) (JHED login); please don't redistribute logo files outside Hopkins.

---

*Built with Claude. All example content in the skill is placeholder-based; no patient information is present anywhere in this repository.*
