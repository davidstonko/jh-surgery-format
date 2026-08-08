# JH Surgery Format — attach this file to Claude and describe your presentation

*Johns Hopkins Department of Surgery presentation formatting skill. Maintained by David P. Stonko, MD, MS. v2.2 — August 2026. Installed-skill command: `/jhsurgeryformat`.*

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

`<entity>` = `JHH` or `Bayview`. H (horizontal) for everything except stationery/narrow spaces; V (vertical) for stationery. Never recolor, stretch, add effects to, or re-draw a logo. The packaged `assets/H-JHM-*.png` and `assets/V-JHM-*.png` files are the official plain JHM logos. Download links: see the FULL BRAND ASSET LIBRARY section below.

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
- **Imagery/flair:** prefer approved Hopkins sources (see the APPROVED IMAGE LIBRARY section below): Blausen medical illustrations for anatomy/mechanism slides, ACCM clinical photography for context, Dome/Billings images for heritage flair. Never patient-identifiable photos; keep any credit lines intact.
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

Portal collections: [JHM logos (plain — deck title-slide default)](https://assets.jh.edu/web/434faef750ce7994/logo-johns-hopkins-medicine/) · [JHH logos](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid) · [JHH Office templates](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid) (download templates individually — the bulk download corrupts the .potx files). Bayview logos: same variant scheme, `Bayview` in filenames (search "Bayview" on [assets.jh.edu](https://assets.jh.edu)). Approved photography and medical illustrations: see the APPROVED IMAGE LIBRARY section below. Downloads prompt for a brief reason.

## Appendix B — CME language (reference only — NEVER insert into a deck)

Grand rounds CME accreditation language (ACCME statement, credit designation, disclosure policy, off-label notice, MOC/ABS statements) and the M&M confidentiality statement are **handled separately in a different PowerPoint** maintained by the department — they do not go into presenter decks. Recognize the language by its headings: ACCREDITATION STATEMENT, CREDIT DESIGNATION STATEMENT, POLICY ON PRESENTER AND PROVIDER DISCLOSURE, NOTICE ABOUT OFF-LABEL USE PRESENTATIONS, MOC STATEMENT, AMERICAN BOARD OF SURGERY. If a user asks to add it, explain the department handles it separately. **The presenter's own financial-disclosure slide (Blueprint G) is a different thing and IS appropriate in decks.**


---

# APPROVED IMAGE LIBRARY (inlined)

# Approved image library — Johns Hopkins Brand Portal

*Hopkins-approved imagery for presentations. Compiled 2026-08-08 from the Brand Portal (assets.jh.edu) with Dr. Stonko's account. Public share links work without login; downloads prompt for a brief reason.*

## Bundled hero photos (in `assets/photos/`)

These three are the approved go-to images, shipped with the installed skill package — users of this standalone file: use the labeled `[campus photo — JHH or Bayview]` placeholder per Step 6 instead:

| File | Subject | Use |
|---|---|---|
| `JHH-1800-Orleans-exterior.jpg` | The Johns Hopkins Hospital — 1800 Orleans St. entrance (Zayed/Bloomberg towers) | **Thank-you slide** for JHH work; title-slide flair |
| `JHBMC-Bayview-campus.jpg` | Johns Hopkins Bayview Medical Center aerial | **Thank-you slide** for Bayview work; title-slide flair |
| `illustration-AAA-blausen.jpg` | Blausen medical illustration: abdominal aortic aneurysm anatomy | Background/anatomy slides (vascular) |

**Thank-you slide rule:** the closing "Thanks! / Questions?" slide should carry the campus photo of the hospital where the work was done (JHH or Bayview), full-bleed or as a large right-side panel, with the thank-you text on a Heritage Blue overlay or clear sky area.

## Brand Portal collections (public share links)

| Collection | Assets | What's inside / when to use |
|---|---|---|
| [Blausen Illustration](https://assets.jh.edu/web/e9d307ec068ad8db/blausen-illustration/) | 242 | Licensed medical illustrations (anatomy, pathology, devices) — first stop for anatomy/mechanism slides |
| [ACCM Core Historical & Clinical Scenes](https://assets.jh.edu/web/a3e81573f73e4ef4/accm-core-historical---clinical-scenes/) | 92 | OR and clinical photography, historical Hopkins scenes — talk openers, clinical-context slides |
| [ACCM Education, Culture & Departmental Life](https://assets.jh.edu/web/dd7df4de256f9768/accm-education--culture---departmental-life-/) | — | Teaching, rounds, departmental life photography |
| [Dome/Billings Images](https://assets.jh.edu/web/8d909179015cb5c0/dome-billings-images/) | 12 | The historic Billings dome — title slides, grand rounds, heritage flair |
| [East Baltimore Drone Footage](https://assets.jh.edu/web/9d350dfd9c5108fa/east-baltimore-drone-footage/) | 2 | Campus aerials (video) |
| [Virtual Backgrounds](https://assets.jh.edu/web/9039e0c0edf296f2/virtual-backgrounds/) | 123 | Branded backgrounds — also useful as slide backdrops |
| [Neuro Work by Lydia Gregg](https://assets.jh.edu/web/90f0e0394283753d/neuro-work-by-lydia-gregg/) | 18 | Neurovascular/neurosurgical illustration |
| [Portraits](https://assets.jh.edu/web/69ecff05f3133883/portraits/) | — | Official faculty headshots — bio slides |
| [Logo—Johns Hopkins Medicine](https://assets.jh.edu/web/434faef750ce7994/logo-johns-hopkins-medicine/) | 27 | The plain JHM logo files (the deck title-slide default) |
| [Walters Collection](https://assets.jh.edu/web/abad49868578e048/walters-collection/) | 1 | Historic art |
| Art as Applied to Medicine Contemporary Collection | 801 | Major medical-art archive — **not published publicly**; browse logged-in at assets.jh.edu (Collections → "Art as Applied to Medicine") |

## Usage rules

- Prefer these approved sources over web images — they are cleared for Hopkins use.
- Match imagery to the hospital (JHH vs. Bayview) and to the clinical topic; illustrations (Blausen, AAM, Gregg) beat clip-art every time.
- Credit lines: Blausen and Art-as-Applied-to-Medicine images may carry attribution requirements — keep any watermark/credit intact.
- Never use patient-identifiable photographs.


---

# FULL BRAND ASSET LIBRARY (inlined)

# Johns Hopkins Hospital & Bayview — Brand Asset Library

*Reference file for the **JH Surgery Format** skill (Department of Surgery, The Johns Hopkins Hospital & Johns Hopkins Bayview Medical Center).*
*Compiled 2026-08-08 from the Johns Hopkins Brand Portal ([assets.jh.edu](https://assets.jh.edu)) and the official "Using the logo files" guide (JHD1910102, 11/2019).*

## Choosing the hospital logo (JHH vs. Bayview)

The Department of Surgery spans two campuses. **Which hospital's logo appears on a presentation depends on where the work was done:**

- Work done at **The Johns Hopkins Hospital** → use the **JHH** logo lockup.
- Work done at **Johns Hopkins Bayview Medical Center** → use the **Bayview** logo lockup.
- Authors with affiliations at **both**, or a multi-site project → **ask the user which hospital should be the focus** (or whether both logos should appear).

Both logo families use the identical variant scheme, so every selection rule below applies to both.

## Official usage rules (from the JHM "Using the logo files" guide)

**Logo colors:** four colors used in combination — **PMS 288 Blue** (Heritage Blue, ≈ `#002D72`), **PMS 7406 Gold** (≈ `#F1C400`), Black, White.

**Alignment:**

- **H (horizontal)** — "use in all situations except stationery or where space is limited."
- **V (vertical/stacked)** — "use in stationery."

**Color codes in filenames:**

- **2** = two colors: blue-and-gold triangle, blue words.
- **2R** = as above but words reversed to white — "best for use on dark backgrounds."
- **BW** = black-and-white triangle, black words.
- **1** = one color (Enterprise logo only).

**File types (official guidance):**

- **EPS** — "primarily for use by graphic design professionals and printers… also known as vector files." → **use for printed posters.**
- **PNG** — "background is transparent, making it ideal where a background color needs to be visible, such as in a PowerPoint presentation." → **use for slides.**
- **JPG** — "best for MS Word and the internet; background is not transparent." → white-background documents only.

**Entity names in filenames** (relevant subset): `JHH` = The Johns Hopkins Hospital · `Bayview` = Johns Hopkins Bayview Medical Center · `JHM` = Johns Hopkins Medicine · `SOM` = Johns Hopkins School of Medicine.

**Do not** recolor, stretch, add effects to, or re-draw any logo. Use only official files.

### Quick selection matrix

| Output | File to use |
|---|---|
| Printed conference poster | `H-<entity>-2.eps` (or 500-DPI PNG if EPS unsupported) |
| Slide deck, light background | `H-<entity>-2.png` |
| Slide deck, dark/Heritage Blue background | `H-<entity>-2R.png` |
| Word doc / white background | `H-<entity>-2.jpg` (or the transparent PNG, which renders fine on white) |
| One-color or B&W reproduction | `-BW` variant |
| Stationery / narrow vertical space | `V-` variants of the above |

---

## Collection 1 — Logos: The Johns Hopkins Hospital (JHH)

**Collection page:** <https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid>
17 assets · lockup: dome mark + "JOHNS HOPKINS MEDICINE / THE JOHNS HOPKINS HOSPITAL"
*Local copies of all 16 logo files + usage guide PDF were obtained via `All JHH logos.zip` (2026-08-08).*

### Vertical (stacked)

| File | Format | Dimensions / DPI | Direct link |
|---|---|---|---|
| V-JHH-2.eps | EPS vector, full color | vector | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=45D8173C-7514-4676-8B49AEE2A5203526) |
| V-JHH-2.png | PNG, transparent | 2355 × 1913 px, 500 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=3956554A-FB96-4D9D-834A842BB78AAE7C) |
| V-JHH-2.jpg | JPG, white bg | 1954 × 1620 px, 400 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=44657ED6-6E37-4474-A4E051C95099674E) |
| V-JHH-2R.eps | EPS vector, reversed | vector | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=B4DE01B8-A45E-4A47-9D35B0795475283C) |
| V-JHH-2R.png | PNG, reversed, transparent | 2355 × 1913 px, 500 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=5100A305-96EA-4EDB-8F6F31FFD2C6ECAD) |
| V-JHH-BW.eps | EPS vector, B&W | vector | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=4B681D63-C2E8-4B73-B76E7001C27AA3CF) |
| V-JHH-BW.png | PNG, B&W, transparent | 2355 × 1913 px, 500 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=1ECD7527-C3D2-4A30-BE90DD0BB0DEC474) |
| V-JHH-BW.jpg | JPG, B&W, white bg | 1954 × 1620 px, 400 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=2C09DC62-657C-4574-BED8E6B74A395A7C) |

### Horizontal

| File | Format | Dimensions / DPI | Direct link |
|---|---|---|---|
| H-JHH-2.eps | EPS vector, full color | vector | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=06367E53-2204-4CE1-8962FA7658529C97) |
| H-JHH-2.png | PNG, transparent | 3062 × 901 px, 500 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=3D5C4773-2EA0-4563-BED710BAF2CB1213) |
| H-JHH-2.jpg | JPG, white bg | 2512 × 853 px, 400 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=D4910E69-5BA1-4D2D-A764A33B35D01454) |
| H-JHH-2R.eps | EPS vector, reversed | vector | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=B9EED477-D9BA-4E04-8D79E25B16A9A6F5) |
| H-JHH-2R.png | PNG, reversed, transparent | 3062 × 901 px, 500 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=27CA5DC3-538C-44BE-A7D40ECEAA0826A8) |
| H-JHH-BW.eps | EPS vector, B&W | vector | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=CF60D032-B07C-4273-A98086D459EC8365) |
| H-JHH-BW.png | PNG, B&W, transparent | 3062 × 901 px, 500 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=224D7971-FCD7-496F-AD1702FCAFF4AA8A) |
| H-JHH-BW.jpg | JPG, B&W, white bg | 2512 × 853 px, 400 DPI | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=6D6B2A07-1BEC-4C86-A0DA689358A97D38) |

