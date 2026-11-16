# Ssport — Hệ Thống Quản Lý Kế Hoạch & Checklist Công Việc

Ứng dụng web theo dõi kế hoạch kinh doanh và checklist công việc đa tháng dành cho toàn thể nhân sự **Công ty TNHH Học viện Giáo dục Thể thao Ssport**.

---

## 📁 Cấu Trúc Dự Án

```text
ssport-plan/
├── index.html                  # Giao diện chính (hỗ trợ Light / Sepia / Dark, 4 chế độ xem)
├── data/
│   ├── bundle.js               # Dữ liệu tổng hợp các tháng (chạy được cả offline & online)
│   ├── months.json             # Danh mục các tháng làm việc
│   ├── tasks-2026-11.json      # Checklist 78 đầu việc chi tiết Tháng 11/2026
│   └── tasks-2026-10.json      # Checklist công việc lịch sử Tháng 10/2026
└── README.md                   # Hướng dẫn sử dụng và cập nhật
```

---

## 🚀 Hướng Dẫn Triển Khai Lên GitHub Pages (2 Phút)

### Cách 1: Tải lên trực tiếp trên giao diện web GitHub (Đơn giản nhất, không cần cài Git)

1. **Tạo Repository mới trên GitHub:**
   - Đăng nhập vào [github.com](https://github.com/).
   - Bấm nút **New** (Tạo repository mới).
   - Đặt tên Repository, ví dụ: `ssport-plan` hoặc `ssport-tasks`.
   - Chọn chế độ **Public** (để dùng GitHub Pages miễn phí).
   - Bấm **Create repository**.

2. **Tải toàn bộ thư mục lên:**
   - Trên trang repository vừa tạo, bấm **"uploading an existing file"** (hoặc kéo thả).
   - Kéo toàn bộ file `index.html` và thư mục `data/` vào khung upload.
   - Bấm **Commit changes**.

3. **Bật GitHub Pages để có link web:**
   - Vào mục **Settings** của repository -> chọn tab **Pages** ở thanh menu bên trái.
   - Tại mục **Build and deployment** -> **Branch**:
     - Chọn nhánh: `main` (hoặc `master`).
     - Chọn thư mục: `/ (root)`.
     - Bấm **Save**.
   - Sau khoảng 1 phút, GitHub sẽ cấp cho bạn một đường link công khai dạng:
     `https://<ten-tai-khoan>.github.io/ssport-plan/`

---

## 📅 Hướng Dẫn Cập Nhật Tháng Mới (Tháng 12, Tháng 1...)

Mỗi khi bước sang tháng làm việc mới, bạn chỉ cần thực hiện 1 trong 2 cách sau:

### Cách 1: Cập nhật trực tiếp vào file `data/bundle.js`
1. Mở file `data/bundle.js`.
2. Thêm thông tin tháng vào danh sách `months`:
   ```javascript
   { "id": "2026-12", "label": "Tháng 12/2026", "count": 50, "is_current": true }
   ```
3. Thêm danh sách công việc vào mục `tasks`:
   ```javascript
   "2026-12": [
     {
       "stt": 1,
       "project": "Tên dự án",
       "task": "Nhiệm vụ chính",
       "weight": "8",
       "assignee": "Tên người phụ trách",
       "desc": "Mô tả KPI cụ thể",
       "start_date": "01/12/26",
       "end_date": "05/12/26",
       "deadline_time": "17:00",
       "level": "Cao",
       "days_left": "5 ngày",
       "status": "Đang thực hiện",
       "done": false
     }
   ]
   ```
4. Lưu file và tải lên GitHub. Web app sẽ tự động hiển thị tháng mới trong menu chọn!

---

## 🎨 Tính Năng Ứng Dụng
- **Chuyển đổi đa tháng:** Chuyển qua lại giữa Tháng 11/2026, Tháng 10/2026 và các tháng tương lai.
- **4 Chế độ xem:** Theo nhân sự (*Assignee Cards*), Bảng chi tiết (*Table Checklist*), Kanban Board, Gom nhóm theo Dự án.
- **Thống kê tiến độ:** Theo dõi tỷ lệ hoàn thành, quá hạn, đang làm và phân bổ khối lượng cho 8 nhân sự.
- **Lưu trữ cục bộ (LocalStorage):** Tự động ghi nhớ các đầu việc nhân viên tick hoàn thành trên từng máy mà không làm mất dữ liệu gốc.
- **Bộ 3 Theme:** Sáng (Light) / Giấy Sepia ấm mắt / Tối (Dark mode).
