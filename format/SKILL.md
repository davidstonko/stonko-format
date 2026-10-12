---
name: format
description: "Format a Word manuscript (.docx) to David P. Stonko's standard journal-submission template and house style. Times New Roman 11 pt throughout, double-spaced body with single-spaced title, 1-inch margins on US Letter, bold 11 pt section headings (no larger fonts anywhere), and a title page carrying the standard author, affiliation, correspondence, funding, email and keywords block. Also holds his house rules for statistics (P values, confidence intervals), tables, figures, references, Conclusions and Journal of Vascular Surgery conventions. Trigger when the user says '/format', 'format this manuscript', 'apply my template', 'format for submission', asks to add a title page in their house style, or asks for a paper, table or figure in his house style."
---

# /format: manuscript formatting to the Stonko house template

Apply this when the user wants a manuscript put into their standard submission format,
or invokes `/format`. It restyles an existing `.docx` and prepends a title page. The writing,
statistics, table and figure rules below also apply whenever a manuscript is drafted or revised.

## Formatting specification
- Page: US Letter, 8.5 x 11 in, 1-inch margins on all sides.
- Font: Times New Roman, 11 pt, for ALL text (title, headings, body, captions, tables, references). No font is ever larger than 11 pt.
- Line spacing: double (2.0) for all manuscript text (Introduction, Methods, Results, Discussion, figure legends). The title page and the Abstract are single-spaced (front matter). **The title is always single spaced.**
- No extra space between paragraphs: 0 pt before and after every body paragraph and heading. Never use blank paragraphs as spacers in the body.
- Body paragraphs: left-aligned, first line indented 0.5 in for every new paragraph. Figure legends are double spaced without the indent.
- Section headings (Abstract, Introduction, Methods, Results, Discussion, Conclusions, References, and subsection titles): Times New Roman, 11 pt, bold, black, not italic. Same size as body text.
- Pages: title page, then the Abstract on its own page, then Article Highlights and Table of Contents Summary (when the journal wants them) on their own page, then a page break before the Introduction.
- Tables: single spaced, as are their captions and footnotes; one table per page after the References; wide tables go in their own landscape section, which must stay landscape after formatting. Set explicit column widths (`w:gridCol` plus fixed table layout) because LibreOffice ignores autofit; section label rows are merged across the full table width.
- Equations and embedded figures are left untouched.
- **Revising an existing paper:** edit the content only. Do not change the build template or layout logic unless asked.

## Writing style (applies to text, tables, figures and legends)
- No em dashes anywhere. Use commas, parentheses or a new sentence. En dash only for numeric ranges.
- Nothing that reads as AI-generated. Concise, dense prose; light-touch edits that keep David's voice. Avoid filler and words he has rejected ("narrows" for a gap or difference).
- **Conclusions:** every claim in the Conclusions (Abstract and main text) must be supported by a result that is reported with a P value. Check each sentence of the Conclusions against the Results; a claim with no tested result behind it is cut or flagged, never softened and left in.
- Never invent a number. A value that is not yet available is written as a yellow-highlighted `[placeholder]` so it cannot be missed before submission.
- Capitalize figure labels, axis text and table headers in title case ("Year Before ABI", "BMT Status"); audit this across every figure and table when one changes.

## Statistics presentation (Hicks/Holscher house style)
- **P values:** write `P=0.03`, `P=0.003`, `P<0.001`, `P<0.05`. Capital P, no spaces around `=` or `<`, leading zero, two decimals (three when P<0.01), never `P=0.000`. Same form after a qualifier (`adjusted P=0.008`, `P for interaction=0.02`).
- **In text**, effect, CI and P go in one parenthetical, separated by semicolons: `(aOR, 0.57; 95% CI, 0.39–0.83; P=0.003)`. Never "95% CI a, b" or "[a, b]".
- **CI ranges:** en dash (`0.39–0.83`); write "to" when either bound is negative (`−4.1 to 2.3`), using a true minus sign.
- **In tables:** `0.57 (0.39–0.83)` with a separate P column (`0.03`, `<0.001`); reference levels shown as `Ref`.
- **Medians:** `65 (58–74)`, labelled median (IQR) in the row or column header. Counts: `457 (26.2)` with n (%) in the header, thousands separators on counts (`1,045`).
- Percentage-point differences are written out in the Abstract, highlights, figures and legends ("15.8 vs 32.4 percentage points"); in the body, `pp` may be used after it is defined at first use in the Methods.
- The Methods state the significance threshold as `P<0.05`, and post hoc or unadjusted tests are named as such where the result is reported.
- **Small cells:** when the data source sets a minimum cell size (e.g., <11 for REACH/JHU enclaves), suppress the count and anything that lets it be recovered by subtraction, merge categories or report as "<11", and footnote the suppression. This covers text, tables, figures (including number-at-risk rows) and supplements.

