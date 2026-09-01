---
type: Playbook
title: 維運手冊
description: 提供資料庫、權限、部署、設定、事件與例行維運的操作指引。
tags: [operations, runbook, incident]
status: draft
---

# 維運手冊 (Operation Runbook)

> 維運手冊。PM 不只是管理開發，還要知道系統出事情時怎麼辦。

## 1. Database

> 資料庫維運指引。

### 1.1 如何查資料？

### 1.2 哪些資料可以查？

### 1.3 哪些情況需要修改 DB？

### 1.4 誰可以操作？

### 1.5 修改前後需要注意什麼？

## 2. Permission

> 權限管理指引。

### 2.1 如何新增 User？

### 2.2 如何調整 Role？

### 2.3 權限問題怎麼查？

## 3. Deployment

> 部署與發佈流程。

### 3.1 如何上版？

### 3.2 UAT → Production 流程？

### 3.3 誰負責？

### 3.4 上版前確認什麼？

## 4. Configuration

> 設定管理。需明確區分哪些由後台控制、哪些需工程師修改。

### 4.1 哪些設定由後台控制？

### 4.2 哪些設定需要工程師修改？

### 4.3 哪些設定改了會影響 Production？

## 5. Incident

> 事件應變流程。

### 5.1 發生問題第一步找誰？

### 5.2 如何判斷是 Backend / Frontend / Infra？

### 5.3 客戶需要怎麼通知？

## 6. 例行維運作業

## 7. 監控與告警

## 8. 備份與復原

## 9. 環境資訊

## 10. 相關知識

- [系統架構總覽](./architecture.md)
- [已知坑與歷史 Bug](./bug-knowledge.md)
- [關係人與對口](./stakeholder-map.md)
- [交接清單](./handover.md)
