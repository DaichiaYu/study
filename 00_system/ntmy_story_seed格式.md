# study｜NTMY story seed 格式 v0.1

本文件定義如何把 `study` 倉庫中的教育案例、家庭關係案例、親密關係案例轉成 NTMY 可用的 `story_seed`。

story seed 的目的不是複製原案例，而是抽出可遊戲化的人性張力、選擇困境與反應模式。

---

## 一、適用時機

適合轉成 NTMY story seed 的案例通常具備以下特徵：

1. 有明確選擇困境。
2. 有關係張力或內在衝突。
3. 不只適用於單一家庭教育情境，可抽象到親子、伴侶、師生、職場、同儕或自我成長。
4. 能對應 NTMY 的 `forceVector` / `textureTags`。

例如：

- 被保護到失去自主。
- 被愛包裝的控制。
- 作業裡的親子權力戰。
- 撒謊是自保還是破壞規則。
- 青春期關門後，大人該靠近還是後退。

---

## 二、檔案命名建議

```text
05_ntmy_story_seeds/<分類>/seed_<主題>_<序號>.md
```

例：

```text
05_ntmy_story_seeds/自主與控制/seed_love_vs_control_001.md
05_ntmy_story_seeds/關係邊界/seed_relation_vs_boundary_001.md
```

---

## 三、story seed 標準格式

```md
# seed_id｜故事種子標題

## 來源

```yaml
metadata:
  source_teacher:
  source_course:
  source_path:
  source_case_card:
  content_type: ntmy_story_seed
  material_type:
  status: drafted

classification:
  domain_tags: []
  problem_tags: []
  mechanism_tags: []
  child_need_tags: []
  adult_pattern_tags: []
  scenario_tags: []
  suitable_for: [ntmy_story_seed]
```

## 原型場景

用抽象方式描述原始場景，不搬原文。

## 核心張力

這個故事真正的衝突是什麼？

例：

- 安全 vs 自主
- 愛 vs 控制
- 保護 vs 成長
- 關係 vs 邊界
- 誠實 vs 自保

## 角色結構

- 角色 A：位置與欲望。
- 角色 B：位置與欲望。
- 角色 C：若有，說明其作用。

## 玩家面對的問題

玩家在這個故事裡需要做出什麼選擇？

## 四個選項方向

1. 選項 A：維持關係／接受現狀。
2. 選項 B：切開關係／取回邊界。
3. 選項 C：包裝問題／表面配合。
4. 選項 D：承接並重新定位。

> 注意：四選項方向不是固定答案，只是初稿方向。正式題目仍需依 NTMY 階段一題目規格重寫。

## NTMY 轉譯

```yaml
ntmy_mapping:
  usable_for_ntmy: true
  scenario_type: family | school | peer | romance | self_growth | work | survival
  tension_axis: []

  source_forceVector: []
  source_textureTags: []

  target_options:
    - option_label: A
      forceVector: []
      textureTags: []
      movement_note:
    - option_label: B
      forceVector: []
      textureTags: []
      movement_note:
    - option_label: C
      forceVector: []
      textureTags: []
      movement_note:
    - option_label: D
      forceVector: []
      textureTags: []
      movement_note:
```

## 可變形場景

這個故事種子可以換成哪些場景？

- 親子
- 伴侶
- 師生
- 職場
- 同儕
- 自我成長

## 不可直接使用的部分

哪些原案例元素不能直接拿去遊戲化？

## 後續設計備註

- 可對應哪一組 NTMY 指標？
- 是否適合階段一？
- 是否需要改寫成人際／職場／伴侶場景？
```

---

## 四、整理原則

1. 不搬原案例原句。
2. 不保留可識別人物細節。
3. 不把育兒案例寫成育兒說教。
4. 優先抽出人性張力，而不是教育正解。
5. NTMY 的 `forceVector` / `textureTags` 只使用正式字典，不新增臨時值。
6. `tension_axis` 是故事設計標籤，不等於 NTMY 正式 responseVector。
7. 不把 movementDelta 當成道德分數。

---

## 五、常用 tension_axis 候選

```yaml
tension_axis:
  - safety_vs_autonomy        # 安全感 vs 自主性
  - love_vs_control           # 愛 vs 控制
  - protection_vs_growth      # 保護 vs 成長
  - rule_vs_flexibility       # 規則 vs 彈性
  - obedience_vs_judgment     # 服從 vs 判斷
  - honesty_vs_self_protect   # 誠實 vs 自保
  - relation_vs_boundary      # 關係 vs 邊界
  - effort_vs_meaning         # 努力 vs 意義
  - desire_vs_responsibility  # 慾望 vs 責任
```

若不夠用，先放入 `candidate_tags`，不要直接新增正式 tension_axis。

---

## 六、版本紀錄

| 版本 | 日期 | 說明 |
|---|---|---|
| v0.1 | 2026-06-27 | 初版。定義 NTMY story seed 的適用時機、命名方式、格式與整理原則。 |
