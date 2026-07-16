# JFT-02 Phase P2R v1.1 Deviation Log

**作成日**: 2026-07-15

本ファイルは修正再実行指示書 v1.1 からの逸脱・警告を記録する。

---

## HARD STOPフラグ

(発火なし — 全 S0X 通過)

## WARNフラグ

### W01: CI 端点差 > 0.05

[15:24:26] W01: primary CI endpoint diff >0.05 ( 0.0567 )

### W03: Reverse lag WCB CI inversion 失敗 → CR2/Satterthwaite 代替

- **DEV-P2R-004**: Reverse lag (seed=20260720) boottest CI inversion が収束しない（β≈0 近傍の既知挙動）
- 対応: 指示書 §6.2 に従い CR2/Satterthwaite 95%CI を代替として使用
- Figure 3 では forward/reverse 双方を CR2 95%CI で統一表示（WCB p 別記）
- WCB p 値 (p≈1.0) は保持

## Python–R 分類

| model | classification |
|-------|---------------|
| primary | B |
| c1_scene_time | A |
| c2_burden | B |
| c3a_scene_stay | A |
| forward_lag | A |
| reverse_lag | A |
| level_fe | A |

**総合分類: B**

## p=0 表記修正

- C3a WCB p: fwildclusterboot が 0 を返す場合、B=9999 に対し p < 1/(B+1) = p < 0.0001 と解釈
- wcb_p_display 列に 'p < 0.0001' を使用

## build_summary present_n

- 記録上の self-reference artifact (build_summary/logs 自身が書込み前にカウントされた) は v1.1 では解消済み
- build_summary は全出力ファイル書込み後に最後に生成

