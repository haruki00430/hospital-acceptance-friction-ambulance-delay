# Source of truth / 数値の正本

Manuscript-facing numbers must come from the files below (relative paths in this repository).

論文・投稿に使う数値は、必ず以下（本リポジトリ相対パス）から取ること。

## Primary files / 主ファイル

| Item | Path | SHA-256 |
|------|------|---------|
| Primary result CSV | `results/publication/results_primary_first_difference.csv` | `87510063d80a37592a3562da9f309e240fe1b359e3a404bdf00224145f62616b` |
| Analysis script | `analysis/R/jft02_p2r_analysis_v1_1.R` | `6d5e3a6c66f03ea89fc28c89ceef8dbf853a4ca8ef9d5b87d96166b7068af85d` |

Note: The script SHA-256 differs from the internal Phase P2R package only because paths were adapted for this repository (`data/` instead of `input/`, bilingual header). Scientific estimators are unchanged; the primary CSV hash above remains the manuscript source of truth.

注: スクリプトのハッシュが内部パッケージと異なるのは、本リポジトリ向けに `data/` 配置へパスを合わせたためです。推定量の定義は同一で、論文の数値正本は上記 primary CSV です。

- Primary seed: `20260715`
- Wild cluster bootstrap: B = `9999` (Rademacher, null imposition, two-tailed, prefecture clustering)

## Formal primary estimate / 正式な主推定量

| Quantity | Value |
|----------|-------|
| β | `0.435446048604` |
| WCB 95% CI | `0.221984028769` to `0.564341596056` |
| WCB p | `0.0003` |
| CR2 95% CI | `0.257560717787` to `0.613331379421` |
| CR2 p | `0.0004` |

Do not mix older draft bootstrap endpoints into manuscript text.

下書き段階の古いブートストラップCI端点を本文・表・補足に混在させないこと。
