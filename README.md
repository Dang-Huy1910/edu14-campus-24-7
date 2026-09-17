# Campus 24/7 – Trợ lý AI Vận hành Học vụ 24/7

> **Đề tài**: EDU-14 – AI Vận hành & Hỗ trợ Học vụ  
> **Nhóm thực hiện**: Team EDU-14  
> **Hồ sơ Gate 1**: [docs/gate-1/](docs/gate-1/README.md)

---

## 📌 Giới thiệu Đề tài

**Campus 24/7** là trợ lý AI vận hành học vụ dành cho sinh viên, có khả năng:
1. **Tra cứu quy chế có nguồn trích dẫn chính thức**: Hỗ trợ giải đáp 24/7 từ tài liệu quy chế nhà trường, loại bỏ hoàn toàn hiện tượng trả lời bịa đặt (anti-hallucination).
2. **Tiếp nhận yêu cầu có xác nhận người dùng (Human confirmation)**: Tạo ticket hỗ trợ, đặt phòng tự học hoặc gửi yêu cầu thủ tục sau khi sinh viên chủ động xác nhận thông tin.
3. **Chuyển giao cán bộ (Human-in-the-loop - HITL)**: Tự động phát hiện các ca nhạy cảm (khiếu nại điểm, thiếu nguồn, rủi ro) và chuyển tiếp ngay tới cán bộ quản trị kèm ngữ cảnh tóm tắt.

---

## 📂 Cấu trúc Repository

```text
edu14-campus-24-7/
├── README.md                      # Giới thiệu tổng quan dự án
├── .gitignore                     # Cấu hình bỏ qua file nhạy cảm và cache
├── docs/
│   ├── gate-1/                    # Toàn bộ hồ sơ nộp Gate 1
│   │   ├── README.md              # Bảng index điều hướng Gate 1
│   │   ├── 01-brief.md            # Bản tóm tắt đề tài (Brief 1 trang)
│   │   ├── 02-prd.md              # Tài liệu yêu cầu sản phẩm (PRD)
│   │   ├── 03-ui-flow.md          # Luồng giao diện & Wireframe
│   │   ├── Phan-cong-nhiem-vu.md  # Kế hoạch phân công nhiệm vụ 4 thành viên
│   │   └── assets/                # Hình ảnh giao diện wireframe và diagrams
│   └── reference/                 # Tài liệu nghiên cứu & phân tích nền tảng
│       ├── EDU-14-Campus-24-7.md
│       ├── MO-TA-SAN-PHAM-EDU-14.md
│       ├── EDU-14-KHAC-BIET-KY-TRUOC.md
│       ├── LY-DO-CHON-EDU-14.md
│       └── EDU-14-Gate-1-Plan.md
├── ai-logs/                       # Quản trị và ghi nhận nhật ký sử dụng AI
│   ├── README.md                  # Quy định ghi nhận AI Log
│   └── template.md                # Biểu mẫu log chuẩn
└── src/                           # Khung mã nguồn ứng dụng
    └── README.md
```

---

## 🚀 Trạng thái & Kế hoạch Nộp bài

- **Gate 1**: [Xem hồ sơ nộp bài Gate 1 tại đây](docs/gate-1/README.md)
- **Kế hoạch phân công nhiệm vụ**: [docs/gate-1/Phan-cong-nhiem-vu.md](docs/gate-1/Phan-cong-nhiem-vu.md)
- **Nhật ký AI**: [ai-logs/](ai-logs/README.md)

