---
name: jhsurgeryformat
description: Create Johns Hopkins Department of Surgery presentation drafts — grand rounds, M&M conference, conference posters (any size), podium/plenary research talks, invited case presentations, journal club decks, and letters on official letterhead — with correct JHH or Bayview branding, logo selection, and strict no-PHI placeholders. Use when a Department of Surgery member asks for help starting, drafting, or formatting any presentation, poster, talk, or letter.
---

# JH Surgery Format

A formatting skill for the Department of Surgery, The Johns Hopkins Hospital & Johns Hopkins Bayview Medical Center. It turns a brief description ("I'm giving an M&M on Tuesday", "my poster got into ACS", "I need a grand rounds on AAA repair") into a properly branded rough-draft file the presenter finishes themselves.

**For colleagues new to Claude:** attach this file (or install it as a skill and type `/jhsurgeryformat`), then say in one or two sentences what you need — the type of presentation, your topic, and where/when you're presenting. Claude will ask a couple of questions and build you a starting draft as a real PowerPoint or Word file. You never need to paste patient information — the draft uses placeholders you fill in later on a hospital computer.

**For colleagues already fluent with Claude:** install this as a skill rather than re-explaining the house style each time. As an installed skill, only its one-line description occupies context until it's invoked, the reference files load on demand, and the skill text is byte-identical every session — so it sits in the cached prompt prefix instead of being reprocessed each conversation. Compare that with the alternatives: pasting formatting instructions fresh each time (different tokens every session, no cache reuse, inconsistent results) or attaching an old deck as a style exemplar (parsing a .pptx can cost 10–100× the tokens of this whole skill, every single time). The skill also front-loads the answers Claude would otherwise burn turns rediscovering — exact hex values, slide geometry, logo rules, blueprint structures — which means fewer clarifying questions, fewer revision cycles, and more of the context window left for your actual science.

---

## Step 1 — Intake

Determine the following, asking only for what the user hasn't already said (keep it to one short round of questions):

1. **Format:** grand rounds · M&M · conference poster · podium/plenary research talk · invited case presentation · journal club · letter on letterhead.
2. **Hospital (JHH vs. Bayview):** determined by where the work was done. This drives the affiliation line, the closing-slide campus photo, and — on posters — which hospital lockup appears. (For decks the title-slide logo is plain JHM either way; you still need the hospital for the affiliation line and closing-slide photo — infer it from context and ask only if genuinely unclear.) Authors at both hospitals or a multi-site project → ask which hospital should be the focus, or whether both appear.
3. **Venue and date** (conference name, city, meeting dates; or internal venue).
4. **Talk length / slide budget** (a 5-minute quick-shot vs. 45-minute grand rounds changes slide count).
5. **Topic and whatever content exists** (aims, key results, figures they plan to include).
6. **Authors and degrees** — degrees are listed on external conference materials ("First M. Last, MD, MS; …"); plain names are acceptable for internal talks.
7. **For posters only:** which conference accepted it (see the poster sizing rule below), plus the **Johns Hopkins IRB number, contact email, and lab URL** for the footer.

## Step 2 — PHI guardrail (hard rule, never skip)

- **Never place patient-identifying information in any generated file**: no names, initials, MRNs, exact dates of care, or identifiable images.
- Case-based formats (M&M, case presentation) are generated **entirely from bracketed placeholders**: `[age]`, `[sex]`, `[mechanism/diagnosis]`, `[POD #]`, `[imaging placeholder]`, `[complication 1]`, etc.
- If the user pastes real patient details, generalize them into placeholders in the draft and remind them (once, briefly) that clinical details should be added on a secure hospital machine.
- Do not put the CME language or any confidentiality statement into any deck — see Appendix B.

## Step 3 — The design system

### Colors

| Role | Hex | Use |
|---|---|---|
| Heritage Blue | `#002D72` (PMS 288) — **generate with this hex**; `#002C77` appears in older decks, do not use for new work | Dominant structural color: title bands, footer bars, section headers |
| Gold accent | `#F1C400` (PMS 7406; poster titles use `#FFD96E`) | Thin accent stripes, poster title text — never body text |
| Poster navy | `#264162` | Poster header/section bars and stat boxes |
| Light blue fills | `#DCE6F1`, `#F2F6FC` | Poster panel backgrounds, table shading |
| Charcoal | `#404040` family | The "grey option" background system for grand rounds |
| Body text | `#141414` / black | All body copy |
| Red | `#FF0000` | **Critical emphasis only** (complications, alarming values) |

### Typography