## Manuscript structure
- Order: title page, Abstract, Article Highlights and Table of Contents Summary (JVS), Introduction, Methods, Results, Discussion, References, tables, figure legends, supplemental material.
- Abstract is structured with the labels Objective, Methods, Results, Conclusions.
- Primary analysis first in Methods and Results; secondary and sensitivity analyses follow, labelled as such. Post hoc analyses are called post hoc.
- Methods order and subheadings: Study Design and Data Source, Study Cohort, Study Outcomes, Study Covariates, Statistical Analysis (ending with software and the significance threshold). Ethics/IRB and the reporting guideline (STROBE, RECORD) sit in the first subsection.
- Results open with Patient Cohort, then one topic subheading per analysis in the order the Methods introduced them.
- Figure 1 is an EQUATOR-aligned (STROBE/RECORD) cohort flow diagram with exclusion reasons in side boxes and attrition tracked at each step, ending at the cohort for the primary outcome.
- Supplemental tables and figures numbered S1, S2 … in the order first cited.

## Figures
- Arial (or a metric-compatible font) at 9 pt; top and right spines off; axis labels and tick labels in title case.
- No title inside a main figure when the legend says the same thing. Multi-panel figures carry bold panel labels ("A. Basis of the Diagnosis"). Put the sample size in the axis label or legend.
- A 95% CI on every estimate. Statistics printed inside a figure use the same house style as the text (`P<0.001`, `95% CI, 11.3–20.4`).
- Group of interest first and in a consistent color across figures (vermillion for the group of interest, gray for the comparison group). Green, yellow and red are reserved for ordinal good, partial, none.
- Kaplan-Meier figures carry confidence bands and a number-at-risk row aligned to the x ticks.
- Export each figure as PNG at 600 dpi plus vector PDF and SVG with editable text.

## Journal of Vascular Surgery conventions
- Citations are superscript numerals placed **after** punctuation (`…disease.³` / `…therapy,⁴⁻⁶`).
- References: up to 6 authors then `et al`; `Journal Year;Volume:Pages.` with **no issue number** and abbreviated page ranges (`786-94`, `e1-e8`, `786-94.e2`).
- After the Abstract, add **Article Highlights** with three labelled items (Type of Research, Key Findings, Take Home Message) and a **Table of Contents Summary** (2 to 3 sentences). Check current word limits in the JVS author guide before submission.
- Datasets are cited as references. **JHU REACH:** cite `Chute CG, et al. JHU REACH (Version JHU.DS) [dataset]. doi:10.26144/DCMA-HA86` when first describing the data source in Methods ("the Johns Hopkins Research Enclave for Analyzing Clinical Health Data (REACH)"). No separate grant acknowledgment is listed by REACH.

## Common coauthors: verified roster

Degrees and affiliations below were read from typeset publisher bylines (PMC preserves the printed
byline verbatim in its JATS `<degrees>` field) and corroborated across at least two independent
journals per person, August 2026. Use these directly; no lookup needed.

| Author, as printed | Affil |
|---|---|
| David P. Stonko, MD, MS | 1 |
| Courtenay M. Holscher, MD, PhD | 4 |
| Ying Wei Lum, MD, MPH | 1 |
| James H. Black III, MD | 1 |
| Chen Dun, PhD, MHS | 2,3 |
| Christopher J. Abularrage, MD | 1 |
| Caitlin W. Hicks, MD, MS | 1 |

1. Division of Vascular Surgery and Endovascular Therapy, Department of Surgery, Johns Hopkins University School of Medicine, Baltimore, MD, USA
2. Department of Biomedical Informatics and Data Science, Johns Hopkins University School of Medicine, Baltimore, MD, USA
3. Department of Surgery, Johns Hopkins University School of Medicine, Baltimore, MD, USA
4. Department of Surgery, Johns Hopkins Bayview Medical Center, Johns Hopkins University School of Medicine, Baltimore, MD, USA

