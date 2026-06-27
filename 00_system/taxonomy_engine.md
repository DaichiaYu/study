# study｜Taxonomy Engine 標籤演算法與治理架構 v0.1

本文件定義 `study` 倉庫的標籤治理流程，負責處理候選標籤、正式標籤、別名映射與批次收斂。

本文件不是新的標籤清單。正式標籤清單以 `00_system/標籤系統.md` 為準；本文件只規定標籤如何產生、暫存、映射、合併與升級。

---

## 一、核心定位

`study` 倉庫會持續產生：

- AI digest
- concept card
- case card
- family playbook
- NTMY story seed

如果每整理一篇資料就直接新增正式標籤，標籤系統會快速膨脹。因此需要一個中介流程：

```text
原文解析
→ candidate_tags 暫存
→ active_tags 對照
→ alias_map 映射
→ batch review 批次收斂
→ 回寫正式標籤或保留候選
```

---

## 二、治理原則

### 1. 解耦 Decoupling

原始內容、AI digest、正式標籤三者分開管理。

- 原始逐字稿只保留資料。
- AI digest 可記錄暫時理解與候選標籤。
- 正式標籤只由 `00_system/標籤系統.md` 管理。

### 2. 延遲綁定 Late Binding

整理初期可以使用 `candidate_tags`，不必強行映射到既有正式標籤。

目的：

- 避免太早合併，抹平重要差異。
- 避免太早新增，造成標籤膨脹。

### 3. 映射 Mapping

不同 AI 或不同整理階段可能產生類似標籤。這些不應全部成為正式標籤，而應透過 `alias_map` 指向正式標籤。

### 4. 單一正式來源 Single Source of Truth

正式標籤以 `00_system/標籤系統.md` 為準。

`taxonomy_engine.md` 只管理：

- alias_map
- candidate_tags
- deprecated_tags
- batch review rules

---

## 三、candidate_tags 格式

若遇到現有正式標籤無法穩定表達的新概念，先放入候選。

```yaml
candidate_tags:
  - name:
    layer: domain | problem | mechanism | child_need | adult_pattern | scenario | tension_axis
    reason:
    evidence:
    possible_alias:
    source_path:
```

使用原則：

- `reason` 說明為什麼既有標籤不夠。
- `evidence` 簡述文本依據。
- `possible_alias` 若疑似只是舊標籤別名，先填可能對應。
- 不可把候選標籤直接當正式標籤長期使用。

---

## 四、alias_map 初版

此處只紀錄常見別名對應，不取代正式標籤系統。

```yaml
alias_map:
  mechanism_tags:
    over_worry: adult_anxiety_projection
    anxious_transfer: adult_anxiety_projection
    parent_anxiety_too_much: adult_anxiety_projection
    helicopter_parenting: over_protection
    helicopter_helping: over_protection
    over_helping: over_protection
    too_much_correction: over_correction
    instant_correction: over_correction
    no_control_feeling: loss_of_control
    lack_of_control: loss_of_control
    toxic_stress: toxic_pressure

  adult_pattern_tags:
    helicopter_parenting: helicopter_help
    anxious_parenting: anxious_planning
    emotional_threat: emotional_blackmail
    parent_over_teaching: over_teaching
    elder_spoiling: elder_good_intention_damage

  child_need_tags:
    control_need: autonomy
    need_to_feel_capable: competence
    need_structure: structure
    need_to_be_seen: recognition
```

---

## 五、處理流程

### Step 1：解析 Extraction

整理原始資料時，先抽出：

- 核心命題
- 關鍵概念
- 表面問題
- 深層機制
- 孩子／當事人需求
- 大人常見誤判
- 可轉案例或故事種子的元素

若可直接對應正式標籤，使用正式標籤。若不確定，放入 `candidate_tags`。

### Step 2：初步驗證 Validation

整理單篇資料時，AI 應先檢查：

1. 這個概念是否已存在於正式標籤？
2. 是否只是既有標籤的同義詞？
3. 是否只是情境、角色或語氣，不應升級為機制？
4. 是否會影響 playbook、case card 或 NTMY story seed？

### Step 3：批次收斂 Batch Review

每整理 5–10 篇 AI digest 或 5 張 case card 後，進行一次候選標籤批次檢查。

流程：

```text
candidate_tags
→ 合併同義詞
→ 映射到 active tags
→ 決定是否新增正式標籤
→ 更新 alias_map
→ 回寫受影響檔案
```

---

## 六、新增正式標籤條件

候選標籤必須符合以下條件之一，才可升級為正式標籤：

1. 既有標籤無法表達此教育、家庭或關係機制。
2. 此標籤會影響後續 playbook 建議或案例判斷。
3. 此標籤至少預期服務 3 篇以上資料或案例。
4. 雖然少見，但對 NTMY story seed 或家庭決策非常關鍵。
5. 不新增會導致重要差異被錯誤合併。

不符合者應合併到既有正式標籤，或作為 alias_map 保留。

---

## 七、禁止事項

- 不得在單篇 digest 中直接新增正式標籤。
- 不得把情境標籤升級成機制標籤。
- 不得把人物角色升級成機制標籤。
- 不得因語氣不同新增標籤。
- 不得把 NTMY 的 `forceVector` / `textureTags` 和 study 的 classification 混用。
- 不得把候選標籤永久堆在檔案裡不收斂。
- 不得在本文件建立一套與 `標籤系統.md` 競爭的正式標籤字典。

---

## 八、AI 工作指令

後續整理任一資料時，AI 應遵循以下流程：

1. 先依 `digest格式.md`、`case_card格式.md` 或 `ntmy_story_seed格式.md` 產出內容。
2. 標籤優先使用 `標籤系統.md` 的正式標籤。
3. 若無法確定，使用 `candidate_tags`，並寫明 `reason` 與 `possible_alias`。
4. 不自行新增正式標籤。
5. 每 5–10 篇或使用者要求時，進行一次候選標籤批次對齊。
6. 只有在使用者要求「標籤對齊」或「批次收斂」時，才更新正式標籤與 alias_map。

---

## 九、批次收斂輸出格式

```md
# taxonomy batch review YYYY-MM-DD

## 本次檢查範圍

- 檔案一
- 檔案二

## candidate_tags 彙整

| candidate | layer | 出現次數 | 來源 | 建議處理 |
|---|---|---:|---|---|

## 建議新增正式標籤

| tag | layer | 理由 | 影響範圍 |
|---|---|---|---|

## 建議 alias_map 更新

```yaml
alias_map:
  mechanism_tags:
    over_worry: adult_anxiety_projection
```

## 需要回寫的檔案

- file_path：candidate → active
```

---

## 十、與 NTMY 的關係

`taxonomy_engine.md` 不管理 NTMY 正式 responseVector。

NTMY 的正式 forceVector / textureTags 以 NTMY 專案文件為準。study 倉庫只在 `ntmy_story_seed` 中做轉譯，不在一般 AI digest 或 case card 中強制標 NTMY vector。

處理流程：

```text
case_card
→ 抽象出 tension_axis
→ 判斷 source_forceVector / source_textureTags
→ 設計 target options
→ 另存為 ntmy_story_seed
```

---

## 十一、版本紀錄

| 版本 | 日期 | 說明 |
|---|---|---|
| v0.1 | 2026-06-27 | 初版。建立延遲綁定、alias_map、candidate_tags、批次收斂與 AI 工作指令。 |
