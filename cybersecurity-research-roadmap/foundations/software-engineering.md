# 軟體工程

[計算機網路](computer-networking.md) · [共同基礎](../02-CORE-FOUNDATIONS.md) · [程式](programming.md)

學習類型：程式與研究技能。這裡只留研究會反覆用到的工程習慣。完整的安全開發生命週期在 [模組 14](../modules/14-secure-software-engineering-and-supply-chain.md)，不要提前把供應鏈工具學完。

## 現在要會的

| 主題 | 深度 | 重要性 | 原因 |
|---|---|---|---|
| Git 與實驗版本 | L1 | REQUIRED | 你已會基本 Git；補的是「這個結果來自哪一次提交」 |
| 讀陌生程式 | L1 | REQUIRED | 方法見 [程式](programming.md) |
| 測試 | L1 | REQUIRED | 一個小測試保護你的分析腳本不被自己改壞 |
| 介面與模組邊界 | L1 | RECOMMENDED | 信任邊界常常就是介面 |
| 錯誤處理 | L1 | REQUIRED | 安全缺陷常出現在失敗路徑 |
| 建置可重現 | L0 | RECOMMENDED | 記錄編譯器、系統與指令；完整可重現建置是模組 14 |
| 程式架構風格 | L0 | OPTIONAL | 能畫分層即可 |

## 研究工程的最低標準

每次實驗記錄：

- 程式版本或提交識別碼
- 輸入資料的來源與使用條款
- 指令與重要參數
- 工具版本
- 你手動改過的步驟

這是可重現性的工程部分，定義見 [詞彙](../GLOSSARY.md)。

## 讀程式時的安全問題

不要先找漏洞。先回答：輸入從哪進來、哪裡檢查長度與權限、失敗時回傳什麼、秘密放在哪裡。這些問題對 Web、系統與協定實作都適用。

## 練習

把 [初學專題](../projects/beginner-projects.md) 的第一個腳本放進 Git，寫一個測試固定一小段輸入的輸出，並在 README 裡記錄如何重跑。測試失敗時先修腳本，不要改測試去配合錯誤結果，除非你發現測試本身問錯了問題並寫下原因。

## 可延後

CI 平台的完整安全、簽章、依賴掃描工具、微服務架構。它們在模組 14 的 Stage 2 之後才需要。

---

[程式](programming.md) · [模組 14](../modules/14-secure-software-engineering-and-supply-chain.md) · [學習法](../03-LEARNING-METHODOLOGY.md)
