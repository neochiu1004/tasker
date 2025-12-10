Command Center V3 - 雲端互助與任務管理系統

這是一個基於 Web 的單頁應用程式 (Single Page Application)，整合了 任務追蹤 (Tracker)、倒數計時器 (Timer) 以及 互助簽到面板 (Mutual Relay)。

V3 版本引入了 Firebase 雲端同步功能，並針對手機操作（特別是 iOS 捷徑自動化）進行了深度優化，實現「一鍵分享、自動分流、無縫同步」。

✨ 主要功能

1. ☁️ 雲端同步 (Cloud Sync)

空間代碼 (Space ID)：透過輸入自訂的 ID (例如 group-111) 即可登入。

跨裝置：在手機、電腦輸入相同 ID，資料即時同步。

自動登入：支援透過網址參數自動登入，無需每次輸入。

2. 📝 任務追蹤 (Tasks)

自動儲存：透過捷徑或貼上新增時，直接寫入雲端，無需額外確認。

智慧重複處理：

若新增的任務名稱已存在，系統會詢問是否「覆蓋舊連結」或「建立新任務」。

捷徑分享時若名稱重複，會自動更新連結。

一鍵清除連結：任務右側新增「斷開連結」按鈕，快速清空網址但保留任務。

排程開啟：可設定時間 (24h)，時間到時自動開啟網址 (需允許彈出視窗)。

3. 🤝 互助面板 (Mutual Relay)

智慧分流 (Smart Routing)：

當捷徑分享進來時，系統會自動比對標題。

若標題是「互助名單」中的人名 (如 "爸爸")，會直接更新該成員的連結，而不是建立新任務。

智慧貼上：貼上含雜訊的文字 (如 LINE 宣傳文) 時，自動擷取 https:// 網址，過濾其餘文字。

一鍵清除：成員欄位旁新增紅色垃圾桶，一鍵清空該成員網址。

歷程紀錄：點擊下方小按鈕可記錄今日已幫助過的人員。

4. ⏱️ 計時器 (Timer)

視覺化倒數進度條。

支援全域緩衝時間 (Delay Buffer) 設定。

📱 iOS 捷徑設定教學 (自動化神器)

為了發揮此系統的最大效能，建議在 iPhone 上建立專屬捷徑。

捷徑功能：

在 Safari 瀏覽網頁時，點擊分享，直接將網址傳送到 Command Center。

若標題是互助成員 -> 自動更新該成員連結。

若標題是新任務 -> 自動新增到待辦清單。

全程自動登入並儲存，無需手動操作。

設定步驟：

開啟 iPhone 「捷徑 (Shortcuts)」 App。

建立新捷徑，命名為 「加到 Command Center」。

設定接收輸入：Safari 網頁 或 URL (在分享表單中顯示)。

加入動作：「URL 編碼」 (對網址進行編碼)。

加入動作：「URL 編碼」 (對網頁名稱進行編碼)。

加入動作：「URL」，填入以下格式：

[https://您的網址.com/?space_id=您的空間代碼&share_url=](https://您的網址.com/?space_id=您的空間代碼&share_url=)[編碼後的URL]&share_title=[編碼後的名稱]


space_id：請填入您想固定的空間號碼 (例如 85)。

share_url：選擇剛剛編碼過的網址變數。

share_title：選擇剛剛編碼過的名稱變數。

加入動作：「打開 URL」。

💻 網頁操作指南

登入

首次進入請輸入 Space ID。

若使用上述捷徑連結進入，系統會自動登入。

任務列表 (Tracker)

新增：點擊右下角 + 按鈕 (若隱藏可透過貼上觸發)。

多選刪除：點擊「SELECT」進入多選模式。

清除連結：點擊任務右側的紅色「斷開連結」圖示。

互助面板 (Mutual)

設定名單：點擊右上角 ⚙️ 設定按鈕，一行一個名字。

貼上連結：直接在成員欄位貼上，或點擊貼上按鈕 (自動過濾文字)。

重置：點擊右上角重置按鈕，可清空今日簽到紀錄。

🛠️ 技術細節

Frontend: 原生 HTML5, Tailwind CSS (CDN), Lucide Icons.

Backend: Google Firebase (Firestore Database, Auth).

Database Structure:

Public Path: artifacts/my-ticket-app/public/data/

Collections:

{SpaceID}_cmd_tasks: 儲存待辦任務。

{SpaceID}_cmd_timers: 儲存計時器。

Document {SpaceID}_mutual/config: 儲存互助名單與狀態。

⚠️ 注意事項

由於使用免費版 Firebase 配額，請勿濫用寫入頻率。

自動開啟網頁功能需在瀏覽器設定中允許「彈出式視窗 (Pop-ups)」。
