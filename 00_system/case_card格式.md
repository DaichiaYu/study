# study｜case card 格式 v0.1

本文件定義如何把課程中的具體場景、直播問答、家庭問題或社會切片整理成 `case_card`。

case card 的目的不是保存完整故事，而是抽出可分析、可查用、可轉化的問題結構。

---

## 一、適用時機

適合做 case card 的資料通常具備以下特徵：

1. 有具體場景。
2. 有角色衝突或需求衝突。
3. 有表面問題與深層機制。
4. 可轉成家庭 playbook 或 NTMY story seed。

例如：

- 孩子作業做不完。
- 長輩過度包辦。
- 孩子偷東西。
- 老師說孩子注意力不集中。
- 青春期孩子回家鎖門。
- 伴侶間因金錢與照顧責任衝突。

---

## 二、檔案命名建議

```text
03_case_bank/<分類>/<case_id>_<簡短主題>.md
```

例：

```text
03_case_bank/學習與作業/case_homework_delay_001_作業做不完.md
03_case_bank/長輩與家庭系統/case_elder_help_001_長輩包辦.md
```

---

## 三、case card 標準格式

```md
# case_id｜案例標題

## 來源

```yaml
metadata:
  source_teacher:
  source_course:
  source_path:
  content_type: case_card
  material_type:
  status: drafted

classification:
  domain_tags: []
  problem_tags: []
  mechanism_tags: []
  child_need_tags: []
  adult_pattern_tags: []
  scenario_tags: []
  age_range: []
  suitable_for: []
```

## 場景摘要

用 3–5 句話概括案例，不搬原文細節。

## 角色結構

- 角色 A：位置、需求、壓力。
- 角色 B：位置、需求、壓力。
- 角色 C：如果有，說明其作用。

## 表面問題

大人或當事人表面上會怎麼描述這個問題？

## 深層機制

這個問題背後可能是什麼機制？

## 真實需求

孩子或當事人真正需要被看見的是什麼？

## 大人常見誤判

大人可能怎麼看錯、幫錯、管錯？

## 看似幫助，實則傷害

列出表面像幫忙，實際可能造成副作用的行為。

## 可用策略

整理可操作的處理方式。

## 注意事項

哪些狀況下不能硬套？有哪些風險？

## 可連結概念卡

- 概念卡一
- 概念卡二

## 是否適合轉成 NTMY story seed

```yaml
ntmy_mapping:
  usable_for_ntmy:
  scenario_type:
  tension_axis: []
  source_forceVector: []
  source_textureTags: []
  target_forceVector_candidates: []
  target_textureTags_candidates: []
  movement_note:
```

## NTMY 可用故事張力

如果適合轉 NTMY，這裡抽出人性張力與選擇困境。
```

---

## 四、整理原則

1. 不原封不動搬案例原文。
2. 不保留過多可識別個資或具體人物細節。
3. 只抽結構：角色、需求、衝突、誤判、機制、策略。
4. 不把單一案例直接當成普遍規律。
5. 不急著轉 NTMY，先判斷是否有足夠抽象張力。
6. 若只有概念沒有具體場景，應整理成 AI digest 或 concept card，不做 case card。

---

## 五、案例分類建議

```text
03_case_bank/
├── 學習與作業/
├── 自驅力與情緒/
├── 德育與邊界/
├── 長輩與家庭系統/
├── 學校與同儕/
└── 親密關係與性教育/
```

---

## 六、版本紀錄

| 版本 | 日期 | 說明 |
|---|---|---|
| v0.1 | 2026-06-27 | 初版。定義 case card 的適用時機、命名方式、標準格式與整理原則。 |
