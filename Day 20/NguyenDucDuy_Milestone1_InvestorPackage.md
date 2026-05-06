# MILESTONE 1: INVESTOR-READY PACKAGE
**Dự án:** AutoClip AI
**Founder:** Nguyen Duc Duy

---
<div style="page-break-after: always;"></div>

## [Trang 1] Cover & Elevator Pitch

### AutoClip AI
*Cỗ máy lắp ráp video tự động cho Content Creators & L&D Teams.*

### Twitter Pitch (The Hook)
Bọn em là AutoClip AI. Bọn em giúp L&D teams giải quyết việc mất 3h/ngày tìm B-roll dựng clip bằng cỗ máy ghép video tự động từ kịch bản, kết hợp duyệt tay (Human-in-the-loop). Giá vốn siêu rẻ 1.600đ/clip, margin >60%. Gọi $200K Seed để scale lên 500 khách trả phí đầu tiên.

### Elevator Pitch (45 giây)
"Xin chào, bọn em là AutoClip AI. Bọn em giúp các Content Creators và đội ngũ đào tạo nội bộ giải quyết bài toán tốn 3 giờ mỗi ngày để săn lùng hình ảnh và dựng video kiến thức.

Giải pháp của bọn em là một cỗ máy lắp ráp tự động từ kịch bản, nhưng tuyệt đối giữ quyền kiểm duyệt cho người dùng. Khác với các AI sinh video đắt đỏ và hay sai lệch, AutoClip sử dụng dữ liệu có sẵn để ép giá vốn sản xuất xuống chỉ còn 1.600 đồng cho một video 1 phút, mang lại biên lợi nhuận trên 60% cho gói thuê bao.

Bọn em đang gọi 200.000 đô la Seed để scale tập khách hàng trả phí đầu tiên."

---
<div style="page-break-after: always;"></div>

## [Trang 2-5] Pitch Memo, Market Analysis & PRD

### 1. Pitch Memo: The Problem & The Insight
**The Problem:**
Content Creators và nhân sự đào tạo nội bộ (L&D) đang tốn từ 2-3 giờ mỗi ngày để "đãi cát tìm vàng" — săn lùng hình ảnh minh hoạ (B-roll) trên mạng và căng mắt đo thời gian sao cho khớp với giọng đọc. Việc này khiến họ kiệt sức và không thể duy trì tần suất ra video kiến thức/tin tức.

**The Insight:**
Mọi người nghĩ tương lai của video là dùng AI để sinh ra hình ảnh từ con số 0 (như Sora, Runway). Nhưng sự thật là: Video kiến thức cần sự CHÍNH XÁC tuyệt đối với chi phí cực thấp, chứ không cần những đoạn phim điện ảnh dễ bị sai lệch (ảo giác). "Lắp ráp dữ liệu có sẵn" (Assembly) mới là chân ái của video kiến thức, không phải Pixel Generation.

**Why Now:**
Nhu cầu tiêu thụ nội dung nhanh dạng dọc (Shorts, Reels, TikTok) bùng nổ mạnh mẽ. LLM nhỏ gọn (như GPT-4o-mini) và TTS đã đủ thông minh để hiểu ngữ cảnh kịch bản và thực hiện lắp ráp tự động với chi phí API cực thấp.

### 2. Phân tích Khách hàng (Customer Segment)
*   **Segment name:** Knowledge Creators & L&D Teams.
*   **Recurring workflow:** Viết/tổng hợp script -> Thu âm -> Tìm kiếm/tạo hình ảnh minh hoạ -> Dựng video.
*   **Pain moment:** Khi có tin tức nóng cần ra video ngay lập tức nhưng dựng video mất quá nhiều thời gian.
*   **Need Map (JTBD):**
    *   *Tốc độ & Tự động hoá:* Cần chuyển đổi văn bản thành video ngay lập tức.
    *   *Tính chính xác:* Hình ảnh minh hoạ phải khớp chính xác với ngữ cảnh.
    *   *Tính tuỳ chỉnh linh hoạt (Human-in-the-loop):* Có thể can thiệp nhanh chóng để tải lên media riêng nếu AI chọn chưa đúng ý.

### 3. Product Requirements (PRD Cốt lõi)
**Luồng hoạt động của AutoClip AI:**
1.  **Nhập kịch bản (Text Input):** Dán đoạn văn bản đã chuẩn bị sẵn.
2.  **LLM Parser (Multi-Agent Splitter):** AI chẻ nhỏ văn bản thành các cảnh logic, gán loại cảnh và tạo prompt tìm kiếm hình ảnh. Sử dụng `gpt-4o-mini`.
3.  **Tổng hợp giọng nói (TTS):** Sử dụng Vbee/OpenAI TTS để có giọng đọc tự nhiên.
4.  **Auto-matching Media:** Hệ thống tự động tìm và gán video/hình ảnh stock từ Pexels (hoặc kho Local) dựa trên prompt.
5.  **Review UI (Human-in-the-loop - USP):** Giao diện cho phép xem trước, đổi hình (Re-search) hoặc tải hình ảnh nội bộ (Upload) cho từng phân cảnh. Tuyệt đối không để AI "ảo giác" làm sai lệch kiến thức.
6.  **Serverless Render (Remotion Lambda):** Xuất video 9:16 siêu tốc độ, tính tiền theo giây.

