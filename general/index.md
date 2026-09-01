---
okf_version: "0.2"
---

# 專案通用知識庫

此目錄是一個 Open Knowledge Format（OKF）bundle。每份 Markdown 文件代表一個可由人員與 AI agent 共同閱讀、維護及版本控制的知識概念。

## 專案脈絡

* [專案總覽](project-overview.md) - 彙整專案背景、目的、狀態、里程碑與核心知識入口。
* [業務流程](business-flow.md) - 描述核心業務的端到端流程、參與角色與例外處理。
* [客戶資訊](customer-profile.md) - 記錄適合進入版本控制的客戶背景、偏好、要求與合作方式。
* [關係人與對口](stakeholder-map.md) - 整理專案決策者、業務與技術窗口、角色及溝通方式。

## 技術與維運

* [系統架構總覽](architecture.md) - 說明系統元件、資料流、資料模型、外部整合與部署架構。
* [維運手冊](operation-runbook.md) - 提供資料庫、權限、部署、設定、事件與例行維運的操作指引。
* [已知坑與歷史 Bug](bug-knowledge.md) - 保存歷史 Bug、根因、解法、影響範圍與已知注意事項。

## 治理與交接

* [決策紀錄](decision-log.md) - 保存關鍵決策的背景、原因、影響與尚未決議事項。
* [交接清單](handover.md) - 彙整交接對象、未結事項、下一步、負責人與風險。

## 維護原則

- 每份文件只描述一個主要概念；需要更多細節時，以新文件拆分並用 Markdown 連結建立關係。
- `type` 是 concept 唯一必要的 metadata；`title`、`description` 與 `tags` 用於搜尋及導覽。
- 模板尚未填妥前使用 `status: draft`；內容完成並經團隊確認後改為 `status: stable`。
- 不確定來源、驗證者或時效時，不填寫 `sources`、`verified`、`stale_after`，避免製造錯誤的信任訊號。
- 重大知識異動同步記錄於 [更新紀錄](log.md)。

## OKF 參考

- [Google Cloud：Introducing the Open Knowledge Format](https://cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing)
- [Open Knowledge Format v0.2 specification](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md)
