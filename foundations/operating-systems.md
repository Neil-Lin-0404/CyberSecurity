# 作業系統

[計算機結構](computer-architecture.md) · [共同基礎](../02-CORE-FOUNDATIONS.md) · [計算機網路](computer-networking.md)

學習類型：概念為主。讀 xv6 是程式與研究技能，屬於加深路徑，不是抽樣資安專長的門票。

## 必備與進階分開

必備是能解釋隔離與介面。進階是核心內部實作、排程器公式與檔案系統日誌結構。

| 主題 | 深度 | 重要性 | 原因 |
|---|---|---|---|
| 行程與位址空間 | L1 | REQUIRED | 隔離的基本單位 |
| 執行緒 | L1 | REQUIRED | 共享與並發 |
| 排程 | L0 | RECOMMENDED | 知道核心選擇誰執行；演算法研究可延後 |
| 虛擬記憶體與分頁 | L1 | REQUIRED | 記憶體保護的機制 |
| 檔案系統 | L1 | RECOMMENDED | 權限、路徑與鑑識會用到；日誌格式可延後 |
| 系統呼叫 | L1 | REQUIRED | 使用者程式進入核心的窄介面 |
| 權限 | L1 | REQUIRED | 使用者、群組與特殊權限是政策，不是只有技術 |
| 使用者態與核心態 | L1 | REQUIRED | 特權邊界 |
| Linux 架構 | L1 | REQUIRED | 你的實驗環境 |
| Windows 架構 | L0 | OPTIONAL | 只有樣本、企業環境或對照研究需要 |
| 行程間通訊 | L1 | RECOMMENDED | 管線、socket、共享記憶體的信任差異 |
| 同步 | L1 | RECOMMENDED | 鎖解決什麼、死結是什麼 |
| 核心架構與原始碼 | L0 概觀 | ON-DEMAND | 子系統原始碼在系統安全主修後再讀 |

## 你要能講的故事

程式在使用者態執行，能碰到的記憶體由頁表限制。它需要檔案、網路或新行程時，透過系統呼叫進入核心。核心檢查權限與參數，再代表行程完成動作。執行緒若共享記憶體，同步錯誤會讓隔離在行程內部失效。虛擬機器與容器是在這層故事之上再加的邊界，細節放在 [模組 02](../modules/02-operating-system-and-systems-security.md) 與 [模組 07](../modules/07-cloud-container-and-infrastructure-security.md)，這裡只需 L0：它們不是魔法，隔離強度取決於共享了什麼。

## Linux 與 Windows

Linux：先會看行程（`ps`）、開啟的檔案與 socket、權限位元、以及 `strace` 對你自己程式的輸出。核心版本與發行版差異先忽略。

Windows：L0 知道它也有行程、權限與系統呼叫邊界，但物件、登錄與驅動模型不同。不要在學 Linux 介面的同一週改學 Windows 核心。

## 建議閱讀順序

1. [OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/) 的行程與虛擬記憶體章節，讀到你能回答自測。
2. 在虛擬機對自己的程式跑 `strace`，把系統呼叫分成檔案、行程與網路三類。
3. 若系統安全或作業系統實作成為主修，再讀 [MIT 6.1810](https://pdos.csail.mit.edu/6.1810/) 的 xv6 書第 1 章，並對照 [xv6-riscv](https://github.com/mit-pdos/xv6-riscv)。xv6 是教學系統，不是 Linux。

## 自測

1. 說明兩個行程為什麼不能直接讀彼此的變數，以及共享記憶體會改變哪一個假設。
2. 看一次 `strace`，指出哪個呼叫在請求核心做事。
3. 說明分頁權限失敗時，失敗的是哪一層檢查。你不需要寫出頁表項目的每一個位元。
4. 列出你刻意還沒學的核心內部主題。

## 可延後

排程器原始碼、檔案系統日誌、記憶體配置器、eBPF、核心模組開發、Windows 驅動。系統安全模組會告訴你何時才把其中一項升為 REQUIRED。

---

[網路](computer-networking.md) · [系統安全模組](../modules/02-operating-system-and-systems-security.md) · [程式](programming.md)
