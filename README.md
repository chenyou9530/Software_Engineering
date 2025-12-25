# 🏋️‍♂️ 健身房會員管理系統（Gym Management System）

本專案為一套 **健身房會員管理系統**，使用 **C#、ASP.NET Core Web API 與 MySQL** 建置，提供會員、課程、出勤、POS 銷售等完整管理功能。  
系統採用 **前後端分離** 與 **多層式架構（Layered Architecture）**，易於維護、測試與後續擴充。

---

## 📌 系統特色

- 前後端分離（RESTful API）
- 分層架構（Controller / Service / Repository）
- 支援會員、課程、出勤、POS、報表與通知
- 使用 Entity Framework Core 操作 MySQL
- 架構清楚，適合中大型系統與長期維護

---

## 🏗️ 系統架構概觀

![UML_Stracture](https://github.com/user-attachments/assets/082a59ff-a4b7-472c-a101-04e93bcb17d8)

[ WinForms / 行動 App ]
        |
        | HTTP / JSON (REST API)
        v

| ASP.NET Core Web API 層     |
|-----------------------------|
| Controllers                 |
| - AuthController            |
| - MembersController         |
| - PackagesController        |
| - PurchasesController       |
| - PaymentsController        |
| - ClassesController         |
| - EnrollmentsController     |
| - AttendanceController      |
| - POSController             |

        |
        v

| Application / Service 層    |
|-----------------------------|
| - MemberService             |
| - PackageService            |
| - PurchaseService           |
| - PaymentService            |
| - ClassService              |
| - AttendanceService         |
| - PosService                |
| - ReportService             |
| - NotificationService       |

        |
        v

| Infrastructure / Repository |
|-----------------------------|
| - MemberRepository          |
| - PackageRepository         |
| - PurchaseRepository        |
| - PaymentRepository         |
| - ClassRepository           |
| - AttendanceRepository      |
| - ProductRepository         |
| - SaleRepository            |
| - NotificationRepository    |
| - AuditLogRepository        |
| - ReportRepository          |
  

        |
        v

| MySQL Database              |
|-----------------------------|
| - 使用者                    |
| - 員工                      |
| - 會員                        |
| - 套餐                      |
| - 會員購買紀錄               |
| - 付款紀錄                  |
| - 課程排程                  |
| - 課程報名                  |
| - 出勤紀錄                  |
| - 商品                      |
| - 銷售單                    |
| - 銷售明細                  |
| - 通知                      |
| - 操作日誌                  |
| - 報表                      |


---

## 🧩 資料模型與關聯

![UML_Relationship](https://github.com/user-attachments/assets/cb96630c-3580-4c83-ab9d-ce12fa8b7132)

- 會員（Member）⇄ 購買紀錄（Purchase）
- 課程（Class）⇄ 課程報名（Enrollment）
- 會員 ⇄ 出勤紀錄（Attendance）
- 商品（Product）⇄ 銷售單（Sale）⇄ 銷售明細（SaleItem）
- 員工（Employee）⇄ 操作日誌（AuditLog）

---

## 🚀 主要功能模組

### 👤 會員管理
- 會員新增 / 編輯 / 停權
- 查詢購買紀錄、出勤紀錄、通知紀錄

### 📦 套餐與合約管理
- 套餐方案設定（價格、月數、堂數）
- 會員購買與到期日管理

### 🗓️ 課程與出勤管理
- 課程排程與教練指派
- 課程報名 / 取消
- 出勤紀錄（QR Code / 感應卡 / 手動簽到）

### 🛒 POS 與庫存管理
- 商品與庫存管理
- 銷售單與銷售明細
- 銷售紀錄對應會員與員工

### ⚙️ 系統與通知
- 登入與角色權限（管理員 / 員工）
- 操作日誌（Audit Log）
- 系統報表
- 會員通知（到期提醒等）

---

## 📁 專案目錄結構
    GymManagement/
    ├─ src/
    │  ├─ Gym.Api/                     # ASP.NET Core Web API
    │  │  ├─ Controllers/
    │  │  ├─ Filters/
    │  │  ├─ Middleware/
    │  │  ├─ Program.cs
    │  │  └─ appsettings.json
    │  │
    │  ├─ Gym.Application/             # Application / Service Layer
    │  │  ├─ Interfaces/
    │  │  ├─ Services/
    │  │  └─ DTOs/
    │  │
    │  ├─ Gym.Domain/                  # Domain Model
    │  │  ├─ Entities/
    │  │  ├─ Enums/
    │  │  └─ ValueObjects/
    │  │
    │  ├─ Gym.Infrastructure/          # EF Core / Repository
    │  │  ├─ DbContexts/
    │  │  ├─ Configurations/
    │  │  └─ Repositories/
    │  │
    │  └─ Gym.WinForms/                # WinForms Client
    │     ├─ Forms/
    │     └─ Services/                 # HttpClient 呼叫 API
    │
    └─ docs/                           # 文件 / UML / 架構圖


---

## 🛠️ 技術棧

- **後端**：ASP.NET Core Web API  
- **前端**：C# WinForms（可擴充 MAUI / 行動 App）  
- **ORM**：Entity Framework Core  
- **資料庫**：MySQL  
- **架構模式**：
  - 分層架構（Layered Architecture）
  - Repository Pattern
  - Service Pattern
  - RESTful API

---

## 🔮 未來擴充方向

- 🚪 門禁刷卡 / QR Code 簽到整合
- 💳 第三方金流（藍新、綠界、信用卡）
- 📊 進階報表與 BI 儀表板
  - 營收分析
  - 會員留存率
  - 課程熱門度分析
- 📱 行動 App（MAUI / Flutter）

---


