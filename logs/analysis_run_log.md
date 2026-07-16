# JFT-02 Phase P2R v1.1 Run Log

**開始**: 2026-07-15 15:24:22
**終了**: 2026-07-15 15:24:27
**所要時間**: 0.07 分

## Seed 一覧

| Model | Seed |
|-------|------|
| Primary | 20260715 |
| C1 | 20260716 |
| C2 | 20260717 |
| C3a | 20260718 |
| C3b | 20260718 |
| Forward lag | 20260719 |
| Reverse lag | 20260720 |
| S8 weighted | 20260715 |

## WARNフラグ

[15:24:24] DEV-P2R-004: Reverse lag WCB CI inversion failed; using CR2/Satterthwaite fallback
W03: reverse-lag WCB CI inversion failed; CR2 fallback used
[15:24:26] W01: primary CI endpoint diff >0.05 ( 0.0567 )

## STOPフラグ（発火なし = 全PASS）

(なし)

## 実行ログ全文

[15:24:22] === JFT-02 Phase P2R v1.1 開始 ===
[15:24:22] R version 4.6.1 (2026-06-24 ucrt)
[15:24:22] fixest: 0.14.2 | fwildclusterboot: 0.14.3 | clubSandwich: 0.7.0
[15:24:22] --- § 1  SHA-256 fail-closed ---
[15:24:22] SHA OK: jft02_merged_panel_v1_0.csv
[15:24:22] SHA OK: acceptance_friction_panel_completed.csv
[15:24:22] SHA OK: jft02_scene_stay_ge30_panel_v1_0.csv
[15:24:22] SHA OK: jft01_panel_derived_v1_3.csv
[15:24:22] input_sha256_validation.csv saved — all SHA match
[15:24:22] --- § 2  Data load + QA ---
[15:24:22] merged panel: 517 rows x 58 cols
[15:24:22] QA1 PASS: 517 rows
[15:24:22] QA2 PASS: 47 prefs × 2014-2024
[15:24:22] QA3 PASS: no duplicates
[15:24:22] QA4 PASS: no missing primary vars
[15:24:22] QA5 PASS: denominators identical in all 517 rows
[15:24:22] QA6 PASS: all primary vars in [0,100]
[15:24:22] QA8 PASS: variable name correct
[15:24:22] --- § 3  First-Difference 変数 ---
[15:24:22] QA7 PASS: FD N=470, 47 clusters
[15:24:22] Lag panel: 423 rows (2016-2024) PASS
[15:24:22] --- § 4  Primary model (seed=20260715) ---
[15:24:22] Primary β = 0.435446
[15:24:23] Primary WCB p = 3e-04 WCB 95%CI [ 0.222 , 0.5643 ]
[15:24:23] Primary CR2 SE = 0.0784 df = 8.8 p_Satt = 4e-04
[15:24:23] S8 denominator-weighted ---
[15:24:23] S8 β = 0.506935 WCB p = < 0.0001
[15:24:23] results_primary_weighted.csv saved
[15:24:23] --- § 5  Corroborative C1-C3b ---
[15:24:23] C1_scene_arrival_time β= 0.080529 WCB p= 1e-04
[15:24:23] C2_accept_burden β= 0.402385 WCB p= 0.0017
[15:24:23] C3a_scene_stay_exposure β= 0.439212 WCB p= < 0.0001
[15:24:24] C3b_scene_stay_time β= 0.058385 WCB p= < 0.0001
[15:24:24] Holm C1-C3a: 2e-04, 0.0017, 0
[15:24:24] results_corroborative.csv saved
[15:24:24] --- § 6  Level FE ---
[15:24:24] Level FE β = 0.677458 95%CI [ 0.4189 , 0.936 ]
[15:24:24] results_primary_level_fe.csv saved
[15:24:24] --- § 7  Downstream coherence ---
[15:24:24] D1 β = 0.8415 | D2 β = 0.593
[15:24:24] results_downstream.csv saved
[15:24:24] --- § 8  Lag-direction ---
[15:24:24] Forward β = 0.509445 WCB p = 0.0028
[15:24:24] DEV-P2R-004: Reverse lag WCB CI inversion failed; using CR2/Satterthwaite fallback
[15:24:24] Reverse β = -2.7e-05 WCB p = 0.9993 CI method: CR2_Satterthwaite_fallback
[15:24:24] results_lag_direction.csv saved
[15:24:24] --- § 9  Period stability + interaction ---
[15:24:24] 2015-2019 β = 0.294502 p = 0.1059
[15:24:24] 2020-2024 β = 0.447218 p = 0
[15:24:24] results_period_stability.csv saved
[15:24:24] Period interaction β = 1.003174 CR2 p = 0.0021 | period difference interpretation: formally tested and supported
[15:24:24] results_period_interaction.csv saved
[15:24:24] --- § 10  Capacity moderation ---
[15:24:24] Capacity moderation interaction β = 0.15766
[15:24:24] results_capacity_moderation.csv saved
[15:24:24] --- § 11  LOO prefecture (47 runs) ---
[15:24:26] LOO pref range [ 0.3619 , 0.4522 ] | max impact: pref 13 Δβ= 0.0736 ( 16.9 %)
[15:24:26] results_loo_prefecture.csv saved
[15:24:26] --- § 12  LOO year (10 runs) ---
[15:24:26] LOO year range [ 0.3365 , 0.5166 ] | max impact: year 2021 Δβ= 0.0989 ( 22.7 %)
[15:24:26] results_loo_year.csv saved
[15:24:26] --- § 13  Descriptive outputs ---
[15:24:26] Descriptive CSVs saved
[15:24:26] --- § 14  Python–R comparison (A/B/C) ---
[15:24:26] Python-R overall classification: B
[15:24:26] Primary classification: B
[15:24:26] W01: primary CI endpoint diff >0.05 ( 0.0567 )
[15:24:26] python_r_reproduction_comparison.csv saved
[15:24:26] results_primary_first_difference.csv saved
[15:24:26] --- § 15  Regression tests T01-T08 ---
[15:24:26] T01 PASS : Normal run: primary CSV created
[15:24:26] T02 PASS : Corrupted file SHA mismatch detected
[15:24:26] T03 PASS : Denominator mismatch detected
[15:24:26] T04 PASS : Duplicate key detected
[15:24:26] T05 PASS : Primary outcome NA detected
[15:24:26] T06 PASS : Missing output prevents COMPLETE status
[15:24:26] T07 PASS : build_summary present_n matches actual file count
[15:24:26] T08 PASS : scene_ge10_pct label free of '現場滞在'
[15:24:26] validation_test_results.csv saved (T07 will be updated after build_summary)
[15:24:26] --- § 16  Figures ---
[15:24:27] figure1_national_trends.pdf saved
[15:24:27] figure2_within_prefecture_change.pdf saved
[15:24:27] figure3_lag_direction.pdf saved
[15:24:27] supp_loo_prefecture.pdf saved
[15:24:27] supp_loo_year.pdf saved
[15:24:27] supp_period_estimates.pdf saved
[15:24:27] supp_triangulation.pdf saved
[15:24:27] session_info.txt + package_versions.csv saved
