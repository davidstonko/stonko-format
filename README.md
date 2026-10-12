# /format: a Claude skill for the Stonko manuscript template

A [Claude skill](https://support.claude.com/en/articles/12512180-use-skills-in-claude) that puts a Word manuscript into my standard journal-submission format and holds the house style my group uses for statistics, tables, figures and references. It formats; it does not write the science.

## What it does

- Restyles a `.docx`: Times New Roman 11 pt everywhere, US Letter with 1-inch margins, bold 11 pt headings, single-spaced title page and Abstract, double-spaced body with a 0.5 in first-line indent, single-spaced references and tables, wide tables kept in landscape.
- Prepends the title page: working-paper line with date, title, short running title, authors with superscript affiliations, correspondence, funding, emails, keywords.
- Carries the house style for reporting results: `P=0.03`, `P<0.001`, `(aOR, 0.57; 95% CI, 0.39–0.83; P=0.003)`, median (IQR) as `65 (58–74)`, small-cell suppression, and the rule that every claim in the Conclusions is backed by a result with a P value.
- Knows Journal of Vascular Surgery conventions (superscript citations after punctuation, reference format, Article Highlights, Table of Contents Summary).
- Keeps a verified roster of frequent coauthors (degrees and affiliations as printed) and the procedure for verifying anyone not on it.

## What's in this repo

| Path | Purpose |
|---|---|
| `format/SKILL.md` | The skill: formatting specification, house style, title page, references |
| `format/scripts/apply_format.py` | Helper that applies the template to a `.docx` and prints a style check |
| `format/assets/manuscript_template.docx` | Reference copy of the template |
| `format.zip` | The packaged skill, ready to upload |

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

The text of the manuscript is never changed. The run ends with a style check that warns about em dashes, P values and confidence intervals that are not in house style, and fonts over 11 pt.

## Adapting it

The title-page defaults (author, correspondence address, email, funding sentence) are mine. To use the template yourself, change the constants at the top of `apply_format.py` and the "Author details" section of `SKILL.md`.

## Changelog

- **2.0 (Oct 2026).** House style for statistics, tables and figures; Conclusions rule; JVS conventions; REACH dataset citation; multi-author title page (`--authors`, `--affil`); body indent and paragraph spacing; single-spaced tables; landscape table sections preserved; black headings; style check.
- **1.0 (Aug 2026).** Template, title page, verified coauthor roster, reference verification rules.

Maintained by David P. Stonko, MD, MS (Johns Hopkins). Not an official Johns Hopkins or journal template; check the journal's current author guide before submission.