### 4. Ranh giới MVP & Moat Hypothesis (Phòng thủ)
*   **In-Scope:** Dựng luồng Auto-Assembly từ Text -> Cắt cảnh -> Tìm ảnh -> Ghép giọng -> Render. Giao diện Review tay là bắt buộc.
*   **Out-of-Scope (Phase 2):** Sinh kịch bản tự động, Auto-publish, Đa ngôn ngữ, Đa định dạng 16:9.
*   **Non-Goals:** Không làm tool edit video chuyên nghiệp (như CapCut), không làm AI vẽ video từ pixel (như Sora).
*   **Moat Hypothesis:** Thuật toán Multi-Agent hiểu ngữ cảnh để tìm hình ảnh sẽ ngày càng chính xác nhờ học từ thao tác Re-search/Upload của người dùng. Cùng với đó là việc sở hữu Kho Local Media độc quyền giảm giá vốn.

---
<div style="page-break-after: always;"></div>

## [Trang 6-7] Financial Model & Unit Economics

### 1. Dự toán chi phí Production (COGS) Bottom-Up
Để chạy mô hình SaaS phục vụ scale lớn mà biên lợi nhuận vẫn dày, chúng tôi tối ưu kiến trúc để ép chi phí sản xuất xuống cực thấp (Tính cho video 1 phút, cấu trúc 10 phân cảnh):
*   **LLM (gpt-4o-mini):** ~50 VNĐ.
*   **TTS (Vbee VIP+):** ~450 VNĐ.
*   **Media (Local S3):** ~100 VNĐ (thay vì mua API Stock trả phí).
*   **Render (AWS Lambda):** ~1.000 VNĐ.
*   **=> Tổng giá vốn (COGS) / Video 1 Phút = 1.600 VNĐ.**

### 2. Mô hình giá & Unit Economics
*   **Bán gói Thuê bao (Subscription - Hướng chính):** Đẩy gói **399.000đ/tháng**, cho user tạo tối đa 100 video VIP (1 phút/video). Dành cho các creator làm kênh kiến thức/tin tức cần cày cuốc số lượng lớn (3-4 video/ngày).
*   **Lãi gộp (Gross Profit):** Nếu user xài max 100 video, giá vốn là 160.000đ. Startup lãi gộp 239.000đ trên mỗi khách hàng gia hạn mỗi tháng. Margin đạt ~60%.
*   **CAC (Chi phí thu hút khách hàng):** 150.000 VNĐ — Đạt được nhờ chiến lược "Dogfooding" (dùng chính AutoClip tạo video viral trên TikTok/Shorts thay vì đốt tiền Ads).
*   **LTV (Giá trị vòng đời khách hàng):** Với Retention 70%, trung bình mỗi khách ở lại khoảng 3.3 tháng → LTV = 399.000 × 3.3 = **khoảng 1.317.000 VNĐ**.
*   **LTV/CAC Ratio:** 1.317.000 / 150.000 = **khoảng 8.8x** (Cực kỳ healthy, chuẩn SaaS >3x).
*   **Payback Period:** Khách hàng đóng 399k ngay tháng đầu đã bù xong CAC (150k) và COGS (160k), lãi ngay 89k → **Payback < 1 tháng.**

### 3. Số liệu giả định mô hình tài chính (Financial Assumptions)
*   **Thị trường (TAM):** 130,000 khách hàng tiềm năng.
*   **Adoption Rate:** 0.2% (Opt) / 0.1% (Base) / 0.05% (Pess) — Rất thực tế cho startup Bootstrapped.
*   **Fixed Costs:** Lương (40M), Vận hành (10M), Marketing (20M).
*   **Vốn đầu tư ban đầu:** 200,000,000 VNĐ. Tiền mặt ban đầu: 400,000,000 VNĐ.

### 4. Decision Note (Bảo vệ luận điểm gọi vốn)
*   **Về ARPU (399.000đ/100 video):** Định giá theo mô hình Hybrid Credit-based, tính Bottom-Up từ Unit Cost của 1 phút video. Việc khóa cứng số lượng 100 video giúp chặn rủi ro từ Power Users, cố định giá vốn tối đa ở mức 160.000đ/user/tháng. Đảm bảo Gross Margin luôn ~60%.
*   **Về chiến lược Dogfooding:** Đội ngũ sẽ dùng chính sản phẩm AutoClip AI để tự động sản xuất hàng trăm video kiến thức/tin tức mỗi tháng, tạo phễu Viral Marketing Organic trên TikTok/Shorts. Chiến lược này vừa chứng minh sản phẩm hoạt động thật, vừa giữ CAC ở mức 150.000đ.

---
<div style="page-break-after: always;"></div>

## [Trang 8] Roadmap (Now/Next/Later) & OKRs

