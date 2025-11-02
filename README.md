# 🪟 ĐỒ ÁN MÔN LẬP TRÌNH WINDOWS
## Ứng dụng quản lý bán hàng (Sales Management System)

---

## 0. 👥 Thông tin các thành viên

| STT | Họ tên | MSSV | Vai trò | Ghi chú |
|-----|---------|-------|----------|----------|
| 1 | Lê Huy | 21120466 |  |  |
| 2 | Đạo Minh Chiến | 22120033 |  |  |
| 3 | Phan Công Châu | 22120036 |  |  |
| 4 | Đỗ Ngọc Cường | 22120042 |  |  |
| 5 | Quách Thành Kiệt | 22120175 |  |  |
| 6 | Nguyễn Thanh Phong | 22120265 |  |  |

---

## 1. ⚙️ Chức năng ứng dụng

### **Chức năng cơ bản**
- Đăng nhập / Đăng xuất (JWT + Salt)
- Dashboard tổng quan
- Quản lý sản phẩm
- Quản lý loại sản phẩm
- Báo cáo / thống kê
- Cấu hình chương trình: phân trang, lưu lại chức năng chính lần cuối mở.

---

## 2. 🎨 Giao diện (Prototype Figma)

- File Figma: [ Xem Prototype tại đây](https://www.figma.com/file/xxxxx/SalesApp_UI_V1)
- Prototype mô phỏng các luồng chính:
- Đăng nhập → Dashboard → Quản lý sản phẩm → Tạo đơn hàng → In hóa đơn  
- UI sử dụng Fluent 2 Design System của Microsoft để tương thích với WinUI 3.

---

## 3. 🧑‍💻 Làm việc nhóm

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


---

## 5. Design Pattern sử dụng

---

## 6. Đảm bảo chất lượng

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

| Tuần | Nội dung công việc | Người phụ trách |
|------|--------------------|----------------|
| Tuần 1 | Khảo sát đề tài, phân tích yêu cầu, dựng prototyep figma
| Tuần 2 | Thiết kế UI (Figma), dựng kiến trúc MVVM, Hoàn thiện tầng dữ liệu + Repository
| Tuần 3 | Kết nối API, binding dữ liệu UI, Thêm chức năng CRUD + Dashboard
| Tuần 4 | Tích hợp nâng cao, backup/restore, khuyến mãi
| Tuần 5 | Test manual, unit test, hoàn thiện logic
| Tuần 6 | Hoàn thiện báo cáo, video demo, nộp đồ án
| Tuần 7 | Dự phòng

---

---

## 📜 Tác giả
> **Đồ án môn học: Lập trình Windows – Khoa Công nghệ thông tin - Trường Đại học Khoa học Tự nhiên 
> GVHD: *Thầy Trần Duy Quang*  
> Năm học: 2025

---

