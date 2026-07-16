# JFT-02 Phase P2R Corrective Package v1.1

## 概要

JFT-02「病院収容困難と救急現場到着遅延の連動輻輳解析」の正式 R 再現パッケージ（修正再実行版）。

**指示書**: JFT02_PhaseP2R_修正再実行指示書_v1.1.docx  
**対応バージョン**: v1.0 からの全修正点を実装

## 実行方法

パッケージルート（このファイルのあるディレクトリ）から実行:

```bash
Rscript analysis/R/jft02_p2r_analysis_v1_1.R
```

**前提条件**:
- R 4.6.1 以上
- 必要パッケージ: data.table, fixest, fwildclusterboot, clubSandwich, jsonlite, digest

## ディレクトリ構造

```
JFT02_PhaseP2R_Corrective_Package_v1_1/
├── README.md                         ← このファイル
├── analysis/
│   └── R/
│       └── jft02_p2r_analysis_v1_1.R ← メインスクリプト
├── input/                            ← 凍結入力 CSV（SHA-256 検証対象）
│   ├── jft02_merged_panel_v1_0.csv
│   ├── acceptance_friction_panel_completed.csv
│   ├── jft02_scene_stay_ge30_panel_v1_0.csv
│   └── jft01_panel_derived_v1_3.csv
├── reference/
│   └── python_reference_results.csv  ← Python 参照値（A/B/C 分類基準）
├── results/                          ← 解析出力 CSV（自動生成）
├── figures/                          ← PDF 図（自動生成）
├── logs/                             ← 実行ログ・build_summary.json（自動生成）
└── docs/                             ← 報告書・サマリー MD（自動生成）
```

## 主要変更点（v1.0 → v1.1）

| 項目 | v1.0 | v1.1 |
|------|------|------|
| SHA-256 | 記録のみ | fail-closed (HARD STOP) |
| QA | QA1-QA5 | QA1-QA8 (範囲・N・ラベルチェック追加) |
| CR2/Satterthwaite | なし | 主解析 + C1-C3a |
| C3b | なし | 追加 |
| S8 加重感度分析 | なし | 追加 |
| Reverse lag CI | NA | CR2/Satterthwaite 代替 |
| LOO 最大影響分析 | なし | Δβ・相対変化・依存判定 |
| 期間交互作用検定 | なし | 追加 |
| Python-R 分類 | TRUE/FALSE | A/B/C 3段階 |
| 回帰テスト | なし | T01-T08 |
| 図 | なし | Figure 1-3 + supp 4 図 |
| p=0 表記 | 0 のまま | p < 1/(B+1) = p < 0.0001 |

## 完了ステータス

スクリプト終了時に `logs/build_summary.json` を確認:
- `completion_status` フィールドに完了判定が記録される
- `python_r_classification` が A または B であれば Scientific Review へ提出可

## 入力データ (SHA-256 expected)

| ファイル | SHA-256 |
|---------|---------|
| jft02_merged_panel_v1_0.csv | cbbedddc481db5a3... |
| acceptance_friction_panel_completed.csv | 7324c803... |
| jft02_scene_stay_ge30_panel_v1_0.csv | 6a27e45d... |
| jft01_panel_derived_v1_3.csv | 1b70c0b2... |