Affiliations are renumbered 1, 2, 3 … in order of first appearance on each title page.

Notes on this roster:
- **Ask the user for the author ORDER every time.** It is never inferable, and it is the one thing on a
  title page that carries academic weight.
- **Courtenay Holscher** is at Johns Hopkins Bayview (affiliation 4), verbatim from PMID 40645573 (Ann Vasc Surg 2026) and 38914374 (JVS-VL 2024). Usual senior author on the PAD/REACH work.
- **Chen Dun** printed *MHS* alone through early 2025 and *PhD, MHS* from mid-2025; one 2025 *Surgery*
  paper typeset *MS*, which is contradicted by every other byline. She does not carry the vascular
  division affiliation.
- **Ying Wei Lum's** bylines vary: JVS journals print *MD, MPH*; JAMA journals print *MD* only, which is
  house style suppressing the second degree, not evidence against it. Some papers add *FACS*, a
  fellowship rather than a degree; include it only if including it for everyone.
- The group's papers also use "The Johns Hopkins Hospital" in place of "Johns Hopkins University School
  of Medicine" in affiliation 1. Both appear in print; the School of Medicine form is more common on
  their recent *Journal of Vascular Surgery* papers and is the default here.
- Recheck a degree if a paper is being submitted more than a year from now; people finish degrees.

## Coauthors not on the roster: verify, never infer

**Never write a degree or an affiliation you have not read in print.** A plausible degree is not a
verified one, and a wrong one on a title page is visible to every coauthor. Degrees do not follow from
role or seniority: a surgeon-scientist may be MD, MD MS, MD PhD or MD MPH, and a research scientist may
be PhD, MHS, ScD, or a pair.

1. **Affiliation.** Find the person's most recent indexed papers on PubMed
   (`https://pubmed.ncbi.nlm.nih.gov/?term=Lastname+II%5BAuthor%5D&sort=date`) and read the affiliation
   field verbatim. Note the PMID. If recent papers disagree, use the form that appears most often on
   the group's own recent papers, and say that you chose.

2. **Degrees.** PubMed's author field strips post-nominals, so go to the publisher's article page (the
   DOI) or the PMC record and read the byline **as typeset**. PMC's JATS `<degrees>` field is the most
   reliable source. Journals that reliably print degrees: *Journal of Vascular Surgery*, *Annals of
   Vascular Surgery*, *JAMA Surgery*, *J Am Heart Assoc*, *Circ Cardiovasc Qual Outcomes*. Corroborate
   across at least two independent journals.

3. **Traps.** House style can suppress degrees (a single MD-only byline disproves nothing). Degrees
   change when someone finishes a doctorate, so prefer recent bylines. A lone disagreeing byline is
   usually a typesetting error. FACS and FAHA are fellowships, not degrees. A second affiliation is
   only real if it is consistent; one appearing on 3 of 80 recent papers is not a standing
   affiliation.

4. **Report per person**: degrees as printed, affiliation verbatim, source PMID and URL, and one of
   *verified in print* / *inferred* / *not verified*. **If you cannot find a degree in print, say "not
   verified" and ask.** That is the correct answer and far more useful than a plausible guess.

## Title page (prepend, then a page break before the Abstract/body)
Build these lines, each Times New Roman 11 pt, single spaced. Ask the user for any field marked {…} that is not already known.

1. `Prepared for: ` + bold-italic `***working paper***` + a right-aligned tab + `{Mon. YYYY}` (e.g., "Jul. 2026").
2. (blank line)
3. **Title** (bold, single-spaced): `{Full title}`
4. `Short Running Title:`
5. `{Short running title}`
6. (blank)
7. Authors in the order the user gave, separated by `; `, each with superscript affiliation numbers
   and degrees separated by commas (`David P. Stonko, MD, MS`). Single-author default:
   `David P. Stonko, MD, MS` with superscript `1`.
