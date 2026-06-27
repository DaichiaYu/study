# study｜AI digest 格式 v0.1

本文件定義逐字稿、PDF、工具表或補充資料整理成 `AI digest` 時的固定格式。

AI digest 的目的不是寫讀書心得，而是把原始資料壓縮成 AI 後續可以穩定調用的知識結構。

---

## 一、適用時機

適合做 AI digest 的資料通常具備以下特徵：

1. 有明確核心觀念。
2. 可支撐後續判斷或行動。
3. 可能被反覆引用。
4. 不是單一案例，而是可以泛化成方法、原則或框架。

例如：

- 家衛｜壓力系統概述
- 家衛｜清單、計畫、作業、復習
- 沈奕斐｜鬆弛父母先導課
- 沈奕斐｜規矩、表揚、主動學習

---

## 二、檔案命名建議

```text
01_ai_digest/<來源老師>/<課程>/<原檔序號或主題>.md
```

例：

```text
01_ai_digest/家衛/自驅力/01-壓力系統概述.md
01_ai_digest/沈奕斐/鬆弛父母/001-先導課-認知篇.md
```

---

## 三、AI digest 標準格式

```md
# 標題

## 來源

```yaml
metadata:
  source_teacher:
  source_course:
  source_path:
  content_type: ai_digest
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

## 一句話定位

用一句話說明這篇資料在整個倉庫中的用途。

## 核心命題

這篇真正想解決的問題是什麼？

## 關鍵概念

- 概念一：定義與作用。
- 概念二：定義與作用。
- 概念三：定義與作用。

## 推理脈絡

整理作者如何從問題推到結論。

## 操作原則

這篇可以轉成哪些具體做法？

## 看似幫助，實則傷害

如果這篇有指出常見誤區，在這裡列出。

## 適用情境

這篇適合用在哪些情境？

## 不適用／容易誤解

避免 AI 或人類把這篇用歪。

## 可抽出的概念卡

- 概念卡候選一
- 概念卡候選二

## 可抽出的案例卡

- 案例卡候選一
- 案例卡候選二

## 可轉為 NTMY story seed 的元素

這篇是否有可抽象化的人性張力、關係困境或選擇困境。

## 後續處理建議

- 是否需要整理 concept card
- 是否需要整理 case card
- 是否需要進 playbook
- 是否適合轉 NTMY seed
```

---

## 四、整理原則

1. 不要長篇複述原文。
2. 不要把作者所有例子都搬進 digest。
3. 優先抽出可重複調用的概念與操作框架。
4. 明確標出容易誤解的地方。
5. 若只是單一場景，不必硬做 digest，可轉 case_card。
6. 若還不確定標籤，先放 `candidate_tags`，不要新增正式標籤。

---

## 五、版本紀錄

| 版本 | 日期 | 說明 |
|---|---|---|
| v0.1 | 2026-06-27 | 初版。定義 AI digest 的適用時機、命名方式與標準格式。 |
