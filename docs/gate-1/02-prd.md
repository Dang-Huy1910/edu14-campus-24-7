# Tài liệu Yêu cầu Sản phẩm (PRD) – Campus 24/7

> **Dự án**: Campus 24/7 – Trợ lý AI Vận hành Học vụ 24/7  
> **Chủ trì hoàn thiện**: Thành viên 3 (Lead Product & Integration)  
> **Đóng góp kỹ thuật**: Thành viên 1 (Data & API Specs), Thành viên 2 (AI & RAG Architecture)

---

## 1. Tổng quan Sản phẩm & Mục tiêu
Campus 24/7 là hệ thống trợ lý học vụ AI đa tác tử tích hợp cơ chế Human-in-the-loop (HITL), hỗ trợ giải đáp quy chế đào tạo, tự động hóa quy trình tiếp nhận dịch vụ một cửa và chuyển giao cán bộ cho các tình huống nhạy cảm.

---

## 2. Đối tượng Người dùng & Chân dung (User Personas)
### 2.1. Sinh viên (Primary Persona)
- **Hành vi**: Cần tra cứu nhanh ngoài giờ hành chính, muốn nhận câu trả lời chắc chắn không bị phạt quy chế, muốn đặt lịch/phòng tiện lợi.
- **Nỗi đau (Pain Points)**: Tìm quy chế khó khăn, gọi hotline ngoài giờ không ai bắt máy, không biết thủ tục khiếu nại điểm đi về đâu.

### 2.2. Cán bộ Một cửa Học vụ (Secondary Persona)
- **Hành vi**: Tiếp nhận hàng trăm câu hỏi giống nhau mỗi kỳ tuyển sinh/thi cử, tốn thời gian xử lý thủ công.
- **Nỗi đau**: Bị quá tải bởi câu hỏi lặp lại, thiếu công cụ gom nhóm và phân loại ticket khẩn cấp.

---

## 3. Danh mục Tính năng & Tiêu chí Nghiệm thu (User Stories & Acceptance Criteria)

### US-01: Tra cứu quy chế có nguồn trích dẫn
- **Mô tả**: Là sinh viên, tôi muốn hỏi về quy định thôi học, học bổng, điểm rèn luyện và nhận được câu trả lời kèm tên văn bản, số điều.
- **Acceptance Criteria**:
  - [ ] Trả về nội dung giải đáp ngắn gọn, dễ hiểu.
  - [ ] Đi kèm thẻ Citation: Tên quy chế, số điều, link hoặc số trang PDF tham chiếu.
  - [ ] Nếu không tìm thấy thông tin trong tài liệu: Hệ thống thông báo rõ không có dữ liệu và đề xuất tạo ticket hỗ trợ.

### US-02: Thực hiện yêu cầu có xác nhận người dùng
- **Mô tả**: Là sinh viên, tôi muốn đặt phòng tự học hoặc xin cấp giấy xác nhận trực tiếp qua chat.
- **Acceptance Criteria**:
  - [ ] Agent trích xuất các thông tin cần thiết: Họ tên, MSSV, loại giấy tờ/thời gian đặt phòng.
  - [ ] Agent hiển thị hộp thoại Tóm tắt & Xác nhận (Confirmation Modal).
  - [ ] Chỉ khi sinh viên ấn nút "Xác nhận", hệ thống mới gọi API tạo ticket hoặc đặt chỗ.

### US-03: Chuyển giao cán bộ xử lý (Human-in-the-loop)
- **Mô tả**: Khi gặp tình huống nhạy cảm (khiếu nại điểm, stress thi cử, quy chế mập mờ), hệ thống tự động chuyển giao cán bộ.
- **Acceptance Criteria**:
  - [ ] Agent nhận diện tín hiệu cảm xúc/từ khóa nhạy cảm.
  - [ ] Hiển thị thông báo minh bạch: "Trường hợp này cần cán bộ chuyên trách hỗ trợ, tôi đã tạo ticket chuyển phòng Đào tạo".
  - [ ] Cán bộ nhìn thấy ticket kèm tóm tắt cuộc trò chuyện trên Dashboard.

---

## 4. Kiến trúc Dữ liệu & Hợp đồng API (Data & API Specs)
*(Được đóng góp bởi Thành viên 1)*

### 4.1. Entity Schema
- **Ticket**: `id`, `student_id`, `category` (lookup | action | complaint), `status` (open | pending_officer | resolved), `priority`, `summary`, `created_at`.
- **StudentContext**: `mssv`, `full_name`, `email`, `cohort`, `faculty`.

### 4.2. API Endpoints Mock
- `POST /api/v1/chat`: Nhận tin nhắn sinh viên, trả về câu trả lời RAG hoặc đề xuất hành động.
- `POST /api/v1/tickets/confirm`: Xác nhận và lưu trữ ticket vào cơ sở dữ liệu.
- `GET /api/v1/officer/tickets`: Lấy danh sách ticket theo bộ lọc và mức độ ưu tiên.

---

## 5. Kiến trúc AI, Luồng RAG & Guardrails
*(Được đóng góp bởi Thành viên 2)*

### 5.1. Luồng RAG & Chống ảo giác
- **Indexing**: Văn bản quy chế được chuẩn hóa định dạng Markdown/Text, phân đoạn (chunking 500 tokens, overlap 50 tokens), gán metadata văn bản.
- **Grounding Rule**: LLM chỉ được tổng hợp câu trả lời dựa trên context đã retrieve, cấm tự suy diễn quy chế không có trong dữ liệu.

### 5.2. Agent Decision & Safety Guardrails
- **Read vs Write Barrier**: Tra cứu quy chế là thao tác Read-only; tạo ticket/đặt phòng là Write operation bắt buộc qua cổng xác nhận người dùng.
- **Safety Gate**: Phát hiện các yêu cầu can thiệp trái phép (sửa điểm, xóa môn) $\rightarrow$ Từ chối và ghi log cảnh báo.

---

## 6. Tiêu chí Đánh giá & Chỉ số Thành công (Evaluation Metrics)
| Metric | Mục tiêu | Phương pháp đo lường |
|:---|:---:|:---|
| **Citation Precision** | $\ge 70\%$ | Kiểm thử trên bộ 50 câu hỏi quy chế chuẩn |
| **Tool Execution Precision** | $\ge 90\%$ | Đo lường tỷ lệ tạo đúng tham số qua API mock |
| **Sensitive Case Handover** | $100\%$ | Kiểm thử trên bộ 15 kịch bản nhạy cảm / khiếu nại |

