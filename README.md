> **Repository:** https://github.com/haruki00430/hospital-acceptance-friction-ambulance-delay  
> **Reproduction:** [`REPRODUCE.md`](REPRODUCE.md) · [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md) · [`analysis/README.md`](analysis/README.md) · [`CITATION.cff`](CITATION.cff)  
> **Zenodo:** https://doi.org/10.5281/zenodo.21392281

# Hospital-Acceptance Friction and Delayed Ambulance Scene Arrival

## A Prefecture-Year Panel Study in Japan, 2014–2024

**論文タイトル（日本語）**: 病院収容照会困難と救急現場到着遅延の連動：日本の都道府県×年パネル分析（2014–2024）

**Manuscript target:** *Paramedicine* (Sage, Diamond OA) — under review  
**Authors:** Haruki Saito; Tetsuya Ohira (Fukushima Medical University)

---

## Abstract / 研究概要

Ambulance scene-arrival delay is often treated as a prehospital performance metric, but it may also reflect congestion elsewhere in the emergency care system. Using official Fire and Disaster Management Agency (FDMA) **public aggregate** prefecture-year statistics for all 47 Japanese prefectures (2014–2024), this study examines whether within-prefecture annual increases in hospital-acceptance friction (share of severe-or-more-serious transports requiring ≥4 acceptance inquiries) are associated with delayed call-to-scene arrival (≥10 minutes).

救急の現場到着遅延は、搬送前のパフォーマンス指標として扱われがちですが、救急医療システムの他部位の輻輳を反映している可能性があります。本リポジトリは、消防庁の**公開集計**（47都道府県×年）に基づく解析用データ・Rコード・検証済み結果表・図・由来記録を公開用に整理したものです。個人単位の患者データは含みません。

**Primary estimate (source of truth):** β = 0.435 percentage points (WCB 95% CI 0.222–0.564; p = 0.0003). See [`docs/SOURCE_OF_TRUTH.md`](docs/SOURCE_OF_TRUTH.md).

---

## What is included / 同梱内容

| Path | English | 日本語 |
|------|---------|--------|
| `data/` | Analysis-ready CSV panels | 解析用パネルCSV |
| `analysis/R/` | Formal R reproduction script (v1.1) | 正式R再現スクリプト |
| `reference/` | Python reference coefficients for Class A/B checks | Python参照係数 |
| `results/publication/` | Manuscript-facing verified tables | 論文用・検証済み結果 |
| `results/additional_audit_not_publication_claims/` | Transparency-only audit outputs | 監査用（出版主張には使わない） |
| `figures/manuscript_png/` | Manuscript figures (PNG) | 論文図PNG |
| `docs/` | Provenance, STROBE map, analysis reports | 由来・STROBE・解析報告 |
| `logs/` | Session info, run/deviation logs | 実行環境・逸脱ログ |
| `CITATION.cff` / `.zenodo.json` | Citation & Zenodo metadata | 引用・Zenodoメタデータ |

**Not included / 含まないもの**

- Journal submission DOCX / title page / cover letter  
- Raw FDMA yearbook PDFs (cite via provenance URLs)  
- Individual-level or non-public data  

Style reference for this repository layout: public repos such as [`institutional-channel-simulation-study`](https://github.com/haruki00430/institutional-channel-simulation-study) and [`ndb-pm25-diabetes-japan`](https://github.com/haruki00430/ndb-pm25-diabetes-japan).

---

## License / ライセンス

| Material | License |
|----------|---------|
| Code (`analysis/` and other software) | [MIT](LICENSE) |
| Derived data, results, figures, docs | [CC BY 4.0](DATA_LICENSE.md) |

Article copyright for the journal submission is separate from this repository.

---

## Quick start / クイックスタート

```bash
git clone https://github.com/haruki00430/hospital-acceptance-friction-ambulance-delay.git
cd hospital-acceptance-friction-ambulance-delay
```

- **Use verified numbers without re-running:** open `results/publication/results_primary_first_difference.csv` and `docs/SOURCE_OF_TRUTH.md`.  
  **再実行なしで数値を使う:** 上記CSVと SOURCE_OF_TRUTH を参照。
- **Re-run analysis:** see [`REPRODUCE.md`](REPRODUCE.md) and [`analysis/README.md`](analysis/README.md).  
  **解析の再実行:** REPRODUCE.md と analysis/README.md を参照。

---

## Ethics / 倫理

This study uses only publicly available aggregate government statistics and does not involve individual-level human data. It is not human subjects research; institutional ethics review was not required.

本研究は公開集計統計のみを用い、個人単位データは扱いません。ヒトを対象とする研究には該当せず、機関の倫理審査は不要です。

---

## Citation / 引用

Please cite this repository via `CITATION.cff` or the Zenodo archive:  
https://doi.org/10.5281/zenodo.21392281

引用は `CITATION.cff` または Zenodo アーカイブ（上記 DOI）をご利用ください。  
論文掲載後は `related_identifiers` に掲載 DOI を追記予定です。
