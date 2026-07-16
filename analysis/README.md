# Analysis code / 解析コード

## Script / スクリプト

`analysis/R/jft02_p2r_analysis_v1_1.R`

Formal R reproduction for the prefecture-year first-difference analysis (Phase P2R v1.1): wild cluster bootstrap, CR2/Satterthwaite, corroborative models, lag direction, LOO, Python–R Class A/B checks, and regression tests.

都道府県×年の一階差分モデルの正式R再現（Phase P2R v1.1）です。Wild cluster bootstrap、CR2/Satterthwaite、裏付けモデル、ラグ方向、LOO、Python–R 分類、回帰テストを含みます。

## How to run / 実行方法

From the **repository root**:

```bash
Rscript analysis/R/jft02_p2r_analysis_v1_1.R
```

See also [`../REPRODUCE.md`](../REPRODUCE.md).

## Path layout expected by the script / スクリプトが想定する配置

| Directory | Contents |
|-----------|----------|
| `data/` | Input CSVs (fail-closed SHA-256 checks) |
| `reference/` | `python_reference_results.csv` |
| `results/` | Rerun CSV outputs (frozen manuscript tables stay in `results/publication/`) |
| `figures/` | Rerun PDF figures (manuscript PNGs stay in `figures/manuscript_png/`) |
| `logs/` | Session / run / deviation logs |

## Notes / 注意

- Code comments in the script are primarily English; this README provides bilingual orientation.  
  スクリプト内コメントは主に英語です。日英の案内は本READMEを参照してください。
- Do not treat `results/additional_audit_not_publication_claims/` as prespecified publication evidence.  
  監査用フォルダの出力を事前規定の出版証拠として扱わないでください。