### 1. Roadmap (Now/Next/Later)
*Dựa trên kết quả RICE & Ma trận 2x2 Value-Effort. Tập trung giải quyết vấn đề, không chốt ngày tháng.*

*   **🟢 NOW — Quick Wins (RICE Score cao nhất):**
    *   **Vấn đề 1:** User tốn hàng giờ chẻ kịch bản và tìm hình → Giải quyết bằng Multi-Agent Splitter + Auto-match Media.
    *   **Vấn đề 2:** User thiếu tin tưởng AI chọn sai hình → Giải quyết bằng giao diện Human-in-the-loop (đổi hình, upload).
    *   **Vấn đề 3:** User cần giọng đọc tự nhiên Tiếng Việt → Giải quyết bằng Vbee TTS.
*   **🟡 NEXT — Strategic Bet (Đầu tư moat dài hạn):**
    *   **Vấn đề 1:** Phụ thuộc Pexels API gây rủi ro rate limit khi scale → Giải quyết bằng Local Media Library 100k assets trên S3.
    *   **Vấn đề 2:** Cần đo lường hành vi user → Giải quyết bằng bảng Analytics cơ bản.
*   **🔴 LATER — Vision lớn:**
    *   **Vấn đề 1:** Khách hàng L&D đa quốc gia cần đào tạo đa ngôn ngữ → Multi-language AI Dubbing.
    *   **Vấn đề 2:** Creators cần video cho nhiều nền tảng → Auto-resize Engine (16:9, 1:1).
*   *Backlog:* Auto-publish lên TikTok/Shorts (Fill-in, làm khi rảnh). AI Script Writer (Non-starter, loại bỏ).

### 2. OKRs cho cột NOW
**🏆 Objective:** "Trở thành cỗ máy lắp ráp video tự động không thể thiếu cho Content Creators và L&D team tại Việt Nam."
*   **📈 KR1 (Leading):** Có ít nhất 50 paying user sử dụng AutoClip để xuất thành công ≥ 3 video/tuần (Đo lường sự hình thành thói quen).
*   **💰 KR2 (Lagging):** Đạt doanh thu $300 MRR từ 20 khách hàng trả phí đầu tiên (Validation sự sẵn sàng trả tiền).
*   **🛡️ KR3 (Quality):** Monthly Retention Rate đạt ≥ 70% (Đảm bảo sản phẩm đã trở thành công cụ không thể thiếu — dấu hiệu Product-Market Fit).

---
<div style="page-break-after: always;"></div>

## [Trang 9] Dependency Map & Critical Path

### 1. Dependency Map (3 rủi ro ngoại vi & Plan B)
*   **OpenAI API (`gpt-4o-mini`)**
    *   *Worst-case:* Siết rate limit, sập server toàn cầu → luồng phân tích kịch bản tê liệt.
    *   *Plan B:* Chuyển sang Claude 3.5 Haiku. Hệ thống đã có lớp trừu tượng cho phép đổi nhà cung cấp.
    *   *Cost:* ~0 VNĐ phát sinh + 1-2 ngày công điều chỉnh prompt.
*   **Pexels API (Kho Media Stock)**
    *   *Worst-case:* Thu hồi API Key hoặc giới hạn gọi → video không có hình minh hoạ.
    *   *Plan B:* Chuyển sang kho Local Media Library tự lưu trữ trên S3 (đã cào sẵn 5.000-10.000 video).
    *   *Cost:* ~500.000 VNĐ/tháng S3 + 3-5 ngày công cào dữ liệu ban đầu.
*   **Vbee TTS (Giọng đọc Tiếng Việt)**
    *   *Worst-case:* Server quá tải, độ trễ tăng vọt → trải nghiệm sụp đổ.
    *   *Plan B:* Chuyển sang OpenAI TTS (giọng không chuẩn Việt bằng nhưng giữ trải nghiệm mượt mà).
    *   *Cost:* ~0 VNĐ phát sinh + 1 ngày công đổi endpoint.

### 2. Critical Path (Đường găng dự án cột NOW)
*Trễ 1 ngày trên Critical Path = Trễ Launch 1 ngày.*

1.  **[CRITICAL]** Xây dựng AI Splitter Pipeline (Test độ chính xác phân cảnh).
2.  **[CRITICAL]** Tích hợp nguồn Media & Giọng đọc.
3.  **[CRITICAL]** Xây dựng giao diện Human-in-the-loop (Xem trước, đổi hình, upload). *(Blocking task 4)*
4.  **[CRITICAL]** Tích hợp quy trình xuất video Serverless.
5.  **[CRITICAL]** End-to-end Testing & Launch bản Alpha.

**Sơ đồ chuỗi Critical Path:**
`AI Splitter Pipeline` ➔ `Media & TTS Integration` ➔ `Review UI (Human-in-the-loop)` ➔ `Serverless Render` ➔ `Alpha Launch`

---
### PHỤ LỤC
*   [Chi tiết Financial Model Excel Day 18](../Day%2018/Day18-AI-Product-Finance-Model.xlsx)
*   [Chi tiết PRD Day 17](../Day%2017/PRD.md)