### Complete package

| File | Format | Size | Direct link |
|---|---|---|---|
| All JHH logos.zip | ZIP | 5.63 MB | [Open](https://assets.jh.edu/web/8bd08c173d1a2b3e/logo-the-johns-hopkins-hospital/?viewType=grid&mediaId=7FB5E2EC-6B69-433F-928422F90B6CE71B) |

---

## Collection 2 — Logos: Johns Hopkins Bayview Medical Center (JHBMC)

*Obtained from `AllJHBMC logos.zip` (provided 2026-08-08). Same variant scheme as JHH; lockup reads "JOHNS HOPKINS MEDICINE / JOHNS HOPKINS BAYVIEW MEDICAL CENTER". Portal collection: search "Bayview" under Locations on [assets.jh.edu](https://assets.jh.edu).*

**Files in the package** (each in `horizontal/` and `vertical/` folders):

- `H-Bayview-2.eps`, `H-Bayview-2.jpg`, `H-Bayview-2.png`, `H-Bayview-2R.eps`, `H-Bayview-2R.png`, `H-Bayview-BW.eps`, `H-Bayview-BW.jpg`, `H-Bayview-BW.png`
- `V-Bayview-2.eps`, `V-Bayview-2.jpg`, `V-Bayview-2.png`, `V-Bayview-2R.eps`, `V-Bayview-2R.png`, `V-Bayview-BW.eps`, `V-Bayview-BW.jpg`, `V-Bayview-BW.png`
- `Using the logo files.pdf` (official usage guide)

All the selection rules in the matrix above apply — substitute `Bayview` for `JHH` in the filename.

---

## Collection 2b — Logos: Johns Hopkins Medicine (plain JHM — no hospital line)

*Obtained from `All JHM logos.zip` (provided 2026-08-08). **This is the default logo for deck title slides.** Same variant scheme: `H/V-JHM-{2,2R,BW}` in EPS/JPG/PNG. Portal: "Logo—Johns Hopkins Medicine" collection on [assets.jh.edu](https://assets.jh.edu).*

## Collection 3 — Templates: The Johns Hopkins Hospital

**Collection page:** <https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid>

> ⚠️ **Note:** the portal's *bulk* "Download ()" of this collection produced corrupted/truncated .potx files (the zip even shipped with a "Corrupted files" notice). **Download each template individually** from its detail page instead.

### PowerPoint templates (.potx) — design descriptions (from rendered inspection)

| File | Title-slide design | Direct link |
|---|---|---|
| JHM_JHH_White.potx | White upper half with full-color vertical JHH logo, Heritage Blue lower band, thin gold accent bar at top, blue footer bar with "Presented by / date / slide #" | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=7EF9B154-8AD2-4D1C-92D8BB40E2B7C615) |
| JHM_JHH_Blue.potx | Full Heritage Blue background, reversed (white) JHH logo, gold horizontal band carrying presenter name/date, gold edge accents | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=31D0365C-070C-4F98-B3BB4CD31B928195) |
| JHM_JHH_Blue_v2.potx | Variant of Blue: two-tone blue panels, reversed logo top-right, gold presenter band lower third | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=D03E64BD-1FF1-4D52-BD4BC49215511CF1) |
| JHM_JHH_Tower.potx | Full-bleed blue-duotone photo of the historic Billings dome, gold frame border, reversed JHM logo lower-right, gold footer band | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=4BA25A22-31EE-4BDD-8BA2E7BDB99BD170) |
| JHH_ZB_Towers.potx | Full-bleed blue-duotone photo of the Zayed Building towers, gold frame; content layout uses a light background with faded Zayed photo, blue title rule, footer with date/slide #/logo | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=47899D0D-2F46-4F77-8DDC0975C926B7E3) |

