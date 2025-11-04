# 🪟 ĐỒ ÁN MÔN LẬP TRÌNH WINDOWS
## Ứng dụng quản lý bán hàng (Sales Management System)

---
## Mục lục
1. [Thông tin các thành viên](#0-thông-tin-các-thành-viên)  
2. [Chức năng ứng dụng](#1-chức-năng-ứng-dụng)  
3. [Giao diện (Prototype Figma)](#2-giao-diện-prototype-figma)  
4. [Làm việc nhóm & Chiến lược Git](#3-làm-việc-nhóm--chiến-lược-git)  
5. [Kiến trúc phần mềm](#4-kiến-trúc-phần-mềm)  
6. [Design Pattern áp dụng](#5-design-pattern-áp-dụng)  
7. [Đảm bảo chất lượng](#6-đảm-bảo-chất-lượng)
9. [Các tính năng nâng cao](#7-các-tính-năng-nâng-cao)  
10. [Kế hoạch & Tiến độ thực hiện](#8-kế-hoạch--tiến-độ-thực-hiện)  

---

## 0. Thông tin các thành viên

| STT | Họ tên | MSSV | Vai trò | Ghi chú |
|-----|---------|-------|----------|----------|
| 1 | Lê Huy | 21120466 |  |  |
| 2 | Đạo Minh Chiến | 22120033 |  |  |
| 3 | Phan Công Châu | 22120036 |  |  |
| 4 | Đỗ Ngọc Cường | 22120042 |  |  |
| 5 | Quách Thành Kiệt | 22120175 |  |  |
| 6 | Nguyễn Thanh Phong | 22120265 |  |  |

---

## 1. Chức năng ứng dụng

### **Chức năng cơ bản**
- Đăng nhập / Đăng xuất (JWT + Salt)
- Dashboard tổng quan
- Quản lý sản phẩm
- Quản lý loại sản phẩm
- Báo cáo / thống kê
- Cấu hình chương trình: phân trang, lưu lại chức năng chính lần cuối mở.

---

## 2. Giao diện (Prototype Figma)

- File Figma: [ Xem Prototype tại đây](https://www.figma.com/design/hGmClwEz3A8rula3h4sst7/Windows-Programming?node-id=0-1&t=KYH1VTSzuTjpkDmF-1)
- Prototype mô phỏng các luồng chính:
- Đăng nhập → Dashboard → Quản lý sản phẩm → Tạo đơn hàng → In hóa đơn  
- UI sử dụng Fluent 2 Design System của Microsoft để tương thích với WinUI 3.

---

## 3. Làm việc nhóm

### **Công cụ và quy trình**
- Quản lý mã nguồn: **GitHub**
- Giao tiếp nhóm: **Zalo, Notion, Google meet**
- Thiết kế UI: **Figma**
- IDE: **Visual Studio 2022**, **PostgreSQL / Supabase**

### **Chiến lược làm việc với Git**
- Nhánh chính: `main`  
- Mỗi thành viên tạo branch riêng: `feature/<tên-chức-năng>`  
- Quy trình merge:  
  1. Commit → Push lên nhánh cá nhân  
  2. Pull Request → Review code → Merge vào `develop`  
  3. Khi ổn định → merge `develop` → `main`

---

## 4. Kiến trúc phần mềm

### 4.1. Frontend: Mô hình MVVM (Model–View–ViewModel)

Phần giao diện được áp dụng mô hình **MVVM** để tách biệt giữa giao diện, dữ liệu và logic xử lý hiển thị:

* **View:** Chịu trách nhiệm hiển thị dữ liệu và nhận các thao tác từ người dùng.
* **ViewModel:** Xử lý logic hiển thị, ràng buộc dữ liệu (**data binding**) và giao tiếp với backend thông qua RESTful API.
* **Model:** Biểu diễn dữ liệu nhận từ server, như thông tin sản phẩm, đơn hàng, hay doanh thu.

> Cách tổ chức này giúp mã nguồn frontend **rõ ràng**, **dễ kiểm thử** và **dễ mở rộng** khi thêm hoặc thay đổi tính năng giao diện.

---

### 4.2. Backend: Mô hình 3-Layer Architecture

Phần backend được tổ chức theo mô hình **3-Layer Architecture**, đảm bảo phân tách rõ ràng giữa các tầng:

* **Controller:** Tiếp nhận yêu cầu từ frontend, điều phối và trả kết quả phản hồi.
* **Service:** Chứa toàn bộ **logic nghiệp vụ** của hệ thống như tính doanh thu, quản lý đơn hàng, kiểm tra tồn kho.
* **Repository:** Làm việc trực tiếp với cơ sở dữ liệu, thực hiện các thao tác **CRUD** (Create, Read, Update, Delete).

> Dữ liệu giữa frontend và backend được trao đổi thông qua **RESTful API**, đảm bảo tính độc lập và khả năng thay thế công nghệ giữa hai phần.

---

### 4.3. Clean Architecture trong dự án

Ứng dụng được định hướng và triển khai theo **Clean Architecture**, đảm bảo nguyên tắc **phụ thuộc hướng vào trong (Dependency Rule)** – các tầng bên ngoài có thể phụ thuộc vào tầng trong, nhưng ngược lại thì không.

#### Clean Architecture ở Frontend (Áp dụng qua MVVM)

| Tầng (Layer) | Thành phần tương ứng | Chức năng chính |
| :--- | :--- | :--- |
| **Presentation Layer** | **View** | Hiển thị giao diện và nhận thao tác người dùng. |
| **Application Layer** | **ViewModel** | Xử lý logic hiển thị, gọi dữ liệu từ API và cập nhật lại giao diện. |
| **Domain Layer** | **Model** | Chứa các lớp mô hình dữ liệu cốt lõi (Product, Order, Category, User). |
| **Infrastructure Layer** | API Services | Bao gồm các service gọi REST API, lưu dữ liệu tạm thời hoặc thao tác với bộ nhớ cục bộ. |

#### Clean Architecture ở Backend (Áp dụng qua 3-Layer)

| Tầng (Layer) | Thành phần tương ứng | Chức năng chính |
| :--- | :--- | :--- |
| **Presentation Layer** | **Controller** | Tiếp nhận request từ frontend và trả response cho client. |
| **Application Layer** | **Service** | Chịu trách nhiệm xử lý logic nghiệp vụ và điều phối dữ liệu giữa các tầng. |
| **Domain Layer** | **Model** | Định nghĩa các đối tượng cốt lõi của hệ thống (Product, Order, Category, User). |
| **Infrastructure Layer** | **Repository** | Gồm Repository và các cấu hình truy cập cơ sở dữ liệu, giúp hệ thống kết nối và lưu trữ thông tin. |
---


## 5. Design Pattern sử dụng
| STT | Design Pattern                    | Mục đích chính                                                                                                                                           |
| :-: | :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | **Command**                       | Đóng gói **thao tác người dùng** (nhấn nút, menu) thành đối tượng để thực thi và quản lý.                                                                |
|  2  | **Observer**                      | **Cập nhật tự động** các phần UI (View) phức tạp khi trạng thái dữ liệu (Model/ViewModel) thay đổi, ngoài `INotifyPropertyChanged` cơ bản.               |
|  3  | **Repository**                    | Cung cấp lớp trung gian để **quản lý dữ liệu** và tách biệt **Tầng Logic Nghiệp vụ (ViewModel)** khỏi chi tiết truy cập dữ liệu (SQL, Web API).          |
|  4  | **Facade**                        | Cung cấp một **interface đơn giản** cho ViewModel truy cập vào một **hệ thống con phức tạp** (bao gồm DB, File Storage, Web Service).                    |
|  5  | **Factory Method** / **Mediator** | **Tạo các đối tượng** giao tiếp client-server (**Service Connector**) một cách **độc lập** với code Business Logic (ViewModel).                          |
|  6  | **Strategy**                      | Thay đổi **thuật toán xử lý** động.                                                                                                                      |

---

## 6. Đảm bảo chất lượng
### 6.1 Coding Convention

#### Quy tắc đặt tên
- **Tên biến & phương thức**: dùng `PascalCase` cho phương thức, `camelCase` cho biến cục bộ.  
- **ViewModel**: kết thúc bằng hậu tố `ViewModel` (VD: `OrderViewModel`, `ProductViewModel`).  
- **Command & Property**: tuân theo chuẩn **MVVM Toolkit** (`[ObservableProperty]`, `[RelayCommand]`).

#### Thư mục tổ chức
```
/Views
/ViewModels
/Models
/Services
/Helpers
/Tests
```

#### Nguyên tắc viết code
- Tuân thủ **SOLID** và **Clean Code**.  
- Tất cả commit phải đi kèm description rõ ràng.  
- Hạn chế **code-behind**, logic đặt trong **ViewModel**.  
- Comment cho logic phức tạp, ưu tiên code dễ đọc.  
- Sử dụng `.editorconfig` + **StyleCop** để format tự động.  
- Commit message chuẩn: `feat:`, `fix:`, `refactor:`, `test:`  
- Không viết logic nghiệp vụ trong **View (XAML.cs)** — toàn bộ xử lý được thực hiện trong **ViewModel** hoặc **Service**.

#### Format & Style
- Tuân theo **.NET Coding Style (Microsoft C# Guidelines)**.  
- Dùng **StyleCop Analyzers** hoặc **Roslyn Analyzer** để kiểm tra coding rule.  
- Cấu hình `.editorconfig` để thống nhất format toàn dự án.

#### Quy trình commit
Sử dụng **Conventional Commit** cho Git message:

```
feat: thêm màn hình quản lý đơn hàng
fix: sửa lỗi binding dữ liệu sản phẩm
refactor: tách service xử lý doanh thu
docs: cập nhật hướng dẫn sử dụng
```

---

### 6.2 Chiến lược kiểm thử (Testing Strategy)

#### 1. Manual Test (Kiểm thử thủ công)
**Mục tiêu**: Đánh giá trải nghiệm người dùng và kiểm tra luồng nghiệp vụ chính.

**Phương pháp:**
- Test từng chức năng: Login, CRUD sản phẩm, đơn hàng, báo cáo.  
- Test theo role: Admin, Staff, User.  
- Test trên nhiều độ phân giải màn hình Windows.  
- Ghi log kiểm thử trên **Google Sheet / Azure DevOps / Jira**.

---

#### 2. Unit Test (Kiểm thử đơn vị)
**Mục tiêu**: Đảm bảo các hàm và component hoạt động đúng độc lập.  
**Công cụ**: `xUnit` hoặc `NUnit`, `Moq` để mock service/API.

**Phạm vi:**
- Tính toán hóa đơn, doanh thu.  
- Validate dữ liệu nhập.  
- Test ViewModel không phụ thuộc UI.  

**Cấu trúc thư mục test:**
```
/Tests
  /Services
    OrderServiceTests.cs
  /ViewModels
    OrderViewModelTests.cs
```

**Mục tiêu bao phủ**: ≥ 70% dòng lệnh.

---

#### 3. UI Automation Test (Kiểm thử giao diện tự động)
**Mục tiêu**: Mô phỏng thao tác người dùng để phát hiện lỗi UI.  
**Công cụ**: WinAppDriver / Playwright Desktop / Appium Windows.

**Kịch bản test:**
1. Mở app → đăng nhập → thêm sản phẩm → tạo đơn → kiểm tra tổng tiền.  
2. Thử nhập sai dữ liệu xem có hiển thị lỗi.  
3. Test timeout khi API lỗi.

---

### 6.3 Tổng kết

| Hạng mục          | Công cụ / Quy ước                            | Mục tiêu                              |
|-------------------|----------------------------------------------|----------------------------------------
| Coding convention | StyleCop, .editorconfig, Conventional Commit | Giữ code thống nhất và dễ bảo trì     |
| Manual test       | Checklist, cross-resolution test             | Xác minh chức năng và UX              |
| Unit test         | xUnit / NUnit, Moq                           | Kiểm tra logic nghiệp vụ và ViewModel |
| UI test tự động   | WinAppDriver / Appium for Windows            | Đảm bảo UI hoạt động đúng             |
| Code review       | Pull Request & Review                        | Phát hiện lỗi và cải thiện chất lượng |

---

## 7. Tính năng nâng cao

| Tên tính năng | Ghi chú |
|----------------|---------|
| Auto Save | +0.25 |
| Responsive Layout | +0.5 |
| Bổ sung khuyến mãi | +1.0 |
| Sử dụng kiến trúc MMVM | +0.5 |
| Sử dụng dependency injection | +0.5 |
| Quản lý khách hàng | +0.5 |
| In đơn hàng (PDF) | +0.5 |
| Hỗ trợ sắp xếp khi xem danh sách theo yêu cầu | +0.5 |
| Hỗ trợ tìm kiếm nâng cao | +1.0|

---

## 8. Kế hoạch & Tiến độ thực hiện

| Tuần | Nội dung công việc |
|------|--------------------|
| Tuần 1 | Khảo sát đề tài, phân tích yêu cầu, dựng prototyep figma
| Tuần 2 | Thiết kế UI (Figma), dựng kiến trúc MVVM, Hoàn thiện tầng dữ liệu + Repository
| Tuần 3 | Kết nối API, binding dữ liệu UI, Thêm chức năng CRUD + Dashboard
| Tuần 4 | Tích hợp nâng cao, backup/restore, khuyến mãi
| Tuần 5 | Test manual, unit test, hoàn thiện logic
| Tuần 6 | Hoàn thiện báo cáo, video demo, nộp đồ án
| Tuần 7 | Dự phòng

---

---

## Tác giả
> **Đồ án môn học: Lập trình Windows**
> GVHD: *Thầy Trần Duy Quang*  
> Năm học: 2025

---

