# 學思軒專案密碼安全防護準則 (Password & Credential Security Guidelines)

本準則適用於學思軒國語文練習神器全系列網頁、整合平台及教師管理後台：

## 1. 嚴禁在前端原始碼中存放明文密碼 (No Plaintext Passwords in Source Code)
- 嚴格禁止在 HTML / JavaScript 原始碼中直接撰寫或比對明文密碼（如 `if (password === "221313")`）。
- 防止學生透過「檢視網頁原始碼」或按 `F12` 開發者工具搜尋取得管理密碼。

## 2. 強制採用單向加密雜湊比對 (Enforce SHA-256 Cryptographic Hash Verification)
- 所有管理密碼比對必須採用 Web Crypto API 進行 SHA-256 雜湊比對。
- 原始碼中僅存放不可逆的 SHA-256 雜湊值（特徵碼），確保即使原始碼公開亦無法被反向推算破解。

## 3. 密碼輸入介面強制遮罩 (Masked Password Inputs)
- 禁止使用 `window.prompt()` 明文對話框。
- 必須使用專屬彈窗搭配 `<input type="password">`（星號 / 圓點遮罩）以確保輸入安全。