**Arial** (or Calibri) throughout; titles bold. Slide type scale: title 36 pt, body 20–28 pt, footer 10–12 pt. Poster: section headers ~44–54 pt, body 24–32 pt, captions ~20 pt italic gray.

### Logo rules (which logo, and where it appears)

**On slide decks (all talk formats):**

- **Title slide only:** the **plain Johns Hopkins Medicine logo** — dome mark + "JOHNS HOPKINS MEDICINE", **without** the hospital line underneath — top-right in the white upper field. This is the default.
- **Content slides carry no logo.** Do not repeat the logo on every slide.
- The hospital identity (JHH vs. Bayview) is conveyed by the **affiliation text**, not the slide logo.

**On posters:** use the **full hospital lockup** (JHM + "THE JOHNS HOPKINS HOSPITAL" or Bayview line) — `H/V-JHH-…` or `H/V-Bayview-…` per the site of the work.

**Letters:** default to the official JHH letterhead template (its own lockup). Bayview-based authors: reproduce the letterhead layout with the Bayview lockup instead.

**Everything else (flyers, one-off formats):** may use either the plain JHM logo or a full hospital lockup depending on what the user wants — ask.

| Output | File |
|---|---|
| Deck title slide (default) | plain JHM logo, transparent PNG (`H-JHM-2` style; reversed `-2R` on dark backgrounds) |
| Poster | full lockup `<H/V>-<entity>-2.eps` (vector) or the 500-DPI PNG |
| Word/letter, white background | packaged `H-<entity>-2.png` (transparent renders fine on white; the `.jpg` variants are portal downloads only) |
| B&W reproduction | `-BW` variants |

`<entity>` = `JHH` or `Bayview`. H (horizontal) for everything except stationery/narrow spaces; V (vertical) for stationery. Never recolor, stretch, add effects to, or re-draw a logo. The packaged `assets/H-JHM-*.png` and `assets/V-JHM-*.png` files are the official plain JHM logos. Download links: `references/brand-assets.md` (or the "Brand asset library" section of the standalone file).

### Slide anatomy (the standard 16:9 talk template — the DEFAULT for all decks)

This white-background system is the default background for every deck this skill generates unless the user picks an alternative.

- **16:9 at 13.33" × 7.5"** is the default for new talks; the official .potx templates are 4:3 — ask before using 4:3.
- **Title slide (exact default layout, top to bottom):**
  1. **Gold band across the full top edge** (~4% of slide height; gradient gold if possible, solid PMS 7406 otherwise)
  2. **White upper field (~40% of height):** large **plain JHM logo** (no hospital line) top-right (roughly a third of the slide width); bold black title, left-aligned, sitting in the lower part of the white field; society/meeting logo top-left when presenting externally
  3. **Heritage Blue panel filling the lower half** of the slide, with presenter/author names in white near its top-left, and beneath them the affiliation subtitle — **default: "Department of Surgery, The Johns Hopkins Hospital, Baltimore, MD"**. Use a division-specific subtitle ("Division of Vascular Surgery and Endovascular Therapy, Department of Surgery, …") **only when the author is confirmed to be in that division**; if unclear, use the general Department of Surgery subtitle
  4. **Footer bar in lighter slate blue** (`#4F669C` family): date (left) · event label (center) · slide 1 (right)
  5. **Thin gold line along the bottom edge**
- **Content slides:** white background; bold title top-left; **no logo**; blue footer bar on every slide; figure-led results (one message per slide, often a full-bleed figure with no title); tables thin-ruled with a p-value column; key phrase of a bullet bolded in blue; red only for critical items.
- **Closer:** "Thanks! / Questions?" slide carrying the **approved campus photo of the hospital where the work was done** (`assets/photos/JHH-1800-Orleans-exterior.jpg` or `assets/photos/JHBMC-Bayview-campus.jpg`) — full-bleed or large right panel, thank-you text on a Heritage Blue overlay or clear-sky area; **backup data slides go after it** for Q&A.
- **Imagery/flair:** prefer approved Hopkins sources (see `references/image-library.md`): Blausen medical illustrations for anatomy/mechanism slides, ACCM clinical photography for context, Dome/Billings images for heritage flair. Never patient-identifiable photos; keep any credit lines intact.
- **Findings-first titles everywhere:** the title states the conclusion ("X Delays Y in Z"), not the topic.

### The grey variant (alternative full-deck background, used at national meetings too)

