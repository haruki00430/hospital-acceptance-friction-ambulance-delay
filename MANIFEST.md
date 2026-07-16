# Public release file map / 公開対象ファイル一覧

This repository is currently **Private**, but contents are curated as **public-ready** (same standard as sibling public repos such as `institutional-channel-simulation-study` and `ndb-pm25-diabetes-japan`).

本リポジトリは現時点で Private ですが、内容は公開可能な水準で整理しています。

## Included / 含む

- Root: `README.md`, `REPRODUCE.md`, `DATA_DICTIONARY.md`, `LICENSE`, `DATA_LICENSE.md`, `CITATION.cff`, `.zenodo.json`, `MANIFEST.md`, `.gitignore`
- `data/` — analysis-ready public aggregate CSVs
- `analysis/` — R script + bilingual README
- `reference/` — Python reference coefficients
- `results/publication/` — verified manuscript tables
- `results/additional_audit_not_publication_claims/` — audit-only (labeled)
- `figures/manuscript_png/` — manuscript PNGs
- `docs/` — provenance, STROBE, analysis reports, `SOURCE_OF_TRUTH.md`
- `logs/` — session / run / deviation / build logs
- `SHA256SUMS.txt` — checksums for packaged release files (regenerate after intentional freezes)

## Excluded on purpose / 意図的に除外

- Journal submission DOCX, title page, cover letter, author-only checklists
- Local machine absolute paths / manuscript QA JSON with private paths
- Raw FDMA PDF yearbooks
- Hub-internal Step 1–3 drafting notes under `projects/JFT02/JFT02_manuscript_*`

## Audit labeling / 監査出力の扱い

Anything under `results/additional_audit_not_publication_claims/` must not be cited as a primary publication claim unless the manuscript explicitly describes it.
