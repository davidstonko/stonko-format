---
name: "jvsformat"
description: "Take a manuscript already in /format house style to a complete Journal of Vascular Surgery submission package, with a draft visual abstract and a full consistency audit. Trigger on '/jvsformat' or 'prep this for JVS'."
---

# /jvsformat: JVS submission package

This builds on /format. Load /format first; its house style, statistics, figure and reference rules all
apply. This skill adds what JVS and its Editorial Manager (EM) site require, makes every piece of the
package, then checks every file against the final manuscript.

Sources to read before starting (David's copies first; anyone else uses the journal's live pages):
- The journal's current Guide for Authors at jvascsurg.org, and the Application for Publication form from the JVS Editorial Manager site.
- `reference/JVS_Information_for_Authors_Jul2016.md` (claude.ai Project "REACH database: Management of patients with PAD"). It dates from 2016, so check the live EM screens for anything newer.
- `reference/JVS_Application_for_Publication.md`, plus the blank form at `~/Projects/REACH_PAD/templates/JVS_Application_for_Publication_TEMPLATE.docx` on David's Mac.
- The most recent JVS package as a worked example: `~/Projects/REACH_PAD/JVS_submission_2026-11-03/JVS_submission/`.

Never invent a form layout, a contribution role, a conflict of interest, a credential or a number. If a
file or fact is not in reach, ask David for it.

## 0. Start: confirm the corresponding author and the pieces
Ask David once, up front, for anything not already known:
- Corresponding author (name, degrees, title, institution, address, email). Use the verified roster in /format for degrees and affiliations.
- The full author list in order, each with full name as it should print (middle initial included), degrees and affiliation. Run the /format "Author check before every submission" on it now; a placeholder, nickname or unverified degree is resolved with David before any file is built.
- Article type (Clinical Research unless told otherwise), the final title, and whether he is keeping a title that breaks a JVS rule.
- Who signs the Application for Publication, and each author's contribution roles and conflicts.
- Whether AI tools were used for the analysis code or figures (this changes the Methods; see section 2).

Then make every piece below, in this order.

## 1. Cover letter to the editor
- Write it on the corresponding author's institutional letterhead. Use the /jhsurgeryformat skill (github.com/davidstonko/jh-surgery-format) for the logo and letterhead (JHH or Bayview, chosen by the corresponding author's affiliation; Courtenay Holscher is Bayview).
- Addressed to the Editors of the Journal of Vascular Surgery. Dated the submission day. States the final title verbatim, the article type, the main finding with the same numbers as the Abstract, why it matters to JVS readers, that the work is original and not under consideration elsewhere, and that all authors approved it.
- Signed with the corresponding author's name and credentials as printed on the title page.
- Save as .docx and render to PDF to check the logo, margins and one-page length.

## 2. Conformance pass on the manuscript (tracked changes in David's name)
- **Limits for Clinical Research (live Guide for Authors, checked Nov 2026):** abstract 250 to 400 words, body 3,500 words, 50 references, **6 print figures and/or tables plus 4 online only, with supplemental tables counted in the table limit**; no author cap. The 2016 guide's 8 authors / 10 figures / 10 tables / 40 references is out of date. **Actually run the counts** (abstract; body = Introduction through Conclusions, headings and the AI declaration excluded) and print them in the reply with the limits beside them; never report a limit as met without the number. A Nov 2026 package went in at 4,935 body words and 8 print items because the count was listed as "to check" and never run. Move long methods to Supplemental Methods rather than cutting results, and ask David before cutting anything.
- **Title:** declarative, no colon, no abbreviations. If David keeps a title that breaks a rule, keep it and note it once.
- **Abstract:** structured (Objective, Methods, Results, Conclusions), no abbreviations, no references, real numbers.
- **Article Highlights** (Type of Research, Key Findings up to 300 characters, Take Home Message) and a **Table of Contents Summary** (up to 400 characters).
- **Clinical practice guidelines paragraph.** EM asks authors to confirm (True/False) a short paragraph in the Discussion or Introduction that places the study against the most recent relevant guidelines from any society. Make sure one exists and is cited (for PAD: the 2024 ACC/AHA/SVS multisociety guideline and the 2024 ESC guideline; for diabetic foot ulcers: the 2023 intersocietal IWGDF/ESVS/SVS guideline, Fitridge R, et al. J Vasc Surg 2023;78:1101-31, PMID 37724985). Note where it is so David can answer the checkbox.
- **AI disclosure (EM item "Use of AI Tools in Research and Writing").** JVS follows Elsevier policy:
  - Writing help (editing, outlining, summarizing, reference and format checks, translation) goes in a section placed **directly before the References**, using the journal's wording: "Declaration of Generative AI and AI-Assisted Technologies in the Writing Process. During the preparation of this work the authors used [tool] in order to [reason]. After using this tool, the authors reviewed and edited the content as needed and take full responsibility for the content of the publication." Name Claude (Anthropic) and list what it actually did on this paper.
  - AI used in the research itself (study design, data collection, analysis code, statistics, charts) is described in the **Methods**, in enough detail for reproducibility, and in figure captions where it drew a figure. Only David can say what was used: ask him before building the package, then write the sentence as he confirms it. Never leave it highlighted for him to decide in the file.
  - Spelling and grammar checks alone need no disclosure.
