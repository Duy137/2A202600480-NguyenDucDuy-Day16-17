# Student: Nguyễn Đức Duy

**Date:** 2026-04-24

**Product idea:** AutoClip AI - Cỗ máy lắp ráp tự động chuyển đổi văn bản thành Video kiến thức.

## 1. MVP Boundary Sheet
**Riskiest Assumption:**

Người xem cuối (end-users) sẽ chấp nhận định dạng video ghép từ stock media (thay vì video quay thật) đủ lâu để Content Creators/L&D Teams thấy hiệu quả duy trì kênh và tiếp tục trả phí cho nền tảng.

### In-Scope (tối đa 3):

- [x] Phân tích kịch bản & Gán media tự động (Splitter/Director Agent) — test giả định: LLM có thể phân loại đúng ngữ cảnh chuyên môn để gán hình ảnh khớp > 80% mà không bị ảo giác.

- [x] Giao diện Review: Re-search & Upload Custom Media — test giả định: Tính năng Human-in-the-loop giúp user tin tưởng xuất bản video hơn là phó mặc hoàn toàn cho AI (Black-box generation).

- [x] Render ra MP4 9:16 có Auto-subtitle & Voice TTS — test giả định: Định dạng video dọc + phụ đề là định dạng dễ tiêu thụ nhất cho kiến thức ngắn, giúp user có sẵn sản phẩm đăng tải mạng xã hội ngay.

### Out-of-Scope:

- AI tự động sinh kịch bản (Script Writer) — lý do bỏ: User mục tiêu (L&D, Creator chuyên nghiệp) đã có sẵn kịch bản chất lượng cao, họ cần tốc độ "dựng hình", không cần AI "viết chữ" thay họ.

- Xuất video đa định dạng (16:9, 1:1) và Đa ngôn ngữ — lý do bỏ: Tăng độ phức tạp render hệ thống. MVP chỉ cần focus mảng video ngắn dọc (Shorts/Reels) ngôn ngữ Việt đang thịnh hành.

- Chỉnh sửa Timeline chi tiết (kéo thả từng frame) — lý do bỏ: Trượt khỏi định vị "Công cụ tự động hóa lắp ráp". Nếu user cần kéo thả từng frame, họ nên dùng phần mềm edit chuyên dụng như CapCut/Premiere.

### Non-Goals:

- Tuyệt đối KHÔNG sinh pixel video từ đầu bằng Generative AI (Sora, Runway) để tránh chi phí compute khổng lồ và thiếu tính kiểm soát.

- Tuyệt đối KHÔNG trở thành một mạng xã hội (Social Media) lưu trữ và chia sẻ video trực tuyến.

## 2. PRD Skeleton
### Problem Statement
Các Content Creators và Đội ngũ Đào tạo nội bộ (L&D) đang tốn hàng giờ đồng hồ mệt mỏi để tìm kiếm hình ảnh minh hoạ (B-roll) và canh thời gian ghép thủ công cho khớp với lời đọc, gây tốn kém nhân sự và không thể duy trì tần suất ra video đều đặn.

### Target User
Content Creators cá nhân làm tin tức/kiến thức trên TikTok/Shorts & L&D Managers tại doanh nghiệp SME - những người cần Tốc độ sản xuất nhanh nhưng yêu cầu độ chính xác chuyên môn cực cao.

### User Stories
**Story 1:**

As a Content Creator bận rộn, I want hệ thống tự động phân tách kịch bản của tôi và tự động gán media minh hoạ khớp với từng cảnh, so that tôi có thể sản xuất video tin tức mỗi ngày để giữ tương tác mà không bị kiệt sức vì khâu dựng hình.

**Story 2:**

As an L&D Manager, I want có thể xem trước (review) và tự tay tải lên video nội bộ công ty thay thế cho cảnh AI chọn sai trước khi xuất file, so that tôi đảm bảo bài giảng chính xác 100% về chuyên môn và bảo mật.

### AI-Specific
**Model Selection:**

- Model: OpenAI gpt-4o-mini (Logic text) và OpenAI TTS (Voice).

- Lý do chọn: Nhờ áp dụng kiến trúc Multi-Agent (Splitter & Director) để chia nhỏ tác vụ, chúng ta chỉ cần model nhỏ như 4o-mini là đủ để phân tích ngữ cảnh xuất sắc với chi phí API cực rẻ và tốc độ phản hồi tính bằng giây.

- Trade-offs chấp nhận: Model nhỏ không giỏi "sáng tạo văn học" sâu sắc (nhưng ta không cần vì text do user cấp sẵn).

- Trade-offs không chấp nhận: Dùng Local LLM yếu (gây ảo giác sai lệnh layout JSON) hoặc model khổng lồ (Claude Opus) làm âm biên lợi nhuận.

**Data Requirements:**

- Nguồn: Pexels API (Stock Media miễn phí bản quyền) và Custom Media của user.

- Owner: Third-party (Pexels) và First-party (User).

- Update frequency: Realtime (Pexels) và Per Job (User Data).

**Fallback UX:**

- Chiến lược: Graceful Handover (Trao quyền kiểm soát lại cho con người).

- Trigger: Khi Pexels API trả về 0 kết quả HOẶC khi AI "ảo giác" chọn hình không đúng ý đồ chuyên môn của user.

- Hành động: Hệ thống tuyệt đối KHÔNG báo lỗi Error 404/Crash. Tại màn hình Review, hiển thị một [Ảnh Placeholder xám dịu mắt] kèm thông báo: "AI chưa tìm được hình ảnh phù hợp. Bạn muốn thử từ khóa khác hay tải lên media riêng?".

