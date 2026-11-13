# 模組 01 — 網路安全

[從這裡開始](../00-START-HERE.md) · [網路基礎](../foundations/computer-networking.md) · [模組 02](02-operating-system-and-systems-security.md)

網路協定的正常行為在 [計算機網路](../foundations/computer-networking.md)。本模組問的是這些行為把信任放在哪裡，以及防禦與量測能檢查什麼。

## A. 概述

網路安全研究協定、實作與營運網路在機密性、完整性與可用性上的失敗方式，以及如何偵測、緩解或把假設講清楚。它存在，是因為網際網路的轉送、名稱與傳輸大多先假設參與者大致誠實，安全是後來加上的層或營運措施。

真實世界裡它出現在企業網路的過濾與監控、服務提供者的流量工程與清洗、瀏覽器與伺服器的 TLS、以及研究者對網際網路規模現象的量測。

它和鄰居的差別：

- 與 [情資、歸因與量測](13-threat-intelligence-attribution-and-measurement.md)：網路安全可以停在「這個機制擋得住什麼」。歸因還要把證據連到基礎設施或組織，並處理不確定性。
- 與 [密碼與協定](04-cryptography-and-protocol-security.md)：TLS 的定義與證明在密碼模組；本模組關心它在網路上如何失敗，例如驗證被關掉、中間設備、部署差異。
- 與 [系統安全](02-operating-system-and-systems-security.md)：主機如何產生封包是系統問題；封包在路徑上遇到什麼是網路問題。

## B. 研究問題

1. 一份擷取裡，哪些 TCP 重送可以用遺失解釋，哪些需要你承認自己沒有路徑上的觀察？
2. 一個 DDoS 偵測特徵在合成的正常流量與合成的大量請求之間，誤報與漏報各在什麼條件下上升？
3. 被動收集的來源 IP，在經過 NAT 之後還能支持哪一層歸因，不能支持哪一層？
4. DNS 快取的存活時間會讓錯誤回答持續多久？規格保證了什麼，實作可能多做了什麼？
5. 防火牆的狀態表在什麼流量下會失去與端點狀態機的一致性？
6. 若 TLS 憑證驗證失敗仍繼續連線，應用程式實際失去的是伺服器鑑別、機密性，還是兩者？

## C. 研究者實際在做的事

吸引人的版本是「找出網路如何被濫用並設計更好的防禦」。日常工作比較接近：

- 讀 RFC 的狀態機與 Security Considerations。
- 在自己的實驗環境擷取封包，對照規格。
- 清洗與標註流量，記錄時鐘與取樣。
- 實作一個簡單特徵或狀態機，和基線比較。
- 測量誤報、漏報、延遲與資源成本。
- 寫下威脅模型：路徑上的對手、鄰近區域網路的對手、只能發送封包的對手，能力不同。
- 重現論文時先重現資料條件，而不是只重現結論句子。
- 發表量測或系統論文，或把負結果寫成「這個特徵在這些條件下不可靠」。

## D. 先修

| 先修 | 重要性 | 需要的深度 | 原因 |
|---|---|---|---|
| [網路基礎](../foundations/computer-networking.md) 到 TCP、DNS、HTTP、TLS | REQUIRED | 該頁指定的深度 | 沒有正常行為就無法談偏離 |
| 封包擷取的基本操作 | REQUIRED | L1 | 本模組的證據多數是擷取 |
| [機率與統計](../foundations/mathematics.md) | RECOMMENDED | L1 | 偵測與量測需要樣本和基線；推論公式可後補 |
| [程式](../foundations/programming.md) 的 Python 或 socket | REQUIRED | L1 | 產生你自己的流量與解析標頭 |
| 路由與 BGP | OPTIONAL | L0，路由安全方向才升 L2 | 多數偵測問題用不到路由政策 |
| [密碼定義](04-cryptography-and-protocol-security.md) | RECOMMENDED | L0–L1 | 讀 TLS 時知道鑑別與機密性是不同性質 |
| [作業系統](../foundations/operating-systems.md) 的 socket 與權限 | RECOMMENDED | L1 | 了解擷取權限與本機堆疊 |
| 機器學習 | ON-DEMAND | L0，直到你要評估這類偵測器 | 許多有用的偵測不是學習模型 |

## E. 知識路線

### Stage 0 — 入門

