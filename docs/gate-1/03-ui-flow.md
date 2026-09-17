# Tài liệu Luồng Giao diện & Wireframe (UI Flow)

> **Dự án**: Campus 24/7 – Trợ lý AI Vận hành Học vụ 24/7  
> **Chủ trì**: Thành viên 1 (Kỹ sư Giao diện & Đặc tả Kỹ thuật)  
> **Figma Link**: *(Cập nhật link Figma với quyền Anyone with link can view tại đây)*

---

## 1. Sơ đồ Luồng Người dùng Tổng quát (User Journey)

```text
               ┌───────────────────────┐
               │    Sinh viên đăng nhập │
               └───────────┬───────────┘
                           │
                 [Nhập yêu cầu chat]
                           │
       ┌───────────────────┼───────────────────┐
       ▼                   ▼                   ▼
 [Hỏi quy chế]      [Yêu cầu dịch vụ]     [Khiếu nại/Nhạy cảm]
       │                   │                   │
  RAG Tra cứu       Agent trích xuất      Agent kích hoạt
  + Trích dẫn       + Hiện Xác nhận       Handover cán bộ
       │                   │                   │
[Xem câu trả lời]    [Bấm Confirm]        [Tạo ticket khẩn]
                           │                   │
                   [Tạo ticket/đặt chỗ]        │
                           └─────────┬─────────┘
                                     │
                                     ▼
                          ┌─────────────────────┐
                          │ Dashboard Cán bộ    │
                          │ - Xem context       │
                          │ - Xử lý / Phản hồi  │
                          └─────────────────────┘
```

---

## 2. Chi tiết Các Màn hình Cần Vẽ trên Wireframe/Figma

### 2.1. Cổng Sinh viên (Student Portal)
1. **Màn hình Chat chính**:
   - Sidebar: Lịch sử trò chuyện, danh sách ticket của tôi, nút tạo phiên chat mới.
   - Main Chat Area: Khung hiển thị tin nhắn, hộp nhập câu hỏi.
   - Thẻ Citation Component: Nằm dưới câu trả lời của Bot, hiển thị thẻ trích dẫn (Tên văn bản, Điều khoản) có thể click để mở popover xem trích đoạn gốc.
2. **Hộp thoại Xác nhận (Confirmation Modal)**:
   - Xuất hiện khi Sinh viên yêu cầu đặt phòng tự học hoặc làm thủ tục hành chính.
   - Hiển thị tóm tắt thông tin: Họ tên, Mã sinh viên, Dịch vụ yêu cầu, Thời gian thực hiện.
   - 2 nút bấm rõ ràng: "Hủy bỏ" và "Xác nhận & Gửi yêu cầu".
3. **Màn hình Thông báo Chuyển giao Cán bộ (Handover Banner)**:
   - Hiển thị badge trạng thái màu vàng/cam thông báo: "Yêu cầu đã được chuyển tới Cán bộ Phòng Đào tạo (Mã Ticket: #TK-1024)".

### 2.2. Cổng Cán bộ Hỗ trợ (Staff Dashboard)
1. **Màn hình Danh sách Ticket (Kanban / Table)**:
   - Bộ lọc: Trạng thái (Chờ xử lý, Đang xử lý, Đã hoàn thành), Mức độ ưu tiên (Khẩn cấp, Bình thường), Phân loại (Hỏi đáp, Thủ tục, Khiếu nại).
2. **Màn hình Chi tiết Ticket & Ngữ cảnh**:
   - Bên trái: Lịch sử tóm tắt cuộc trò chuyện giữa Sinh viên và AI trước khi chuyển giao.
   - Bên phải: Khung phản hồi của Cán bộ, nút cập nhật trạng thái và nút "Hoàn tất xử lý".

---

## 3. Danh mục Hình ảnh Wireframe Export
Các hình ảnh bản vẽ wireframe sau khi xuất từ Figma sẽ được lưu tại thư mục:
`docs/gate-1/assets/`
- `student-chat-view.png`
- `student-confirmation-modal.png`
- `student-handover-notice.png`
- `staff-dashboard-tickets.png`
- `staff-ticket-detail.png`