A complete charcoal alternative to the white default, chosen by presenter preference: charcoal background throughout with white body text; gold band along the top and bottom edges; darker charcoal header band with bold white title and a **thin blue rule beneath it**; light-blue accent graphics (e.g., chevron arrows in timeline diagrams); same footer (date · event · slide #). Title slide: meeting name in the top gold band (top-right), society logo in a white panel top-left, bold white title, author list on charcoal; use the reversed plain JHM logo (`H-JHM-2R.png`) where the layout allows (e.g., lower-right), or omit it when society branding dominates, as in the house exemplar.

### Multi-institution author formatting (title slides)

When authors span institutions: **superscript numbers after each name** ("First M. Last¹·³, Second Author², …") with a numbered affiliation list beneath ("1. Johns Hopkins Hospital  2. [Institution]  3. [Institution]").

## Step 4 — Format blueprints

**Adaptability rule:** these blueprints cover the common cases, but they are not a fence. If the user asks for something not explicitly covered — a visual abstract, a fellowship interview talk, a lab-meeting update, a symposium flyer, a title page for a grant, anything — **do your best to build it using the same colors, fonts, logo rules, and slide anatomy** from Step 3, borrowing structure from whichever blueprint is closest. Ask one or two clarifying questions if the shape is genuinely unclear, then produce a real draft rather than declining.

### A. Grand rounds (45–60 min, CME-accredited series)

Default to the **standard white 16:9 template** (Step 3); alternatives are the **grey variant** (Step 3) or the official blue .potx template backgrounds (rebuild those looks at 16:9 — the .potx files themselves are 4:3, so ask before delivering an actual 4:3 deck). Structure: Title (topic, presenter, "Department of Surgery Grand Rounds", date) → optional presenter-disclosure slide (see G) → Objectives (3–4 learner-oriented bullets) → clinically organized body (anatomy/background → evidence → cases-as-placeholders → technique → outcomes) → "Take-home points" → References → Thanks/Questions. ~1 slide per minute minus discussion. **Do not insert the CME INFORMATION slide** — that is shown separately (Appendix B).

### B. M&M conference

Standard 16:9 template, footer center label "M&M". Structure is rigid:

1. **Slide 1 = the whole case in miniature:**
   - Bold black text block: one-paragraph case synopsis — `[age/sex] [mechanism/diagnosis], requiring [operations/interventions in sequence]`
   - **Heritage Blue band:** `Complication: (1) […], (2) […], (3) […]` in bold white
   - Team block: `Operating Resident/Fellow:` · `Attendings:` · `Service:`
2. Pre-operative Course → 3. Intraoperative Course (OR times as `[OR time]` placeholders) → 4. POD-numbered events / returns to OR → 5. Postoperative course → 6. **Summary** — one dense recap bullet restating the full arc.
- Imaging-heavy middle slides, often untitled full-bleed `[imaging placeholder]` boxes; red text flags critical events. No boilerplate slides of any kind.

### C. Conference poster

**There is no fixed departmental poster size.** When the user names the conference:

1. **Look up that conference's current poster specifications** (web-search the meeting's presenter guidelines).
2. **If specs can't be found, ask the user** for required dimensions/orientation.
3. Adapt the system to the shape. Reference design (from a 48" × 42" exemplar):
   - **Header band (full width, navy `#264162`):** title in gold `#FFD96E`, findings-first; author line with degrees; affiliation line ("Division of …, Department of Surgery, The Johns Hopkins Hospital, Baltimore, MD"); society logo top-left; hospital lockup beneath it (the vertical lockup fits this narrow header stack; use the horizontal lockup if the header gives it room).
   - **Three columns on white** (adjust column count to aspect ratio): left = Background & Objectives → Methods; center = primary figure + key findings; right = performance/secondary results → **Conclusions bottom-right** (reading order ends there).
   - White-on-navy section header bars; a **stat callout row** (large white numbers on navy boxes); figure captions small italic gray; **QR code** bottom-right if there's a companion tool/paper.
   - **Footer strip (navy):** meeting · venue · dates · **Johns Hopkins IRB number** · contact email · lab URL.
   - Print rule: EPS or 500-DPI PNG logos only.

### D. Podium / plenary research talk (5–15 min)

Standard 16:9 template. Title slide: dual logos when collaborative (each in its own white box), findings-first title, full author list with degrees, small event line ("[Meeting], [Year]; City, State"). Structure: Title → Background (1–2) → Rationale → Methods as a **visual timeline** → Results, one message per slide, figure-led → Conclusions (key bullets bolded/underlined) → Thanks → backup slides. A 5-minute quick-shot ≈ 8–10 slides; 15-minute podium ≈ 12–18.

### E. Invited case presentation