概念：威脅模型、被動觀察與主動探測的差別、可用性和完整性在網路上的例子。

成果：能說明為什麼不對公共網路做探測實驗。

先修：網路基礎的封裝 L1。

可延後：所有具體攻擊名稱。

### Stage 1 — 核心概念

概念：協定的安全假設、防火牆與封包過濾、狀態檢查、IDS 與 IPS 的差別、網路異常是相對基線的說法、監控的位置會決定你看得到什麼。

成果：給定「只在邊界看標頭」，列出三種你看不到的事。

先修：TCP 與 IP 的指定深度。

可延後：產品設定畫面、特徵碼語言。

IDS 通知人去調查；IPS 會阻擋或改寫。兩者都依賴感測位置與流量是否可重建。加密會讓內容特徵失效，這是限制，不是工具用錯。

### Stage 2 — 技術理解

概念：TCP 狀態與擷取對照、DNS 解析鏈、TLS 交握到「加密開始」為止、NAT 對來源位址的影響、路由是宣告。

成果：對自己的擷取寫出一頁 [協定分析](../templates/protocol-analysis.md)。

先修：Wireshark 的過濾器 L1。

可延後：BGP 屬性、TLS 記錄層格式。

### Stage 3 — 實作與分析

概念：一個有基線的偵測特徵、防火牆規則與它擋不住的流量、DDoS 的偵測與緩解在目標、路徑與來源端各能做什麼。

成果：在合成流量上比較兩個簡單規則的誤報與漏報，並寫限制。

先修：基礎統計 L1、Python L1。

可延後：即時高速處理、核心旁路、任何對非自有目標的壓力測試。

DDoS 研究在這一層只處理防禦問題：如何從合法尖峰中分辨大量請求、過濾依賴哪些標頭、過濾會誤傷誰、來源偽造會讓基於來源的懲罰打錯對象。緩解的高層類別包括就近過濾、速率限制、以及讓回應不放大到未驗證的來源。不提供製造中斷的步驟。

### Stage 4 — 研究題

路由安全、DNSSEC 的部署與失敗模式、加密流量的可觀察詮釋資料、網路韌性、回溯與歸因。

成果：針對一個問題寫文獻筆記與你能做的受控實驗，不能做的部分明確標出。

可延後且預設不做：網際網路規模的主動掃描、營運中 BGP 實驗、側信道參數。

#### 歸因與回溯

完整討論見 [詞彙](../GLOSSARY.md) 與 [模組 13](13-threat-intelligence-attribution-and-measurement.md)。本模組只要求你能分開：

- IP 來源識別：標頭上的位址。
- 路徑推論：流量可能經過的網路。
- 流量歸因：兩批流量是否相關。
- 基礎設施歸因：網域、憑證、主機的管理線索。
- 操作者：哪個自然人下指令。技術觀察幾乎回答不了這一層。

回溯研究的經典問題是：來源位址可以被填錯時，受害者還能對路徑得知什麼。這是研究題，不是你對真實攻擊源的操作指南。

## F. 實作學習

| 練習 | 目標 | 先備 | 工具 | 產出 | 學到什麼 | 難度 |
|---|---|---|---|---|---|---|
| 自有流量標註 | 標出各層標頭 | TCP L1 | Wireshark | 一頁標註 | 封裝與你仍不懂的欄位 | 初 |
| 只連本機的客戶端 | 產生可重現流量 | socket L1 | Python 或 C | 程式與擷取 | 規格與擷取的對照 | 初 |
| 合成流量特徵 | 比較兩個門檻 | 統計 L1 | Python | 表與限制 | 基線、誤報、漏報 | 中 |
| DNS 假設清單 | 寫出快取與真實性的假設 | DNS L1 | 解析器與 RFC 段落 | 假設表 | 名稱系統不是身份系統 | 中 |

對應專題：[初學](../projects/beginner-projects.md)、[進階](../projects/intermediate-projects.md)。

## G. 論文入口

奠基與必讀的批評：