8. (blank)
9. Numbered affiliation lines, one per line, numbered in order of first appearance.
10. (blank x2)
11. **Correspondence and reprint requests:** (bold label)
12. `David P Stonko`
13. `600 N Wolfe St`
14. `Halsted 668`
15. `Baltimore, MD 21287`
16. (blank)
17. **Source of Funding:** (bold label) ` no funding was utilized.`
18. (blank)
19. **Emails:** (bold label)
20. `David Stonko: dstonko1@jhmi.edu`
21. (blank)
22. **Keywords:** (bold label) ` {6-10 keywords, comma-separated}`
23. Page break (title page occupies its own page).

The Abstract then occupies its own page, followed by a page break so the body starts on a fresh page. Structure: title page -> page break -> Abstract -> page break -> (Article Highlights and Table of Contents Summary -> page break ->) body.

## How to apply
Preferred: run the helper. It restyles fonts, spacing, indents, margins, headings, references and tables, keeps landscape table sections landscape, inserts the title page, and never changes the text.

```bash
python scripts/apply_format.py <target.docx> \
  --title "Full title" \
  --short-title "Short running title" \
  --keywords "kw1, kw2, kw3" \
  --date "Jul. 2026" \
  --authors "David P. Stonko, MD, MS^1; Courtenay M. Holscher, MD, PhD^2" \
  --affil "Division of Vascular Surgery and Endovascular Therapy, Department of Surgery, Johns Hopkins University School of Medicine, Baltimore, MD, USA" \
  --affil "Department of Surgery, Johns Hopkins Bayview Medical Center, Johns Hopkins University School of Medicine, Baltimore, MD, USA" \
  --output <formatted.docx>
```

- `--authors` lists authors in order with affiliation numbers after `^`; `--affil` is repeated once per affiliation in order of first appearance. Omit both for the single-author default. `--funding` overrides the funding sentence. `--no-title-page` restyles a paper that already has its title page.
- The helper relies on Word heading styles (Heading 1 for Abstract, Introduction, Methods, Results, Discussion, References, Figure Legends; Heading 2 and below for subsections). Apply those first if the source uses bold text for headings.
- It ends with a style check that prints warnings for em dashes, P values and confidence intervals that are not in house style, and any font over 11 pt. It reports only; fix the text by hand or ask David.
- If the title, short title, keywords or author order are unknown, ask the user before running.
- Then render to PDF (`soffice --headless --convert-to pdf`) and look at the pages: title single spaced, Abstract on its own page, body double spaced with indents, tables single spaced, wide tables still landscape.
- The specification above is authoritative. If the installed helper is the older one (no `--authors` in `--help`), run it with the flags it has, then fix by hand what it misses: author line and affiliations, single-spaced title, black bold headings, 0.5 in body indent with 0 pt paragraph spacing, page break before the Introduction, single-spaced tables, 6 pt after each reference, and landscape table sections.

## References
- The References section starts at the top of its own page (page break before the References heading).
- Single-spaced, 6 pt after each reference.
- Numbered, in PubMed/NLM (Vancouver) style: `Author AA, Author BB, Author CC, et al. Title of article. Journal Abbrev. Year;Volume(Issue):Pages.` List up to the journal's author limit, then `et al.` For JVS, drop the issue number and abbreviate pages (see above).
- Do not include editorial notes at the top of the References section.
- **Verify every reference against its PubMed record**: author order and initials, full untruncated
  title, journal, year, volume, issue, pages, DOI, PMID. Use NCBI E-utilities (`efetch`/`esummary`,
  `db=pubmed`) rather than scraping PubMed HTML, which rate-limits.
- **Verify the author list, not just the title and PMID.** A citation assembled from a summary can
  carry authors from a neighbouring paper; this has happened.
- Papers published online ahead of print have no volume or pages. Write `Published online {Month D,
  YYYY}` rather than inventing them.
- A PMID that looks too recent for the publication date is usually a delayed NIH manuscript deposit,
  not an error. Check before assuming it is wrong.
- Watch for `Reprint of:` duplicate records (journals' "best of" issues). Cite the original.

## Author details (defaults; override only if the user says so)
- Corresponding author: David P. Stonko, MD, MS (superscript affiliation 1)
- Correspondence: David P Stonko, 600 N Wolfe St, Halsted 668, Baltimore, MD 21287
- Email: David Stonko: dstonko1@jhmi.edu
- Source of Funding: no funding was utilized.

A copy of the reference template is in `assets/manuscript_template.docx`.