### Word templates (.dot) — intact in bulk download

| File | Purpose | Size | Direct link |
|---|---|---|---|
| Letterhead_JHM_JHH.dot | Official JHH letterhead (by BrandSavvy, Inc., 2008) | 38.40 kB | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=74F9EE42-65E9-47FB-85754E4580849BA4) |
| Report_BW-JHM_JHH.dot | Report template, B&W | 429.57 kB | [Open](https://assets.jh.edu/web/9348931fb6c0192c/template-johns-hopkins-hospital/?viewType=grid&mediaId=96B053E0-217C-4B45-B9C12C30BAB6A68C) |

### Extracted design specifications (from the .potx internals)

These are historical measurements of the official 4:3 .potx masters, kept for context. **Where anything here differs from the skill's design system (Step 3 above), Step 3 wins** — including type scale and logo selection:

- **Slide size:** all five official templates are **4:3 (10" × 7.5")**. *(Modern conference projectors are typically 16:9 — the skill should ask the user, defaulting to 16:9 while carrying over the color/typography system.)*
- **Typeface:** **Arial** for both headings and body (major + minor font).
- **Primary blue used in template text/accents:** `#254B8E`; the brand's Heritage Blue is **PMS 288 ≈ `#002D72`**; gold accent **PMS 7406 ≈ `#F1C400`**.
- **Type scale (from slide master):** title 36 pt; body levels 32 / 28 / 24 / 20 pt; footer text 18 pt.
- **Title placeholder:** 0.89" from left, 0.43" from top, 8.5" wide × 1.25" tall. **Body placeholder:** 0.89" left, 2.17" top, 8.5" × 4.5".
- **Footer row** (~6.92" from top): date (left), footer text (center), slide number (right).
- **Recurring motifs:** gold accent bar along slide edge; Heritage Blue field or blue-duotone campus photography on title slides; reversed logo on dark grounds; "Presented by:" name + date band on the title slide.

---

## Official letterhead standards (brand.hopkinsmedicine.org, Design Standards → Letterhead, updated 3/2023)

- **General letterhead:** address block at 1" from left, 1/2" from top, 5" wide; brandmark 1-5/8" top-right; entity name in bold as the first address line; second sheets blank; no affiliate or other-institution logos or co-branding ever.
- **Personalized letterhead:** personalization block (1" from left, 1-3/4" wide: name+degrees bold, titles italic, up to 3 names) → address block (3-1/4" wide: dept bold, address, T/F phone lines, @jhmi.edu email) → brandmark 1-5/8" top-right. 8.5"×11"; logo prints PMS 288 + PMS 7406; all header text JHM Blue; typography Gill Sans 8 pt / 10 pt leading (bold names, italic titles) — **Word/electronic versions substitute Arial**. Format applies to all approved brandmarks.
- Pages: [General](https://brand.hopkinsmedicine.org/brand/design-standards/letterhead/general-letterhead) · [Personalized](https://brand.hopkinsmedicine.org/brand/design-standards/letterhead/personalized-letterhead)

## Notes for the JH Surgery Format skill

- **Hospital selection first:** determine JHH vs. Bayview (or both) from the project site/author affiliations; ask if ambiguous.
- **Asset selection is medium-driven:** EPS (or 500-DPI PNG) for print posters; transparent PNG for slides, matched to background (standard on light, `-2R` on dark); JPG only on white documents.
- **Generated decks should mirror the sanctioned templates' colors, typography, and motifs** (Heritage Blue + gold system, Arial) even when building 16:9 decks from scratch — but logo selection follows Step 3 above: plain JHM on deck title slides, hospital lockups on posters.
- **PHI rule:** no patient identifiers or protected data ever; generated drafts use placeholder case details only.
- **Portal downloads** prompt for a brief "reason for download"; colleagues download assets themselves via the links here.

*Deep-link format: `<collection URL>&mediaId=<ID>`.*