- Robin Sommer、Vern Paxson。*Outside the Closed World: On Using Machine Learning for Network Intrusion Detection*。IEEE Symposium on Security and Privacy，2010。DOI：[`10.1109/SP.2010.25`](https://doi.org/10.1109/SP.2010.25)。說明機器學習入侵偵測為何難以部署。先讀摘要、引言與作者列出的挑戰。
- Stefan Savage、David Wetherall、Anna Karlin、Tom Anderson。*Practical Network Support for IP Traceback*。ACM SIGCOMM，2000。DOI：[`10.1145/347057.347560`](https://doi.org/10.1145/347057.347560)。討論在來源位址不可靠時追溯路徑的研究問題。把它當回溯研究的歷史入口，不當操作手冊。

標準：

- BCP 38 / RFC 2827，網路入口過濾，討論來源位址驗證的營運措施。由 [RFC Editor](https://www.rfc-editor.org/) 讀 RFC 2827。
- RFC 9293（TCP）、RFC 8446（TLS 1.3），只讀與你的問題相關的章節與安全考量。

近期研究不要在這份知識庫裡用未核對的題名代替。用當年的 [IMC](https://conferences.sigcomm.org/imc/)、[SIGCOMM](https://www.sigcomm.org/)、[USENIX Security](https://www.usenix.org/conference/usenixsecurity)、[NDSS](https://www.ndss-symposium.org/) 與 [IEEE S&P](https://sp.ieee-security.org/) 搜尋 DDoS measurement、DNS security、routing security。讀的時候用 [論文範本](../templates/research-paper-review.md)。

社群與實驗室：從你讀到的論文機構往回查，不要背排名。網路量測的公開資料常與 CAIDA（`https://www.caida.org/`）相關；使用前讀該資料集的條款與倫理說明。此入口在資源索引標為已核對時才把資料下載進實驗。

Zeek（`https://zeek.org/`）是網路監控的研究系統與文件來源，適合在你需要撰寫監控邏輯時再讀。它不是入門必裝。

## H. 學習資源

最後檢閱日：2026-11-13。完整說明見 [資源索引](../RESOURCE-INDEX.md)。

| 資源 | 類型 | 程度 | 費用 | 為什麼用 | 從哪裡開始 |
|---|---|---|---|---|---|
| [計算機網路基礎](../foundations/computer-networking.md) | 本知識庫 | 入門 | 免費 | 避免在模組裡重學全部協定 | TCP、DNS、TLS 三節 |
| [Wireshark 文件](https://www.wireshark.org/docs/) | 官方文件 | 入門 | 免費 | 擷取與過濾 | 使用者指南的擷取章 |
| [RFC Editor](https://www.rfc-editor.org/) | 規格 | 中階 | 免費 | 對照觀察 | 單篇 RFC 的安全考量 |
| Sommer and Paxson 2010 | 論文 | 中階 | 依出版者 | 建立對偵測研究的批評標準 | 摘要與挑戰列表 |
| [Kurose and Ross 作者站](https://gaia.cs.umass.edu/kurose_ross/) | 教科書 | 入門 | 書付費 | 安全章的分層背景 | 你尚未穩的那一層 |

延伸：CS144 的傳輸實驗、Zeek 文件、CAIDA 的資料目錄。BGP 與 RPKI 的教材在你把路由安全標成主修題目之後再找官方標準，不先收集。

## I. 自我評估

1. 你是否願意為了一個重送，同時看規格、擷取與你的程式，而不是只換一個更酷的工具？
2. 你是否接受許多「攻擊」在研究裡首先是資料標註與威脅模型問題？
3. 你是否能拒絕把 IP 位址寫成某個人？
4. 你是否願意報告一個特徵不好用，即使它的想法看起來正確？

若第 3 題是否定的，先做模組 13 的 Stage 0，再決定要不要主修本模組。

## J. 完成標準

| 階段 | 你可以交出 |
|---|---|
| 0 | 一段話：被動觀察與主動探測的界限，以及你只在哪些環境實驗 |
| 1 | 一張表：邊界監控看得到與看不到的各三項 |
| 2 | 一份對自己流量的協定筆記，含至少五個你查過規格的欄位 |
| 3 | 一組合成資料上的偵測比較：規則、基線、誤報、漏報、至少一個替代解釋 |
| 4 | 一篇論文的三遍筆記，加上一個你能在授權環境做的後續問題，以及明確不做的實驗 |

---

[網路基礎](../foundations/computer-networking.md) · [模組 13](13-threat-intelligence-attribution-and-measurement.md) · [模組 04](04-cryptography-and-protocol-security.md)