- **Not in the manuscript:** author contributions and conflicts of interest go on the Application for Publication form, not in the text.
- **Acknowledgement:** add the JSCOR sentence when /format calls for it.
- **Tables** are numbered in Roman numerals (Table I, II, III), in order of first mention, with every callout, caption and cross-reference updated.
- **References:** JVS style (6 authors then et al, no issue number, abbreviated pages), checked against PubMed as /format describes.
- **EM preferred order for the manuscript file:** check David's EM "Preferred Order" screen. The 2026 REACH package used: no "Prepared for" line, Keywords and Funding directly after the Abstract, no email list, and the corresponding author's email in the correspondence block.
- Accept all changes properly. A deleted paragraph mark must not merge the next heading into the previous paragraph. Render the result and look at every page.

## 2b. What the JVS editorial office checks on first pass (returned list, 5 Nov 2026)
Every one of these came back as a correction on a package that had passed its own audit. Build to them:
- No figures or tables embedded in the manuscript file. Tables go in one separate Word document (Times New Roman 12 pt, each table on its own page with its legend); figure legends go in a separate Word document; figures are uploaded one file each.
- Title page carries a conflicts statement for all authors: "The authors have no competing interests." when there are none. (It is on the Application form too; EM wants both.)
- Figures referenced sequentially in the text, **and legend text counts**: a Figure 4 legend that says "the models compared in Figure 6" is read as Figure 6 cited before Figure 5. Keep cross-references to later figures out of legends.
- Every supplemental item cited in the text (an uncited Supplementary Figure S1 was flagged) and in ascending order, again counting legend text (a Figure 5 legend naming S5 before the Results cited S4 was flagged).
- Page numbers top right and line numbers that restart on each page in the Word file. In python-docx: a `PAGE` field in the header, right aligned, and `<w:lnNumType w:countBy="1" w:restart="newPage"/>` in every `sectPr`.
- Figures as TIFF, JPEG or EPS. PNGs upload without complaint but are not on the accepted list; send the 600 dpi TIFFs.
- The title page names the corresponding author **and** a post-publication corresponding author (the Application form's note requires both).
- Tables in Roman numerals (Table I, II) in the text, the tables file, the TRIPOD checklist and the supplement; the live guide still says so.

## 2c. Editorial Manager metadata and the built PDF
- The EM "Corresponding Author" is the submitting account unless changed under Manage Co-authors. It must match the title page correspondence block, the cover letter and the person the Application form designates and who signs it. A Nov 2026 submission went in with David as EM corresponding author, Dr Abularrage on the title page and form, and David's signature on the form: three answers to one question. Decide this with David before any file is built and check all four places.
- After submission, download the EM-built PDF (JVS-D-xx-xxxxx.pdf) and read every page. It shows the uploaded file names and types (that is how the PNG figures were caught), the metadata screen, and every file as reviewers will see it, including an optional visual abstract with a typo in it.
- A visual abstract is requested with the revision, not the first submission; uploading it early makes it part of the reviewer PDF.

## 3. Package (one folder, numbered files)
- 00 checklist of every file and every EM item, with answers
- 01 Cover letter (.docx and .pdf)
- 02 Manuscript, in 12 pt Times New Roman, double spaced, with page numbers
- Abstract, each table (Table I, II, III) and the figure legends as separate files
- Online supplement
- Figures: one TIFF per figure, rendered from the vector PDF (`pdftoppm -r 1200 -tiff -tiffcompression lzw` for line art; 300 dpi or more for photographs), plus the PDFs kept alongside
- Visual abstract draft (section 4)
- Application for Publication (section 5)
- `source_and_alternates/`: the locked master (Word `documentProtection` read-only), the tracked version and the PNG/PDF figures

If a file is revised after David has a copy, save it as `_v2`, `_v3`, never over the old one. This applies to every file in the package, the visual abstract and the forms included; overwriting a visual abstract three times in one afternoon (Oct 2026) made the versions impossible to tell apart.

## 4. Visual abstract draft
- Start from David's most recent JVS visual abstract PowerPoint (e.g., `REACH_PAD_JVS_VisualAbstract_v3.pptx`) and keep its layout. Ask for it if it is not in reach.
- Use the final manuscript title verbatim and the same headline numbers as the Abstract. Every number is traced to the manuscript, never retyped from memory.
- Lato for all text, the /format figure palette, no abbreviations a reader cannot decode, and no title truncated to fit (resize the text instead).
- Render to PNG and look at it before sending. It is a draft for David to edit.

## 5. Application for Publication
- Current form: https://vascular.org/sites/default/files/2026-04/Application_for_Publication.docx (April 2026). Visual abstract template: https://legacyfileshare.elsevier.com/gfa/journal-specific/ymva-visual-abstract-template.pptx (13.33 x 7.5 in, four layouts; the headings are text boxes on the slide layout, so rename them in the layout, not the slide). Both download with curl from the cloud workspace.
- Form mechanics learned Oct to Nov 2026: title, corresponding author, overall-responsibility name and date are `w:sdt` content controls (clear `w:showingPlcHdr` when filling); the checkboxes are `w14:checkbox` controls (set `w14:checked` to 1 and the glyph to ☒); the contributions table is `doc.tables[1]`, data rows from index 4, columns Last name, Initials, Conception, Analysis, Data collection, Writing, Critical revision, Approval, Accountable, Statistical analysis, Funding. The red "Role of Sponsors" box is an Example text box (`w:txbxContent`, present twice because of `mc:AlternateContent`) that python-docx's paragraph list does not see; put the sponsor statement in the box and nowhere else, or the rendered form shows it twice.
- Originality: a registry paper whose cohort was reported before is "Follow up", with the prior paper's DOI, the % increase in patients and the added years of follow-up, not "Completely Original".
- Fill the real template with python-docx: content controls for the title, corresponding author, checkboxes and date; the contributions table (rows per author, columns per role, with Approval and Accountability checked for every author); COI, sponsors and off-label fields.
- Roles, conflicts, prior presentation and the signer come from David. Ask about anything not yet confirmed in the reply; the form itself carries no highlighting.
- The signer and the person named as corresponding author must be consistent. Flag it if they differ.

## 6. Editorial Manager checklist answers
In the 00 checklist, draft an answer for each EM item David will meet, with the place in the manuscript that supports it: article type, the guidelines paragraph (True, and where), Use of AI Tools (Yes or No, and where the declaration and any Methods sentence are), data availability, and reporting guideline (STROBE or RECORD).

## 7. Double check everything
- **Authors first.** Run the /format "Author check before every submission" again on the final manuscript, against the roster or a printed byline, not against the other files. A consistency check cannot catch a name that is wrong in the manuscript itself (an Oct 2026 package nearly went out with a coauthor's nickname this way). Then confirm every file (title pages, Abstract file, cover letter, visual abstract author line, Application for Publication names and initials, EM author entries) matches it.
- Extract text from every file in the package and check against the final manuscript: the title (character for character), author list, order and credentials, every number in the cover letter, visual abstract, figures, legends and Highlights, and table and figure numbering.
- Run a fresh agent with no access to the drafting history to repeat the check from the files alone, and reconcile what it finds.
- Run the office's first-pass list (section 2b) as its own check: no embedded figures or tables, separate tables and legends files, conflicts line on the title page, figure and supplement order including legend text, page and line numbers, TIFF figures, post-publication corresponding author, Roman numeral tables.
- Check the counts against the limits again after the final accept. Search every package file for highlighting, comments, tracked changes and placeholders (`w:highlight`, yellow shading, `[`, `***`), and confirm zero before calling the package final: a submission file never carries highlighting (see /format).
- Report what is still open (unverified author names, degrees or affiliations, unconfirmed roles, COI, signer, AI Methods sentence) at the top of the reply, not buried in the checklist.