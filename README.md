# 健身房會員管理系統

健身房會員管理系統使用 C#、ASP.NET Core Web API 與 MySQL，提供會員、課程、出勤與 POS 銷售等完整管理功能，並採用前後端分離與多層式架構設計，方便維護與後續擴充。 

---

## 系統架構概觀

系統採用四層架構，自上而下如下所示。 

![UML_Stracture](https://github.com/user-attachments/assets/082a59ff-a4b7-472c-a101-04e93bcb17d8)

[ WinForms 前端 / 行動 App ]

  |
  |
  |HTTP / JSON (REST API)
  v
  
+-----------------------------+

ASP.NET Core Web API 層
  Controllers
- AuthController
- MembersController
- PackagesController
- PurchasesController
- PaymentsController
- ClassesController
- EnrollmentsController
- AttendanceController
- POSController
- ReportsController
- NotificationsController
+-----------------------------+
   |
   | 呼叫 Service / Repository
   v
+-----------------------------+

Domain / Service 層
Services
- MemberService
- PackageService
- PurchaseService
- PaymentService
- ClassService
- AttendanceService
- PosService
- ReportService
- NotificationService
+-----------------------------+
   |
   | 透過 Repository 操作資料
   v
  +-----------------------------+

資料存取層 (Infrastructure)
Repositories
- MemberRepository
- EmployeeRepository
- PackageRepository
- PurchaseRepository
- PaymentRepository
- ClassRepository
- AttendanceRepository
- ProductRepository
- SaleRepository
- NotificationRepository
- AuditLogRepository
- ReportRepository
使用技術：
- Entity Framework Core
- MySQL Provider
+-----------------------------+
    |
    | EF Core / SQL
    v
+-----------------------------+

MySQL 資料庫
資料表
- 使用者
- 員工
- 會員
- 套餐
- 會員購買紀錄
- 付款紀錄
- 課程排程
- 課程報名
- 出勤紀錄
- 商品
- 銷售單
- 銷售明細
- 通知
- 操作日誌
- 報表
+-----------------------------+
  
---

## 資料模型與關聯圖

下圖為資料表與其關聯關係示意，用於說明會員、員工、課程、銷售等實體之間的 1–N 關係。 

![UmL_Relationship](https://github.com/user-attachments/assets/cb96630c-3580-4c83-ab9d-ce12fa8b7132)

---

## 主要功能模組

- **會員管理**
  - 會員建立 / 編輯 / 停權。
  - 檢視購買紀錄、出勤紀錄與通知紀錄。 

- **套餐與合約管理**
  - 套餐方案定義（名稱、月數、價格、最大堂數）。
  - 會員購買紀錄與到期日管理。 

- **課程與出勤管理**
  - 課程排程與教練指派。
  - 課程報名 / 取消。
  - 會員出勤紀錄（感應卡 / QR / 手動簽到）。 

- **POS 與庫存**
  - 商品資料與庫存量管理。
  - 銷售單與銷售明細（對應會員與員工）。 

- **系統與通知**
  - 登入與角色權限（管理員 / 員工）。
  - 操作日誌與系統報表。
  - 會員通知（例如到期提醒）。 

---

## 專案目錄結構

GymManagement/
├─ src/
│ ├─ Gym.Api/ # ASP.NET Core Web API
│ │ ├─ Controllers/
│ │ ├─ Program.cs
│ │ └─ appsettings.json
│ ├─ Gym.Domain/ # Domain Models & Services
│ │ ├─ Entities/
│ │ └─ Services/
│ ├─ Gym.Infrastructure/ # EF Core / Repositories
│ │ ├─ DbContexts/
│ │ └─ Repositories/
│ └─ Gym.WinForms/ # WinForms Client (optional)
│ ├─ Forms/
│ └─ Services/ # HttpClient to Web API
└─ docs/
├─ UML_Relationship.png # ER diagram
└─ UML_Structure.png # Layered architecture


undefined
---

## 技術棧

- **後端**：ASP.NET Core Web API  
- **前端**：C# WinForms（可擴充為 MAUI / 行動 App）  
- **資料庫**：MySQL（搭配 Entity Framework Core）  
- **架構模式**：分層架構 + Repository / Service Pattern，前後端分離，支援長期維護與功能擴充。 

---

## 未來可擴充方向

- 門禁刷卡與 QR Code 簽到整合。  
- 行動支付與第三方金流（例如藍新、綠界）。  
- 進階報表與 BI 分析儀表板（營收、留存率、課程熱門度等）。 
