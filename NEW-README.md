# 專案文件管理 (Docs Repository)

此 Repository 的主要目的是集中管理特定 siteKey (客戶/品牌) 的所有相關開發專案文件。

## 📂 Repo 建立規則

1. **One siteKey, One Repo**：
   一個 siteKey 開立一個專屬的 docs repo。建立 Repo 時，請選擇 `template-docs` 作為模板 (Template) 建立，並將 `template` 替換為實際的 `siteKey` 作為 Repo 名稱。
2. **多專案管理**：
   如果該 siteKey 底下有多個開發專案，請在 Repo 內「分別建立開發專案資料夾」。
   *(資料夾命名規範：專案_{專案名稱} 請自訂清楚的名稱，原則是讓 BD, AM, PM 都能一目了然、清楚辨識專案內容為主，例如：專案_點數雙倍送Campaign)*

## 🔐 權限與協作流程

當 BD 或 AM 建立好 Repo 之後，必須至 GitHub Settings 進行權限設定，分享 **Write** 權限給以下協作團隊：
- Data Team
- Product Team
- Project Team
- Studio Team


## 🚀 專案文件初始化與異動流程

1. 建立完 Repo 後，將其 Clone 到本地端。
2. 在本地端 Repo 內建立新的專案資料夾。
3. 在專案資料夾內建立該專案的references、BRD、PRD、STD 等文件與資料夾。

   客戶 Repo 內的資料夾架構如下：

   ```
   {siteKey}-docs/                           # 客戶專案文件 Repo（根目錄）
   ├── 專案_A/                                # 開發專案資料夾（依實際專案命名）
   │   ├── 專案_A_Reference.md                # 專案參考資料
   │   ├── 專案_A_BRD.md                      # 專案 BRD 文件
   │   ├── 專案_A_PRD.md                      # 專案 PRD 文件
   │   └── 專案_A_STD.md                      # 專案 STD 文件
   ├── skills/                               # AI 協作技能定義（共用，不刪除）
   │   ├── skills_BRD.md                     # BRD SOP
   │   ├── skills_PRD.md                     # PRD SOP
   │   └── skills_STD.md                     # STD SOP
   ├── template/                             # 標準文件範本（共用，不刪除）
   │   ├── template_BRD.md                   # BRD 範本
   │   ├── template_PRD.md                   # PRD 範本
   │   └── template_STD.md                   # STD 範本
   └── README.md                             # 專案 Repo 的說明文件
   ```

4. 開始進行文件的規劃與撰寫。
5. **文件變更的 Issue 流程**：若需更改規格，不建議直接改動文件。應先在系統上開立「Issue」，清楚紀錄「要改哪份文件、改什麼內容、為什麼要改（例如附上會議結論）」並指派給自己。
6. 後續建立新分支（或讓 AI 依照 Issue 建立）去修改，並在送出 PR (Pull Request) 時標註該 Issue，確保每次異動都有跡可循，方可合併回 main。

## 📝 文件產出階段

| **專案進程** | **關鍵文件** | **參與人員** |
| --- | --- | --- |
| 市場開發期 | reference | BD |
| 前置期 | BRD | BD & AM |
| 規劃期 | PRD | AM & PM |
| 開發期 | SDD & STD | PM & EG |


＊詳細專案流程請參考此文件：https://docuguard.aiii.ai/view/U76tmRPsiVOKw1jOMRQb

## 📄 文件建立與 AI 協作規則

1. **文件流程規範 (PRD 產出標準)**：
   釐清並非所有微調都需要寫 PRD。只有當「User Story（使用者故事與流程）發生變動」（例如：在註冊表單新增一個欄位）時，才需要產出或修改 PRD。若只是單純的 Bug 修復、換圖或改文案，則維持現有 Notion 或開 Issue 紀錄即可。
2. **文件編輯原則**：
   相同功能請編輯同一份 BRD、PRD 文件。
3. **拆解 User Story**：
   為了避免 AI 閱讀大篇幅需求時產生幻覺或自行腦補設計規範，建議將 User Story 拆分為更細的單一功能敘述與詳細情境再交給 AI 處理。
4. **以「最新程式碼 (Source Code)」為單一真相來源**：
   過去依賴散落的 Notion 或舊版 PRD，容易導致規格與實際開發脫節。未來在開發新功能或產出新 PRD 時，不應只參考舊有規格書，而應請工程師匯出最新的程式碼，讓 AI 直接讀取最新程式碼來產出或比對新 PRD。
5. **建立 AI 互相驗證的雙重檢核機制**：
   針對難以判斷 AI 讀取程式碼後產出的規格是否正確的問題，建議導入「多模型驗證」機制（如用另一模型交叉比對邏輯是否有衝突）。並請 AI 將驗證結果整理成易於閱讀的 Markdown 或 HTML 格式（甚至搭配畫面截圖），方便人員快速確認。
6. **全域忽略檔案**：請確保在專案初始化時，加入 `.gitignore` 檔案並排除 `.DS_Store` 等作業系統暫存檔，保持版本控管的整潔。