Standard 16:9 template. Title: "Case Presentation / [Meeting] / City · Date"; presenter + senior author. Structure: case background (4–6 bullets, bolded diagnosis, all placeholders) → imaging summary ("CT-A Summary", full-bleed `[imaging placeholder]`) → **decision-point question slides** ("Endo Options?" / "Open Options?") → staged management narrative ("Stage 1: …", "Stage 2 (POD #n): …") → current anatomy → post-op → **"TEACHING POINTS"** (all-caps, 3–4 plain declarative lessons; optional light italic sign-off).

### F. Journal club

Standard 16:9 template, footer label "Journal Club". Structure: Title (paper citation, presenter, date) → Why this paper / clinical question (PICO) → Study design & methods (with a design diagram) → Key results (1 result per slide, reproduce-as-placeholder figures with citation) → **Critical appraisal** (strengths | limitations two-column; bias assessment) → Applicability to our patients → Discussion questions (3–4) → citation slide. Full citation in the footer of every content slide.

### G. Disclosure + speaker bio slides (add-on for any talk)

- **Disclosure slide** (immediately after title): "Disclosure" title; bullets following the house pattern — "In-Kind Commercial Support: [company] provided [what] used in this study." · "[Author initials]: [relationship, e.g., received payments from [company] for [purpose]], none related to this work." · closing line "No other authors have anything to disclose." — or simply "No relevant financial relationships to disclose." Add "[Funding source]" if the work was funded.
- **Bio slide** (invited talks, optional): speaker photo placeholder left; name + degrees, title(s), division/department, 3–4 career bullet points right.

### H. Letter on letterhead (JHH template default; Bayview reproduction)

Letters from an individual use the **official JHM personalized-letterhead layout** (brand.hopkinsmedicine.org → Design Standards → Letterhead; specs below). Reproduce it exactly:

