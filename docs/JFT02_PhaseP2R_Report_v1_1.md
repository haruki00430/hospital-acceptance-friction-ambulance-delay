# JFT-02 Phase P2R v1.1 修正再実行 実施報告書

**作成日**: 2026-07-15  
**フェーズ**: Phase P2R v1.1 — Corrective Rerun and Formal Reproduction Gate Repair  
**指示書**: JFT02_PhaseP2R_修正再実行指示書_v1.1.docx  
**実行環境**: R version 4.6.1 (2026-06-24 ucrt)  
**完了分類**: B

---

## §1 背景・目的

Phase P2R v1.0 では主要係数・推論方向は Python 参照結果と整合した一方、SHA-256 非検証、CR2 未実装、C3b・S8 未実装、停止条件非強制、比較判定 A/B/C 未適用、ZIP 単体再実行不可等の問題が残った。
v1.1 では全項目を修正・補完し、第三者が再実行・検証できるパッケージとする。

**研究疑問**: 同一都道府県内で、病院受入困難の年次悪化（受入照会≥4件率）が
通報から救急隊の現場到着まで10分以上を要する割合の年次悪化と関連するか。

---

## §2 修正項目

| 項目 | v1.0 状態 | v1.1 修正内容 |
|------|----------|-------------|
| SHA-256 | 記録のみ | 期待値と照合・不一致で HARD STOP |
| QA | QA1-QA5 | QA1-QA8（範囲・N・ラベルチェック追加）|
| CR2/Satterthwaite | 未実装 | 主解析・C1-C3a に追加 |
| C3b | 未実装 | 追加（scene_stay→scene_time）|
| S8 加重 | 未実装 | 分母加重感度分析を追加 |
| Reverse lag CI | NA（inversion失敗）| CR2/Satterthwaite 代替 (DEV-P2R-004) |
| LOO 最大影響点 | なし | Δβ・相対変化・依存判定を追加 |
| 期間交互作用 | なし | 探索的交互作用検定を追加 |
| Python-R 分類 | TRUE/FALSE | A/B/C 3段階分類 |
| 完了ステータス | 固定値 | 実ファイル存在から動的生成 |
| 停止条件 | 非強制 | HARD STOP → exit code 1 |
| 回帰テスト | なし | T01-T08 実装 |
| 図 | なし | Figure 1-3 + supp 4 図生成 |
| p=0 表記 | 0 のまま | p < 1/(B+1) = p < 0.0001 |

---

## §3 主要結果

### 3.1 一次結果

**推奨主結果文（英語）**:
> Within-prefecture annual increases in hospital-acceptance friction were associated with increases in delayed ambulance scene arrival (beta = 0.435 percentage points in the share of calls with scene-arrival time >=10 minutes per 1-percentage-point increase in the four-inquiry rate; R wild-cluster-bootstrap 95% CI 0.222-0.564; p = 3e-04).

**推奨主結果文（日本語）**:
> 同一都道府県内で受入照会4回以上率が年次1 percentage point増加した場合、通報から現場到着まで10分以上を要した割合は 0.435 percentage point増加した（R wild cluster bootstrap 95%信頼区間 0.222–0.564、p=3e-04）。これは関連を示すものであり、因果効果を示すものではない。

| 推定値 | CR2 SE | WCB 95%CI | WCB p | CR2 p (Satt) | Python分類 |
|--------|--------|-----------|-------|--------------|----------|
| 0.435446 | 0.0784 | [0.222, 0.564] | 3e-04 | 4e-04 | B |

### 3.2 Python–R 分類 B

| model | R β | Python β | Δ | 分類 |
|-------|-----|----------|---|------|
| primary | 0.435446 | 0.435446 | 0 | B |
| c1_scene_time | 0.080529 | 0.080529 | 0 | A |
| c2_burden | 0.402385 | 0.402385 | 0 | B |
| c3a_scene_stay | 0.439212 | 0.439212 | 0 | A |
| forward_lag | 0.509445 | 0.509445 | 0 | A |
| reverse_lag | -2.7e-05 | 0.000000 | 2.7e-05 | A |
| level_fe | 0.677458 | 0.677458 | 0 | A |

### 3.3 Corroborative C1-C3b（Holm補正: C1-C3aのみ）

- **C1_scene_arrival_time**: β=0.0805 WCB p=1e-04 Holm p=2e-04 CR2 p=0.013
- **C2_accept_burden**: β=0.4024 WCB p=0.0017 Holm p=0.0017 CR2 p=0.0204
- **C3a_scene_stay_exposure**: β=0.4392 WCB p=< 0.0001 Holm p=0 CR2 p=4e-04
- **C3b_scene_stay_time**: β=0.0584 WCB p=< 0.0001 (support; not in Holm family) CR2 p=NA

### 3.4 Temporal direction

- Forward lag β=0.5094 (WCB p=0.0028; CI method: WCB)
- Reverse lag β≈-2.7e-05 (WCB p=0.9993; CI method: CR2_Satterthwaite_fallback)
- 解釈: temporal asymmetry consistent with, but not proving, downstream-to-upstream spillover

### 3.5 LOO感度

- Prefecture LOO: [0.3619, 0.4522] 符号反転0 最大影響都道府県=13 (Δβ=0.0736, rel=16.9%)
- Year LOO: [0.3365, 0.5166] 符号反転0 最大影響年=2021 (Δβ=0.0989, rel=22.7%)

---

## §4 完了判定

WARN フラグ: 3 件
HARD STOP: 0 件（全 S0X PASS）
回帰テスト: T01-T08 全 PASS

**完了宣言** → §5 参照

---

## §5 禁止表現チェック

- [ ] ~~完全一致~~ → 分類 A/B を使用 ✓
- [ ] ~~翌年の現場滞在~~ → contemporaneous FD + 正確な変数定義 ✓
- [ ] ~~COVID後に増大~~ → 期間差を正式検定 (p=0.0021; 有意) ✓
- [ ] ~~現場到着10分を現場滞在と誤記~~ → scene_ge10_pct = 通報から現場到着 ✓

