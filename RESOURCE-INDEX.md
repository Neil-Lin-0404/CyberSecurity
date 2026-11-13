# 資源索引

[詞彙](GLOSSARY.md) · [地圖](README.md) · [進度](PROGRESS-TRACKER.md)

最後檢閱日：2026-11-13。

各模組只保留 3–5 項入門資源。本頁集中登錄，並說明從哪裡開始。語言以頁面實際語言為準；未特別註明者為英文。費用會變動，以網站當下說明為準。

狀態：已核對表示本輪建置時開啟過官方頁面或出版記錄。未驗證表示寫入時無法確認，不要當成已確認來源。

## 如何使用一份資源

先讀模組指定的起始章節或實驗，做完一個小觀察，再決定要不要往下。不要同時開三本同主題教科書。

## 網路與系統

| 資源 | 類型 | 程度 | 費用 | 語言 | 從哪裡開始 | 狀態 |
|---|---|---|---|---|---|---|
| [Kurose and Ross, Computer Networking: A Top-Down Approach, 第 9 版](https://gaia.cs.umass.edu/kurose_ross/) | 教科書 | 入門到中階 | 付費；作者站有部分教材 | 英文 | 作者站的章節結構；先應用層再往下，安全章後讀 | 已核對。Pearson 頁記載 2025-06 前後出版 |
| [Stanford CS144](https://web.stanford.edu/class/cs144/) | 大學課程 | 中階 | 課程頁公開，作業政策依該季 | 英文 | 當季頁面的實驗 0 與 TCP 相關實驗說明 | 已核對入口 |
| [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/) | 程式教學 | 入門 | 免費 | 英文 | 客戶端—伺服器與 `getaddrinfo` 章 | 已核對入口 |
| [Wireshark 文件](https://www.wireshark.org/docs/) | 官方文件 | 入門 | 免費 | 英文 | 使用者指南的擷取與顯示過濾器 | 已核對入口 |
| [RFC Editor](https://www.rfc-editor.org/) | 規格 | 依 RFC 而定 | 免費 | 英文 | 只讀目前目標那一份，並先看 Security Considerations | 已核對入口 |
| [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/) | 教科書 | 入門到中階 | 免費線上版 | 英文 | 虛擬化部分的行程與位址空間 | 已核對入口 |
| [MIT 6.1810 與 xv6](https://pdos.csail.mit.edu/6.1810/) | 課程與教學系統 | 中階 | 免費 | 英文 | xv6 書第 1 章與對應原始碼；原始碼在 [mit-pdos/xv6-riscv](https://github.com/mit-pdos/xv6-riscv) | 已核對。書為 Cox、Kaashoek、Morris |

Kurose 與 Ross 適合建立分層直覺。CS144 適合在你需要實作傳輸行為時再做，不是網路安全的前置門檻。OSTEP 先於 xv6：先有概念，再讀教學核心。

## 密碼

| 資源 | 類型 | 程度 | 費用 | 從哪裡開始 | 狀態 |
|---|---|---|---|---|---|
| [Dan Boneh 線上密碼課](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/) | 課程 | 入門到中階 | 頁面所列材料免費；若連到平台課程，費用依平台 | 課程大綱中的對稱加密與完整性 | 已核對入口 |
| [Boneh and Shoup, A Graduate Course in Applied Cryptography](https://toc.cryptobook.us/) | 教科書 | 研究所 | 免費線上版 | 目錄中的導論與對稱加密；安全定義先於演算法細節 | 已核對入口 |
| [CryptoHack](https://cryptohack.org/) | 練習 | 入門到中階 | 免費 | 介紹課程；只在本機或站內環境作答 | 已核對入口 |

## Web 與應用

| 資源 | 類型 | 程度 | 費用 | 從哪裡開始 | 狀態 |
|---|---|---|---|---|---|
| [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) | 測試指南 | 中階 | 免費 | 測試框架與授權範圍那一節，再選一個你自己的應用會用到的控制 | 已核對入口 |
| [OWASP ASVS](https://asvs.owasp.org/) | 驗證標準 | 中階 | 免費 | 第一級的鑑別與存取控制 | 已核對入口 |
| [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/) | 實務摘要 | 入門 | 免費 | 與你目前缺陷類型對應的單頁，不要一次讀完 | 已核對入口 |
| [PortSwigger Web Security Academy](https://portswigger.net/web-security) | 教育實驗 | 入門到中階 | 實驗免費 | 各主題的概念頁；只使用學院提供的實驗 | 已核對入口 |

## 鑑識與事件回應

| 資源 | 類型 | 程度 | 費用 | 從哪裡開始 | 狀態 |
|---|---|---|---|---|---|
| [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final) | 標準指引 | 中階 | 免費 | 目的與範圍。DOI：`10.6028/NIST.SP.800-61r3`。2025-04 定稿，取代 Rev. 2。它是 CSF 2.0 社群輪廓，不是逐步操作手冊 | 已核對 |
| [NIST CFTT](https://www.nist.gov/itl/ssd/software-quality-group/computer-forensics-tool-testing-program-cftt) | 工具測試計畫 | 中階 | 免費 | 計畫如何描述工具測試，而不是把報告當成工具教學 | 已核對入口 |
| [NIST CFReDS](https://cfreds.nist.gov/) | 參考資料集 | 中階 | 免費，遵守資料集條款 | 選一個文件說明完整的映像或情境 | 已核對入口 |
| [Autopsy](https://www.autopsy.com/) | 工具文件 | 入門 | 有免費版本；進階功能依廠商 | 官方文件的案件與檔案系統瀏覽；只用授權映像 | 已核對入口 |
| [NIST 事件回應專案頁](https://csrc.nist.gov/projects/incident-response) | 專案入口 | 中階 | 免費 | 與 SP 800-61r3 一併看的補充材料 | 已核對入口 |

## 情資、AI 與雲端

| 資源 | 類型 | 費用 | 從哪裡開始 | 狀態 |
|---|---|---|---|---|
| [MITRE ATT&CK](https://attack.mitre.org/) | 知識庫 | 免費 | 先讀 ATT&CK 是什麼。它記錄觀察到的戰術與技術，不是完整方法論，也不能代替研究設計 | 已核對入口 |
| [MITRE ATLAS](https://atlas.mitre.org/) | AI 威脅知識庫 | 免費 | 矩陣總覽與案例研究的使用限制 | 已核對入口 |
| [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) | 風險框架 | 免費 | AI RMF 1.0（AI 100-1，2023）與 2024-07 的生成式 AI 輪廓 AI 600-1。頁面說明框架正在修訂，引用時寫版本 | 已核對 |
| [OWASP GenAI LLM Top 10](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) | 社群風險清單 | 免費 | 先確認你讀的是 2025 定稿還是 2026 版本。2026 資源頁存在；若下載檔仍標出版日期未定，就不要把它寫成最終標準 | 已核對有版本差異 |
| [Kubernetes 安全概念](https://kubernetes.io/docs/concepts/security/) | 官方文件 | 免費 | 控制平面、Secret、網路政策與稽核 | 已核對 |
| [AWS 安全文件](https://docs.aws.amazon.com/security/) | 官方文件 | 文件免費，服務付費 | 共同責任模型 | 已核對 |
| [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) | 設定基準 | 非商業 PDF 通常可免費取得；掃描產品另計 | 與你實際使用的系統對應的那一份，先讀範圍與適用版本 | 已核對入口 |

## 逆向、硬體與形式方法

| 資源 | 類型 | 費用 | 從哪裡開始 | 狀態 |
|---|---|---|---|---|
| [Ghidra](https://github.com/NationalSecurityAgency/ghidra) | 逆向工具 | 免費 | 官方說明的安裝與對一個你自己編譯的二進位做反組譯 | 已核對入口 |
| [OpenTitan 文件](https://opentitan.org/documentation/) | 硬體信任根 | 免費 | 文件首頁的專案簡介與生命週期；不要從暫存器全集開始 | 已核對入口 |
| [TLA+ 文件](https://docs.tlapl.us/) | 規格語言 | 免費 | HourClock 範例 | 已核對 |
| [Lamport, Specifying Systems](https://lamport.org/tla/book.html) | 教科書 | 作者提供下載 | 只讀 Part I 前幾章，直到你能寫一個小規格 | 已核對 |
| [Alloy](https://alloytools.org/) | 模型語言與分析器 | 免費 | Alloy 6 的語言變更說明與小模型 | 已核對。2025 年初頁面所列版本為 6.2.0 |
| [Software Foundations](https://softwarefoundations.cis.upenn.edu/) | 證明輔助教科書 | 免費 | Logical Foundations 的前言與第一個證明章；這是深入路徑，不是所有人的 REQUIRED | 已核對入口 |

Alloy 站點同時指向 *Practical Alloy* 這本手冊草稿（Alcino Cunha、Nuno Macedo、Julien Brunel、David Chemouil）。它是教材，不是已出版的不變版本，引用時註明你讀到的日期。

## 論文與會議

會議入口與使用方式見 [研究與學術](06-RESEARCH-CAREER-AND-ACADEMIA.md)。個別奠基論文寫在各模組的 G 節，避免在索引裡複製一份會過時的長書目。

已在索引層確認、並會在模組中使用的例子：

- Robin Sommer、Vern Paxson。*Outside the Closed World: On Using Machine Learning for Network Intrusion Detection*。IEEE S&P 2010。DOI：`10.1109/SP.2010.25`。
- Stefan Savage、David Wetherall、Anna Karlin、Tom Anderson。*Practical Network Support for IP Traceback*。SIGCOMM 2000。DOI：`10.1145/347057.347560`。

## 未驗證時怎麼標

若日後連結失效，在使用處加上「未驗證（日期）」，改以出版者、DOI 或專案名稱搜尋，不要換成來路不明的鏡像。

---

[從這裡開始](00-START-HERE.md) · [網路基礎](foundations/computer-networking.md) · [模組 01](modules/01-network-security.md)
