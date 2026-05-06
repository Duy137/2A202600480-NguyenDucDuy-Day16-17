# 🗺️ Roadmap AutoClip AI (Now/Next/Later)

> **Quy tắc:** KHÔNG ghi ngày tháng. Tập trung giải quyết vấn đề (Problem), không phải tính năng (Feature).
> **Tham chiếu:** Sắp xếp dựa trên kết quả RICE & Ma trận 2x2 Value-Effort (xem `rice_matrix.md`).

| Ô RICE 2x2 | Tính năng | RICE Score | → Roadmap |
|---|---|---|---|
| 🟢 Quick Win | Tích hợp TTS Tiếng Việt | 1000 | **NOW** |
| 🟢 Quick Win | Giao diện Human-in-the-loop | 800 | **NOW** |
| 🔴 Strategic Bet | Kho Local Media Library 100k | 300 | **NEXT** |
| 🟡 Fill-in | Auto-publish lên TikTok/Shorts | 20 | *Backlog* — Làm khi rảnh |
| 🗑️ Non-starter | AI Script Writer (Tự sinh kịch bản) | 12.5 | *Loại bỏ* — Không giải quyết đúng pain-point |

---

## 🟢 NOW (Đang làm — Quick Wins + RICE Score cao nhất)
*Tập trung giải quyết rào cản thao tác thủ công, chứng minh giá trị cốt lõi của sản phẩm.*

*   **Vấn đề 1:** User tốn hàng giờ để chẻ nhỏ kịch bản và tìm hình minh hoạ khớp từng đoạn.
    *   *Giải quyết bằng:* Tích hợp Multi-Agent LLM (Splitter & Director) kết hợp tìm kiếm Auto-match qua Pexels API.
    *   *(Tham chiếu: Day 16 Need #1 "Tốc độ và Tự động hoá quy trình", Day 17 PRD User Story #1)*
*   **Vấn đề 2:** User thiếu sự tin tưởng vào AI, họ sợ AI chọn sai ảnh dẫn đến sai lệch kiến thức chuyên môn.
    *   *Giải quyết bằng:* Xây dựng quy trình Review "Human-in-the-loop" (cho phép xem trước, tìm hình khác, tự tải hình lên).
    *   *(Tham chiếu: Day 16 Need #3 "Human-in-the-loop Customization", Day 17 PRD User Story #2 & Fallback UX)*
*   **Vấn đề 3:** User muốn video có giọng đọc trôi chảy, tự nhiên (Tiếng Việt) thay vì giọng robot.
    *   *Giải quyết bằng:* Tích hợp Vbee TTS cho khách VIP, Edge-TTS miễn phí cho user Free.
    *   *(Tham chiếu: Day 18 cost_estimation — Phương án C "Chia tier cho Giọng đọc")*

---

## 🟡 NEXT (Sẽ làm — Strategic Bets từ 2x2)
*Tập trung bảo vệ biên lợi nhuận và giảm thiểu rủi ro để chuẩn bị scale up.*

*   **Vấn đề 1:** Phụ thuộc vào Pexels API quá nhiều gây rủi ro rate limit và đội chi phí khi scale lên 500 khách hàng.
    *   *Giải quyết bằng:* Cào dữ liệu và xây dựng kho Local Media Library 100k assets lưu trữ trên S3, thay thế dần API bên thứ 3.
    *   *(Tham chiếu: Day 18 cost_estimation — Phương án A "Cắt hẳn tiền mua API Stock Video", Day 19 Pitch Memo — "THE ASK: mở rộng Local Media Library lên 100,000 assets")*
*   **Vấn đề 2:** Khách hàng cần đo lường video nào hiệu quả để điều chỉnh chiến lược nội dung.
    *   *Giải quyết bằng:* Bảng Analytics cơ bản (Theo dõi lượt tạo video, chủ đề phổ biến, số credits còn lại).

---

## 🔴 LATER (Tầm nhìn dài hạn — Vision lớn, chưa technically khả thi)
*Mở rộng thị trường, tầm nhìn Pitching với VC.*

*   **Vấn đề 1:** Khách hàng L&D đa quốc gia cần tài liệu đào tạo cho chi nhánh nước ngoài.
    *   *Có thể giải quyết bằng:* Multi-language AI Dubbing (Tự động dịch kịch bản, xuất giọng đọc bản ngữ).
    *   *(Tham chiếu: Day 17 MVP_SCOPE Out-of-Scope — "Đa ngôn ngữ Multi-language")*
*   **Vấn đề 2:** Content Creators muốn tận dụng nội dung cho nhiều nền tảng (YouTube ngang, FB vuông).
    *   *Có thể giải quyết bằng:* Auto-resize Video Engine (Hỗ trợ 16:9, 1:1) ngoài định dạng 9:16 hiện tại.
    *   *(Tham chiếu: Day 17 MVP_SCOPE Out-of-Scope — "Đa định dạng xuất video")*
