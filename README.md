# 🛍️ WinUI 3 Sales Management App

Ứng dụng **quản lý bán hàng** được xây dựng bằng **WinUI 3 (.NET 8)** theo kiến trúc **Client–Server**.  
Đây là đồ án môn *Lập trình Windows*, được phát triển trong vòng **8 tuần**.

---

## 🚀 Mục tiêu dự án

Xây dựng ứng dụng **bán hàng** dành cho chủ cửa hàng, với các chức năng cơ bản:
- Đăng nhập / Đăng xuất (Authentication)
- Quản lý sản phẩm và loại sản phẩm
- Quản lý đơn hàng
- Báo cáo thống kê
- Dashboard tổng quan
- In hóa đơn, tìm kiếm, phân trang, v.v.

Ngoài ra, dự án sẽ triển khai thêm một số **chức năng nâng cao** như:
- Kiến trúc **MVVM**
- **Dependency Injection**
- Backup / Restore dữ liệu
- Quản lý khách hàng và khuyến mãi
- Chế độ dùng thử 15 ngày

---

## 🧩 Kiến trúc

**Client (WinUI 3 Desktop App)**  
→ Giao diện người dùng, xử lý logic hiển thị (MVVM pattern).  

**Server (API)**  
→ Xây dựng bằng ASP.NET Core / NodeJS / Python (tùy chọn), kết nối MySQL hoặc PostgreSQL.

**Cơ sở dữ liệu**  
→ Lưu trữ thông tin sản phẩm, đơn hàng, khách hàng, doanh thu.

---

## 🏗️ Công nghệ dự kiến sử dụng

| Thành phần | Công nghệ |
|-------------|------------|
| Giao diện | WinUI 3, XAML |
| Logic ứng dụng | C# (.NET 8) |
| Mẫu kiến trúc | MVVM |
| Dependency Injection | Microsoft.Extensions.DependencyInjection |
| API | REST / GraphQL |
| Database | MySQL hoặc PostgreSQL |
| ORM (tùy chọn) | Entity Framework Core |
| Quản lý mã nguồn | Git + GitHub |

---

## ⚙️ Setup ban đầu

1. Clone repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
