# 🕸️ Dependency Map & Critical Path

> **Câu hỏi sống còn:** Nếu OpenAI sập ngày mai, dự án AutoClip AI còn chạy được không?

---

## 1. Dependency Map (3 rủi ro ngoại vi có thể giết dự án trong 30 ngày tới)

### Dependency 1: OpenAI API (`gpt-4o-mini`)
*   **Worst-case scenario:** OpenAI siết rate limit hoặc sập server toàn cầu, khiến luồng phân tích kịch bản (Splitter) bị tê liệt hoàn toàn — không thể tạo bất kỳ video nào.
*   **Plan B:** Chuyển sang Claude 3.5 Haiku của Anthropic. Hệ thống đã được thiết kế với lớp trừu tượng (abstract layer) cho phép thay đổi nhà cung cấp mà không ảnh hưởng đến luồng xử lý.
*   **Cost của Plan B:** ~0 VNĐ chi phí phát sinh (giá API tương đương) + 1-2 ngày công để điều chỉnh prompt và test lại độ chính xác.

### Dependency 2: Pexels API (Kho Media Stock)
*   **Worst-case scenario:** Pexels thu hồi API Key hoặc giới hạn số lần gọi, khiến video tạo ra không có hình ảnh minh hoạ — sản phẩm mất giá trị cốt lõi.
*   **Plan B:** Chuyển sang kho Local Media Library tự lưu trữ trên Amazon S3. Trong giai đoạn MVP, đã cào sẵn 5.000-10.000 video miễn phí từ Pexels/Pixabay (tham chiếu: Day 18 cost_estimation — Phương án A "Cắt hẳn tiền mua API Stock Video").
*   **Cost của Plan B:** ~500.000 VNĐ/tháng tiền duy trì S3 (lưu trữ ~50GB) + 3-5 ngày công ban đầu để cào dữ liệu và chạy auto-tagging.

### Dependency 3: Vbee TTS (Giọng đọc Tiếng Việt)
*   **Worst-case scenario:** Server Vbee quá tải, độ trễ tăng vọt khiến quá trình tạo video kéo dài hàng chục phút — trải nghiệm người dùng sụp đổ.
*   **Plan B:** Chuyển sang OpenAI TTS (giọng không chuẩn Tiếng Việt bằng nhưng đảm bảo trải nghiệm người dùng không bị đứt gãy). Đầu tư ban đầu cho Vbee chỉ 1.300.000 VNĐ (tham chiếu: Day 18 cost_estimation — mục "Chi phí đầu tư ban đầu cho Vbee API"), nên rủi ro tài chính nếu phải bỏ Vbee là rất nhỏ.
*   **Cost của Plan B:** ~0 VNĐ phát sinh (OpenAI TTS tính theo usage, giá tương đương ~450 VNĐ/phút) + 1 ngày công để đổi endpoint.

---

## 2. Critical Path (Đường găng dự án cho cột NOW)

*Chuỗi task dài nhất & bắt buộc tuần tự. Trễ 1 ngày trên Critical Path = Trễ Launch 1 ngày.*

1.  **[CRITICAL]** Xây dựng AI Splitter Pipeline — Test độ chính xác phân cảnh của LLM (Tham chiếu: PRD Day 17 — Multi-Agent Splitter & Director).
2.  **[CRITICAL]** Tích hợp Pexels API & Vbee TTS — Kết nối nguồn media và giọng đọc (Tham chiếu: PRD Day 17 — Data Source & TTS).
3.  **[CRITICAL]** Xây dựng giao diện Human-in-the-loop — UI cho phép xem trước, đổi hình, upload media nội bộ (Tham chiếu: PRD Day 17 — Fallback UX). *(Blocking task 4)*
4.  **[CRITICAL]** Tích hợp quy trình xuất video qua Serverless Render (Tham chiếu: Day 18 — Phương án B "Render Serverless").
5.  **[CRITICAL]** End-to-end Testing & Launch bản Alpha cho 50 user pilot.
6.  *[Non-critical]* Thiết kế Landing Page & Tích hợp cổng thanh toán (Giai đoạn đầu có thể cho xài free hoặc chuyển khoản tay).
7.  *[Non-critical]* Thiết lập bảng Analytics cơ bản để theo dõi hành vi người dùng.

**Sơ đồ chuỗi Critical Path (Highlight đỏ):**
`AI Splitter Pipeline` ➔ `Media & TTS Integration` ➔ `Review UI (Human-in-the-loop)` ➔ `Serverless Render` ➔ `Alpha Launch`
