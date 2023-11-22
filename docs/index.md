# devops guide

[[toc]]

## To-Do list
- [logging to-do list](/system/logging/#to-do)
- [metrics to-do list](/system/metrics/#to-do)
- [tracing to-do list](/system/tracing/#to-do)


## abstract
軟體生命週期分為多個階段，包含開發、測試、部屬等等，在每個階段都有專門負責的部門，要如何讓各部門人員能夠緊密協同作業，就需要可遵循的工作架構，而 DevOps 就是一種軟體開發架構，負責讓開發者 (Dev) 和維運人員 (Ops) 合作之間更順暢，不僅能加速整個開發過程，也能有效降低協作成本。


![devops-toolchain](~@source/assets/img/devops-chain.svg)


實現 devops 其中一種方式, 實踐 SRE (Site Reliability Engineering)
- 接受失效(Failure)，視失效為開發週期中的一個元素
    - 培養不究責的文化 Blamelessness => 以利事後調查
    - 允許犯錯 => 鼓勵創新
    - 用來承擔 Launch 的風險 => 做到快速 Launch

- 減少組織之間的穀倉效應
    - 讓開發/測試/生產環境長得幾乎一模一樣，提早發現錯誤
    - 可以被版本控制工具所管理 (如 git)，這代表任何的改變都有跡可尋
    - 減少人工所產生的錯誤
    - 達成自動化

- 持續改善
    - 持續整合 Continuous Integration
    - 持續交付 Continuous Delivery
    - 持續部署 Continuous Deployment

- 善用工具和自動化: 勞務工作如何更有效率, 如以下
    - 手動執行 script、開關機、上新版程式
    - 對每個新客戶進行的重複性工作
    - 沒有永久的價值(長期的改善)

- 任何事都是可以被量測的
    - 監控是追蹤系統健康和可用性最好的方法
    - 如果必須要有人閱讀電子郵件, 並判斷是否需要採取行動的系統,從根本上是有缺陷的。
    - 只有一定要採取行動的時候，系統才發出通知。


## 各小組目標
### DBA
- 自動化一切
- 維運
- 提高系統可靠性
- 協助Developer設計出高可用性服務Roadmap
- infra自動化
- DBA各程式導入CI/CD自動化
- Monitor強化
- 異質database研究(eg: nosql系列)
- 提高承載量

### DevOps
- 自動化一切
- 維運
- 提高系統可靠性
- 協助Developer設計出高可用性服務Roadmap
- 增加自動化覆蓋率至100%
    - KKday所有服務覆蓋率(目前85%)
    - 內部支援系統覆蓋率(目前10%, 此項指的是如jenkins, woodpecker, env等)
- 系統承載量/自動復原
    - 內部支援系統承載量彈性伸縮(如jenkins woodpecker)
    - KKday各服務承載量計算評估並分別設計scaling界限
    - 系統錯誤時自動復原能力(以infra層級為主)
    - 異地備援
- 持續CI/CD優化
    - 細節自動化(如自動release note)
    - 定義github PR標準(如pr開頭為feat, fix等)
- KKday DevOps文化持續建立 (Developer開發時多想到維運)
    - Root cause report機制導入
- 開發/設計工具
    - 開發工具供developer使用，協助developer直接建立服務
- 以上包含持續收以前技術債

### Cross function
- 建立共用性SDK/服務
- 設計各種framework以達快速開發
- 設計系統溝通標準Roadmap
- backend framework(規範/設計原則)
    - 發展kkday framework(base on laravel)
    - HTTP相關framework
    - Daemon(worker)相關framework
    - monitor/log/tracing相關framework
- frontend framework(規範/設計原則)
    - 前端monitor/log/tracing framework
    - socket技術
- API標準
    - 各系統串接/溝通介面定義(HTTP or gRPC)
    - 各系統API產生器 or 快速使用其他產品API


## 參考資料
[RoadMap](https://roadmap.sh/devops)      
[SRE - site reliability engineering](https://sre.google/books/)     
[DevOps - 90 day of devops](https://github.com/MichaelCade/90DaysOfDevOps)      
[DevOps 是什麼？](https://blog.cloud-ace.tw/application-modernization/devops/what-is-devops-how-google-use-sre/)       
[那些年我們做過的 DevOps Pipeline](https://speakerdeck.com/cheng_wei_chen/na-xie-nian-wo-men-zuo-guo-de-devops-pipeline?slide=65)       

```kroki-mermaid
sequenceDiagram
GitLab->>Kroki: Request rendering
Kroki->>Mermaid: Request rendering
Mermaid-->>Kroki: Image
Kroki-->>GitLab: Image
```
