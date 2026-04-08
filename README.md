# 研究顧問 Agent

一個專為「資料科學與機器學習」課程設計的 VS Code Copilot 自訂 Agent，協助學生完成期末研究提案。

## 功能

以批判性但建設性的顧問視角，引導學生逐步完成提案四大主軸：

| 主軸 | 內容 |
|------|------|
| 研究關鍵字（Keywords） | 依任務類型、方法論、應用領域分組，提供 5~10 個英文關鍵字 |
| 背景介紹（Background） | 問題重要性、現有方案、現有方案的不足 |
| 研究困境（Research Challenges） | 至少 3 個技術挑戰，說明「為什麼難」 |
| 資料集與收集方式（Datasets） | 公開資料集推薦或自行收集方式 |

## 互動流程

1. **開場問診** — 先釐清研究方向與清晰程度，再進入主軸
2. **逐項引導** — 每完成一個主軸，確認學生滿意後才進入下一項
3. **提案摘要** — 四項全部確認後，輸出完整提案摘要

## 使用方式

1. 在 VS Code Copilot Chat 中開啟 Agent 選單
2. 選擇 `研究顧問`
3. 描述你的研究方向或問題，顧問會開始引導

## 工具權限

| 工具 | 用途 | 需確認 |
|------|------|--------|
| `web` | 查詢學術論文、資料集 | 否 |
| `search` | 搜尋工作區 | 否 |
| `read` | 讀取檔案 | 否 |
| `edit` | 寫入提案內容 | ✅ 需確認 |
| `agent` | 呼叫其他 Agent | ✅ 需確認 |

## 檔案結構

```
.github/
├── agents/
│   └── consultant.agent.md   # 顧問 Agent 定義
└── skills/ (#來源:https://github.com/heilcheng/awesome-agent-skills/blob/main/README.zh-TW.md)
    ├── deep-research/        # 深度研究 Skill
    └── fact-checker/         # 事實查核 Skill
```
