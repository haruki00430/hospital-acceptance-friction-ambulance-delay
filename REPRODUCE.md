# Reproduction Guide / 再現手順

This document explains how to use the verified outputs and how to re-run the formal R analysis.

本ドキュメントは、検証済み出力の使い方と、正式R解析の再実行手順を説明します。

Related public-repo style: [`ndb-pm25-diabetes-japan/REPRODUCE.md`](https://github.com/haruki00430/ndb-pm25-diabetes-japan/blob/main/REPRODUCE.md).

---

## Option A — Use frozen manuscript tables (no re-run) / 凍結結果を使う（再実行不要）

Publication-facing estimates are in:

論文用の凍結推定量は次にあります。

```text
results/publication/results_primary_first_difference.csv
results/publication/results_primary_weighted.csv
results/publication/results_corroborative.csv
results/publication/results_lag_direction.csv
results/publication/results_loo_prefecture.csv
results/publication/results_loo_year.csv
docs/SOURCE_OF_TRUTH.md
```

Do **not** mix older bootstrap CI endpoints from draft memos.

下書きメモの古いブートストラップCI端点を混在させないでください。

---

## Option B — Re-run the R script / Rスクリプト再実行

### Requirements / 必要環境

- R ≥ 4.6 recommended (verified with R 4.6.1)
- Packages (see `logs/package_versions.csv`):
  - `data.table`, `fixest`, `fwildclusterboot`, `clubSandwich`, `jsonlite`, `digest`

### Run from repository root / リポジトリルートから実行

```bash
Rscript analysis/R/jft02_p2r_analysis_v1_1.R
```

The script reads:

スクリプトの入力:

| Path | Role |
|------|------|
| `data/*.csv` | Analysis inputs (SHA-256 fail-closed) |
| `reference/python_reference_results.csv` | Python–R Class A/B comparison |

It writes rerun artifacts under `results/` (CSV), `figures/` (PDF), `logs/`, and `docs/` (report regeneration).  
Frozen manuscript tables remain under `results/publication/` and `figures/manuscript_png/` unless you deliberately replace them.

再実行出力は `results/`・`figures/`（PDF）・`logs/` 等へ書き出されます。  
論文用凍結ファイルは `results/publication/` と `figures/manuscript_png/` に残ります（意図的に置換しない限り）。

### Seed and bootstrap / シードとブートストラップ

- Seed: `20260715`
- Wild cluster bootstrap: B = 9999, Rademacher, null imposition, prefecture clustering

Re-running WCB may show small CI endpoint differences across package versions; keep the frozen `results/publication/` files as manuscript source of truth unless a deliberate re-freeze is documented.

WCB再実行はパッケージ版によりCI端点がわずかに変わることがあります。論文の正本は、再凍結を文書化するまで `results/publication/` を用いてください。

---

## Data only / データについて

All inputs are **public aggregate** FDMA-derived prefecture-year tables. No individual records.

入力はすべて消防庁由来の**公開集計**です。個人レコードはありません。

See [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md) and provenance files under `docs/`.

---

## Audit-only outputs / 監査専用出力

Files under `results/additional_audit_not_publication_claims/` are retained for transparency (e.g., exploratory period interaction).  
Do **not** cite them as prespecified publication claims unless the manuscript is revised accordingly.

`results/additional_audit_not_publication_claims/` は透明性のための監査出力です。  
原稿を改訂して明示しない限り、事前規定の出版主張として引用しないでください。
