# Data dictionary / データ辞書

Main analytic file / 主解析ファイル: `data/jft02_merged_panel_v1_0.csv`

| Variable | English | 日本語 |
|----------|---------|--------|
| `prefecture_code` | Prefecture code | 都道府県コード |
| `prefecture` | Prefecture name | 都道府県名 |
| `year` | Calendar / data year | 年 |
| `acceptance_ge4_pct` | % of severe-or-more-serious transports with ≥4 hospital-acceptance inquiries | 重症以上搬送のうち受入照会≥4回の割合（%） |
| `scene_ge10_pct` | % of ambulance dispatches with call-to-scene arrival ≥10 minutes | 通報〜現場到着≥10分の出動割合（%） |
| `annual_transport_strain_dispatches_per_team` | Annual dispatches per ambulance team | 救急隊1隊あたり年間出動件数 |
| `call_to_scene_arrival_mean_minutes` | Mean call-to-scene arrival time (minutes) | 通報〜現場到着の平均時間（分） |
| `acceptance_ge4_cases_per_1000_dispatches` | ≥4-inquiry cases per 1,000 dispatches | 出動1,000件あたり照会≥4回件数 |
| `scene_stay_ge30_pct` | % of severe-or-more-serious transports with scene stay ≥30 minutes | 重症以上のうち現場滞在≥30分の割合（%） |

## Other input files / その他の入力

| File | Role |
|------|------|
| `data/acceptance_friction_panel_completed.csv` | Acceptance-friction extraction panel |
| `data/jft02_scene_stay_ge30_panel_v1_0.csv` | Scene-stay ≥30 min panel |
| `data/jft01_panel_derived_v1_3.csv` | Linked derived panel used in corroborative builds |

Detailed provenance: `docs/jft01_source_provenance_v1_3.csv`, `docs/acceptance_friction_*`, `docs/source_package_README.md`.

詳細な由来・抽出記録は `docs/` 配下を参照してください。