- User options: Cung cấp nổi bật 2 nút: (1) Nhập từ khoá mới để AI Re-search, hoặc (2) Upload trực tiếp file từ máy tính. User cũng có thể đổi Scene Type về dạng nền an toàn (Text Background).

### Success Metrics
- **Primary metric:** Activation Rate (Tỷ lệ chuyển đổi từ màn hình Review -> bấm Render).

- **Ngưỡng thành công:** > 70%.

- **Timeframe đo lường:** 14 ngày đầu sau launch.

### Dependencies & Constraints
Rate limit của OpenAI/Pexels API, giới hạn dung lượng tải lên (Max 50MB/video) để tránh quá tải server.

## 3. Hypothesis Table
**Hypothesis 1 (cho tính năng In-Scope #2 - Giao diện Review Human-in-the-loop)**
"Chúng tôi tin rằng việc cung cấp giao diện Review để người dùng tự do Re-search hoặc Upload Media sẽ giúp Content Creators & L&D đạt được sự tự tin 100% về độ chính xác chuyên môn của video trước khi render.

Chúng tôi sẽ biết mình đúng khi thấy Tỷ lệ người dùng có thực hiện ít nhất 1 thao tác sửa đổi (re-search/upload/đổi type) trước khi bấm Render đạt > 50% trong 1 tháng đầu tiên."

- **Riskiest assumption:** Người dùng lười và kỳ vọng tool AI phải "hoàn hảo bằng 1 click". Nếu bắt họ phải review và tự upload hình, họ sẽ bỏ cuộc (churn).

- **Cách test cheapest:** Tracking Event/Heatmap tỷ lệ click giữa nút "Sửa cảnh" vs nút "Bỏ qua & Render Ngay".

**Hypothesis 2 (nếu có)**
Không có.

## 4. PMF Scorecard
**Aha Moment:**

Khi người dùng paste kịch bản thô, thấy timeline tự động hiện ra. Họ phát hiện 1 tấm hình AI chọn sai, họ bấm "Re-search/Upload" và hình ảnh mới CẬP NHẬT NGAY LẬP TỨC vào kịch bản mà không cần thoát ra phần mềm khác. Họ nhận ra mình nắm quyền kiểm soát tuyệt đối trên 1 luồng auto.

**Actionable Metric:**

Retention Rate: Tỷ lệ người dùng quay lại và Render thành công >= 2 video riêng biệt trong vòng 7 ngày đầu tiên sau khi đăng ký (Đo qua database `jobs` status=rendered).

**PMF Method:**

Sean Ellis Test (Gửi survey hỏi "Bạn sẽ cảm thấy thế nào nếu không thể dùng AutoClip nữa?" sau khi họ tạo video thứ 3).

- **Ngưỡng thành công:** > 40% chọn "Rất thất vọng".

**Vanity Metrics tôi sẽ không dùng:**

Tổng số lượt Đăng ký tài khoản (không dùng thật) và Tổng số lượng Video Scenes được AI sinh ra (AI sinh ra nhiều nhưng user vứt đi không render thì vô giá trị).

## 5. AI Critique Log
**Điểm AI chỉ ra:**

- [Issue 1 - Root cause render lỗi] — Action: Accept — Lý do: AI Architect ban đầu đoán lỗi không lưu media khi render là do quên gọi SQL update. Nhưng AI Builder phản biện do code dùng shallow copy `dict(job.props)` khiến scenes array bị shared reference. Cần áp dụng deep copy. Giúp fix tận gốc bug số 1.

- [Issue 2 - Video Jitter] — Action: Partial — Lý do: AI đề xuất bỏ flag `--concurrency=1` của Remotion để render đa luồng cho nhanh. Tuy nhiên, qua log test phát hiện đa luồng gây lỗi seek frame (giật hình) cho stock video. Chấp nhận trade-off render chậm (1 luồng) nhưng mượt, và đổi sang component `<OffthreadVideo>`.

- [Issue 3 - Scope Creep] — Action: Reject — Lý do: AI gợi ý thêm tính năng tự viết kịch bản (Script Gen) ngay từ đầu để dễ thu hút user. Tuy nhiên điều này vi phạm ranh giới đỏ vì tệp khách hàng B2B đã có sẵn kịch bản nội bộ, làm thêm chỉ tốn thời gian MVP.

**Thay đổi lớn nhất giữa Version A và Version B:**

Tái định vị hoàn toàn từ một công cụ "One-click Video Generator" (rủi ro cao, tỷ lệ bỏ cuộc lớn vì AI ảo giác) sang vị thế "Automated Assembly Pipeline + Human-in-the-loop" (Tôn trọng sự can thiệp của con người qua Review UI). Điều này thay đổi cốt lõi Fallback UX (Thay vì crash, trao quyền cho user sửa lỗi) và định nghĩa lại Aha Moment của sản phẩm.

## 6. Self-assessment
**Mắt xích nào trong [MVP Boundary, PRD, Hypothesis, PMF] bạn đang yếu nhất?**

Hypothesis Validation (Cách test giả định rủi ro nhất). Giả định cốt lõi "Khán giả (End-users) có chịu xem video ghép stock này không?" rất khó đo lường trực tiếp, vì tool của ta phục vụ B2B2C (Content Creators). Chúng ta hiện chỉ đo được gián tiếp qua Retention Rate của Creator.

**Open questions bạn muốn giải đáp tiếp:**

- Làm sao để thiết kế Pricing Model cân đối được biến phí API (LLM + TTS + Băng thông), đặc biệt khi user test (review) liên tục, nghe thử TTS nhiều lần nhưng không chịu bấm Render (lúc này chưa charge phí được)?

- Nên hay không nên ép Watermark cho gói Free, và nó có cản trở "Aha Moment" khi user chia sẻ video lên mạng xã hội không?