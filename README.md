# /format and /jvsformat: Claude skills for the Stonko manuscript template

A [Claude skill](https://support.claude.com/en/articles/12512180-use-skills-in-claude) that puts a Word manuscript into my standard journal-submission format and holds the house style my group uses for statistics, tables, figures and references. It formats; it does not write the science.

## What it does

- Restyles a `.docx`: Times New Roman 11 pt everywhere, US Letter with 1-inch margins, bold 11 pt headings, single-spaced title page and Abstract, double-spaced body with a 0.5 in first-line indent, single-spaced references and tables, wide tables kept in landscape.
- Prepends the title page: working-paper line with date, title, short running title, authors with superscript affiliations, correspondence, funding, emails, keywords.
- Carries the house style for reporting results: `P=0.03`, `P<0.001`, `(aOR, 0.57; 95% CI, 0.39–0.83; P=0.003)`, median (IQR) as `65 (58–74)`, small-cell suppression, and the rule that every claim in the Conclusions is backed by a result with a P value.
- Adds the JSCOR acknowledgement to any paper with Caitlin Hicks or JSCOR data.
- Knows Journal of Vascular Surgery conventions (superscript citations after punctuation, reference format, Article Highlights, Table of Contents Summary).
- Keeps a verified roster of frequent coauthors (degrees and affiliations as printed) and the procedure for verifying anyone not on it, and runs an author check against that roster before any submission.

## What's in this repo

| Path | Purpose |
|---|---|
| `format/SKILL.md` | The skill: formatting specification, house style, title page, references |
| `format/scripts/apply_format.py` | Helper that applies the template to a `.docx` and prints a style check |
| `format/assets/manuscript_template.docx` | Reference copy of the template |
| `format.zip` | The packaged skill, ready to upload |
| `jvsformat/SKILL.md` | /jvsformat, the Journal of Vascular Surgery fork (below) |
| `jvsformat.zip` | The packaged fork, ready to upload |

## Install

In Claude, go to **Customize > Skills**, click **+**, choose **Create skill**, then **Upload a skill**, and select `format.zip` (do not unzip it). Then attach a manuscript and type `/format`.

## Use the helper directly

```bash
pip install python-docx
python format/scripts/apply_format.py draft.docx \
  --title "Full title" --short-title "Running title" \
  --keywords "kw1, kw2, kw3" --date "Oct. 2026" \
  --authors "First Author, MD^1; Senior Author, MD, PhD^2" \
  --affil "Affiliation one" --affil "Affiliation two" \
  --output formatted.docx
```

The text of the manuscript is never changed. The run ends with a style check that warns about em dashes, P values and confidence intervals that are not in house style, and fonts over 11 pt, then an author check that flags placeholders, authors not on the verified roster and degrees that differ from it.

## /jvsformat: the Journal of Vascular Surgery fork

/jvsformat is a fork of /format. It loads /format first, so every house rule above still applies, then takes the formatted paper all the way to a JVS submission package:

1. **Cover letter to the editor** on the corresponding author's letterhead, with logo (through [/jhsurgeryformat](https://github.com/davidstonko/jh-surgery-format)), signed with the credentials on the title page.
2. **Conformance pass** as tracked changes: JVS limits, title and abstract rules, Article Highlights, Table of Contents Summary, the clinical practice guidelines paragraph and the AI-use declaration that Editorial Manager asks about, Roman-numeral tables, JVS reference style, Editorial Manager's preferred order.
3. **The package**: separate manuscript, abstract, table and legend files, 1200 dpi TIFF figures from the vector PDFs, online supplement, and a locked master.
4. **A draft visual abstract** from your last JVS PowerPoint, with the title and numbers taken from the manuscript.
5. **The Application for Publication** filled from the journal's own form, with anything unconfirmed asked about rather than guessed.
6. **Editorial Manager checklist answers**, each pointing to where the manuscript supports it.
7. **A full audit**: authors checked against the roster or a printed byline, then every number, title and name in every file checked against the final manuscript, then the same check repeated by a fresh agent that has not seen the drafting.

Install `jvsformat.zip` next to `format.zip`, attach your manuscript and type `/jvsformat`. It asks for the author list, the corresponding author and who signs the form before it builds anything. It never invents a contribution role, conflict of interest, credential or number; those come from you.

## Adapting it

The title-page defaults (author, correspondence address, email, funding sentence) are mine. To use the template yourself, change the constants at the top of `apply_format.py` and the "Author details" section of `SKILL.md`.

## Changelog

- **2.3 (Nov 2026).** No highlighting, comments or placeholders in any final or submission file; author check before every submission (skill and helper), never fill an author slot; statistics in text written `(aOR, 0.57; 95% CI, 0.39–0.83; P=0.003)` and the helper's CI check updated to match (2.2's check flagged the correct form); figures in Lato; JVS Application for Publication, clinical practice guidelines paragraph; /jvsformat fork added.
- **2.2 (Oct 2026).** Statistics in text written `aOR 2.70 (95% CI: 2.44–2.99)` (style check updated); figures back to Arial.
- **2.1 (Oct 2026).** Order of precedence (journal first); JSCOR acknowledgement for Hicks/JSCOR papers; Results lead with the finding; tables numbered in order of first mention with a renumbering procedure; navy flow-diagram style, flow-diagram content rules, CMYK TIFF export; PubMed reference check through the desktop browser (E-utilities blocked) and claim checks.
- **2.0 (Oct 2026).** House style for statistics, tables and figures; Conclusions rule; JVS conventions; REACH dataset citation; multi-author title page (`--authors`, `--affil`); body indent and paragraph spacing; single-spaced tables; landscape table sections preserved; black headings; style check.
- **1.0 (Aug 2026).** Template, title page, verified coauthor roster, reference verification rules.

Maintained by David P. Stonko, MD, MS (Johns Hopkins). Not an official Johns Hopkins or journal template; check the journal's current author guide before submission.