- **Header geometry (8.5" × 11", header starts 1/2" from top):** personalization block at **1" from left, 1-3/4" wide** → address block, **3-1/4" wide** → brandmark top-right at **1-5/8" wide** (the vertical hospital lockup: `V-JHH-2.png`, or `V-Bayview-2.png` for Bayview-based authors).
- **Personalization block:** author's name + degrees in **bold** ("Employee Name, M.D., Ph.D"), primary and secondary titles beneath in *italic*. Up to three names fit this configuration.
- **Address block:** first line department/entity name in **bold**, then street address / suite, City, State ZIP, phone ("T"), fax ("F"), and the author's @jhmi.edu email. Placeholders for anything unknown.
- **Typography and color:** print spec is Gill Sans, 8 pt on 10 pt leading — **electronic/Word letters substitute Arial** per the standard. All header text prints **JHM Blue (PMS 288 / `#002D72`)**.
- **Body:** starts ~2.2" from top; Arial or Times 11–12 pt, standard business-letter structure. Sign-off block: name, degrees, academic title, division, department, institution, contact line; leave several blank lines between "Sincerely," and the printed name for a handwritten signature.
- **Rules from the standard:** letterhead is for people employed by or officially connected to Johns Hopkins, for official activities only; **no other institution's logos or co-branding**; second sheets are blank. The generic (non-personalized) `Letterhead_JHM_JHH.dot` template remains available for department-level letters.
- No PHI in letters drafted with this skill. **Style: write like a person, not a template — no em-dashes in letters** (use commas, colons, or separate sentences), vary sentence length, and avoid formulaic constructions; if a "humanizer"-type writing skill is available, apply it to letter prose.

## Step 5 — Smart enrichment (before delivering any draft)

Before handing over the rough draft, actively look for ways to make it a better starting point. Match the enrichment to the deliverable — research it when it helps, skip it when it doesn't:

**When the user provides an abstract (or author list) for a poster or talk:**

1. **Look the authors up** on PubMed and the web (institutional faculty pages). Use what you find to fill in **degrees and affiliations** for each author, formatted per the house style. Mark anything inferred rather than user-confirmed with a `[verify]` tag so the presenter can check it.
2. **Choose the attribution line at the right level — department is the default:** "Department of Surgery, The Johns Hopkins Hospital, Baltimore, MD" unless all or most authors are **confirmed** members of one division, in which case attribute to that division — "Division of Vascular Surgery and Endovascular Therapy, Department of Surgery, The Johns Hopkins Hospital" (or "Division of Colorectal Surgery…", etc.). Mixed divisions or any uncertainty → the general department subtitle; mixed institutions → list each affiliation with superscript numbering.
3. **Multi-institution teams:** if authors come from other medical centers, add their hospital logos to the poster header alongside ours — search for the official logo; if a usable official file can't be obtained, place a labeled placeholder box ("[University X Medical Center logo]") positioned correctly.
4. **Conference known?** Add the conference/society logo (top-left per the layout) the same way — official file if findable, labeled placeholder if not — and look up the meeting's poster specs (Step 4C).

**When the user hands over finished text (e.g., a letter to put on letterhead):**

- Don't do author lookups — just format it. But **offer a grammar/spelling audit**: if accepted, return the letter on letterhead in final form **plus redline edits** (tracked-changes-style markup or a brief change list) so they can see and veto every change. Never silently alter their wording.

**General rule:** enrichments are additive, clearly marked, and never delay the draft more than a quick round of searches. If a lookup is ambiguous (two surgeons with the same name), ask rather than guess.

## Step 6 — Output

- **Produce a real file** (.pptx for decks, correctly sized .pptx for posters, .docx for letters) — a full draft with every structural slide present and `[bracketed placeholders]` wherever the user's content is thin. Never deliver only an outline unless asked.
- **Embed the actual logo** in every generated file, following the logo rules above: plain JHM mark on the deck title slide only (`assets/H-JHM-2.png`; `-2R` on dark backgrounds), full hospital lockup on posters (`assets/` ships the official `H/V-JHH-…png` and `H/V-Bayview-…png`), user's choice elsewhere. Only if the packaged assets are genuinely unavailable (e.g., a colleague attached the standalone markdown alone), fall back to a clearly marked placeholder box labeled with the exact filename to drop in — never screenshot or redraw a logo. The same fallback applies to the campus photos: a labeled `[campus photo — JHH or Bayview]` box. For print posters, remind the user to swap the PNG for the EPS from the brand portal before sending to the printer.
- **Self-updating fields, not macros.** In every footer, insert PowerPoint's **native auto-date field** (`datetime` field — always displays the current date; this is the house default) and **native slide-number field** (`slidenum`) instead of literal text, so dates and page numbers fill themselves. If the presenter wants the talk date frozen instead, put the event date in as literal text. Never produce macro-enabled (.pptm) files or VBA — hospital IT commonly blocks them and they trigger security warnings; native fields do the job invisibly. (In python-pptx/raw XML: `<a:fld type="datetime1">` and `<a:fld type="slidenum">`; in pptxgenjs: the `slideNumber` option plus a datetime field post-process.)
- **Brand-true theme.** Set the deck's theme colors (accent 1 = Heritage Blue, accent 2 = gold, etc.) and theme fonts (Arial) so anything the presenter adds later — new text boxes, shapes, charts — defaults to brand styling instead of Office defaults.
- **Slide-1 speaker-notes handoff.** Put a short checklist in the title slide's speaker notes listing every `[bracketed]` placeholder in the deck, so the presenter can work through them without hunting.
- End with a 3-line handoff note: what to fill in, which logo file to place, and a reminder to add clinical details only on a hospital machine.

### QA checklist before delivering

☐ Logo rules followed (plain JHM on title slide only — grey variant may omit it per Step 3; no logo on content slides; full hospital lockup on posters) ☐ findings-first title ☐ footer bar on every slide (date · event · #) ☐ no PHI anywhere ☐ backup slides after Thanks ☐ poster: dimensions match conference spec, IRB + contact in footer ☐ degrees on external materials ☐ red used only for critical emphasis ☐ looked-up affiliations/degrees marked `[verify]` ☐ attribution line at division level only when authors are *confirmed* to share a division.

---

## Appendix A — Brand asset library

Full catalog with direct download links: `references/brand-assets.md`. Portal collections: [JHM logos (plain — deck title-slide default)](https://assets.jh.edu/web/434faef750ce7994/logo-johns-hopkins-medicine/) · [JHH logos](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid) · [JHH Office templates](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid) (download templates individually — the bulk download corrupts the .potx files). Bayview logos: same variant scheme, `Bayview` in filenames (search "Bayview" on [assets.jh.edu](https://assets.jh.edu)). Approved photography and medical illustrations: `references/image-library.md`. Downloads prompt for a brief reason.

## Appendix B — CME language (reference only — NEVER insert into a deck)

Grand rounds CME accreditation language (ACCME statement, credit designation, disclosure policy, off-label notice, MOC/ABS statements) and the M&M confidentiality statement are **handled separately in a different PowerPoint** maintained by the department — they do not go into presenter decks. The verbatim language is kept in `references/cme-language.md` purely so it can be recognized — its headings are: ACCREDITATION STATEMENT, CREDIT DESIGNATION STATEMENT, POLICY ON PRESENTER AND PROVIDER DISCLOSURE, NOTICE ABOUT OFF-LABEL USE PRESENTATIONS, MOC STATEMENT, AMERICAN BOARD OF SURGERY. If a user asks to add it, explain the department handles it separately. **The presenter's own financial-disclosure slide (Blueprint G) is a different thing and IS appropriate in decks.**
