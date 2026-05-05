
# Day 16 Submission — Nguyễn Đức Duy

---

## 1. Idea reframed

**Original idea:**
> Làm video về kiến thức và tin tức tự động

**Reframed as a product opportunity:**
> Sản xuất video về kiến thức, hướng dẫn, tin tức tốn rất nhiều thời gian, công sức và là một quy trình lặp đi lặp lại. Những video dạng này thường không cần quá phức tạp về hình ảnh, chủ yếu là truyền tải nội dung chính xác. Những AI gen video hiện tại có thể tạo những video rất đẹp mắt lại không phù hợp với video dạng này và thường tốn nhiều chi phí.

Một hệ thống tự động tạo video có thể giúp doanh nghiệp tạo ra những video hướng dẫn hoặc đưa tin nội bộ nhanh chóng. Bên cạnh đó, content creator cũng có thể sử dụng để tạo ra những video kiến thức hữu ích giúp giữ chân và duy trì tương tác với followers. Thậm chí, những nội dung kiến thức thú vị vẫn có thể trở nên hấp dẫn và thu hút followers.

---

## 2. Customer / Segment Card

- **Segment name:** Knowledge Creators & L&D Teams (Nhà sáng tạo nội dung kiến thức & Đội ngũ đào tạo nội bộ).
- **Operational context:** Thường xuyên phải chuyển đổi văn bản (bài báo, tin tức, tài liệu hướng dẫn) thành video để tiếp cận người xem/nhân viên một cách hiệu quả hơn.
- **Recurring workflow:** Viết/tổng hợp script -> Thu âm (Voiceover) -> Tìm kiếm/tạo hình ảnh minh hoạ (B-roll) -> Dựng video (cắt ghép, thêm phụ đề).
- **Pain moment:** Khi có tin tức nóng cần ra video ngay lập tức nhưng việc dựng video mất quá nhiều thì giờ, hoặc khi phải tốn hàng giờ đồng hồ mỏi mắt tìm footage phù hợp và canh thời gian cho khớp với giọng đọc.
- **Why now:** Sự bùng nổ của video ngắn (Shorts/Reels/TikTok) khiến nhu cầu tiêu thụ thông tin qua video tăng vọt. Các mô hình LLM và Text-to-Speech (TTS) hiện tại đã đủ trưởng thành để tự động hóa cốt lõi của dạng video này, trong khi các AI gen video khác quá đắt đỏ và rườm rà.
- **Access path:** Các cộng đồng Content Creator (YouTube, TikTok, Facebook Groups), LinkedIn (HR, L&D managers, Marketers).

**One-sentence description:**
> Những cá nhân và tổ chức cần sản xuất số lượng lớn video thông tin/kiến thức một cách chính xác, nhanh chóng nhưng đang bị cản trở bởi khâu tìm kiếm hình ảnh minh hoạ và biên tập video thủ công.

---

## 3. Need Map (2–3 needs)

### Need #1 (priority): Tốc độ và Tự động hoá quy trình (Workflow Speed)
- **Statement (JTBD):** When có một tin tức nóng hoặc tài liệu mới, I want chuyển nó thành video ngay lập tức mà không cần tự tay chỉnh sửa, so I can giữ tương tác với người theo dõi và bắt kịp xu hướng.
- **Current workaround:** Tự thu âm trên điện thoại và chèn vài hình ảnh tĩnh sơ sài, hoặc cố gắng thức đêm dùng các phần mềm dựng video truyền thống (Premiere, CapCut).
- **Pain signal:** Than phiền về việc kiệt sức vì áp lực tần suất ra video, lỡ mất "thời điểm vàng" của tin tức nóng.
- **Evidence / proxy evidence:** Nhiều kênh làm tin tức thường chỉ dùng một hình nền hoặc nhân vật cố định nói xuyên suốt video vì không có thời gian làm hình ảnh minh hoạ.
- **Why underserved:** Các công cụ AI tạo video (như Runway, Sora) tập trung vào điện ảnh, tạo video đẹp mắt tốn nhiều compute, chứ không giải quyết bài toán luồng công việc (workflow) tạo video tin tức/kiến thức nhanh và rẻ.

### Need #2: Tính chính xác và độ khớp của hình ảnh (Contextual Relevance)
- **Statement (JTBD):** When tạo video kiến thức chuyên môn, I want hình ảnh minh hoạ phải khớp chính xác với ngữ cảnh nội dung đang nói, so I can giúp người xem dễ hiểu, nắm bắt thông tin trực quan mà không bị phân tâm.
- **Current workaround:** Tìm kiếm thủ công hàng chục từ khoá trên các kho stock video, tự cắt ghép, đo lường thời gian timeline cho khớp với từng câu chữ.
- **Pain signal:** Sự ức chế khi hình ảnh và lời bình "đánh nhau", dẫn đến video trông nghiệp dư.
- **Evidence / proxy evidence:** Bình luận của người xem kiểu "hình ảnh không liên quan", tỷ lệ bỏ xem (drop-off rate) cao khi nội dung khô khan không có hình ảnh bổ trợ đúng lúc.
- **Why underserved:** Đa số tool auto video hiện tại gán hình stock một cách ngẫu nhiên chỉ dựa trên từ khoá (keyword matching) đơn giản, không thực sự hiểu ngữ cảnh sâu (semantic understanding) của câu nói.

### Need #3: Khả năng tuỳ chỉnh linh hoạt (Human-in-the-loop Customization)
- **Statement (JTBD):** When AI chọn hình ảnh hoặc phân cảnh chưa đúng ý đồ, I want có thể can thiệp nhanh chóng để tải lên media của riêng tôi hoặc yêu cầu AI tìm kiếm lại, so I can đảm bảo video cuối cùng chính xác 100% nội dung chuyên môn.
- **Current workaround:** Phải xuất video từ tool AI ra, sau đó đưa vào phần mềm edit truyền thống để cắt bỏ đoạn sai và chèn lại hình mới.
- **Pain signal:** Sự bực bội khi sử dụng các công cụ AI "hộp đen" (black box) one-click, không cho phép sửa đổi chi tiết trước khi xuất file.
- **Evidence / proxy evidence:** Nhu cầu có một giao diện "Review & Edit" trực quan từng phân cảnh (scene-by-scene) trước khi tốn thời gian render.
- **Why underserved:** Nhiều sản phẩm AI tạo video quá chú trọng vào tính tự động hoá 100% (one-click generation) mà bỏ quên nhu cầu kiểm soát (control) và tùy chỉnh (customization) của những người làm nội dung chuyên nghiệp.

---

## 4. Strategy Statement

For **Content Creators và Đội ngũ đào tạo nội bộ (L&D)**
who struggle with **việc tiêu tốn quá nhiều thời gian và công sức để sản xuất video tin tức/kiến thức**,
our product helps them **chuyển đổi văn bản thành video hoàn chỉnh chỉ trong vài phút**
through **kiến trúc Multi-Agent (Splitter & Director) phân tích ngữ cảnh để chia nhỏ kịch bản và tự động ghép nối kho dữ liệu hình ảnh/video có sẵn**,
unlike **các phần mềm chỉnh sửa video truyền thống hay các AI tạo video điện ảnh đắt đỏ**,
because we can leverage **LLM chuyên biệt hoá vai trò để hiểu sâu văn bản và một luồng lắp ráp tự động (automated assembly pipeline) kết hợp giao diện Review linh hoạt (Human-in-the-loop) giúp tối ưu hóa chi phí, thời gian mà vẫn giữ quyền kiểm soát cho người dùng**.

---

## 5. Moat Hypothesis

**Moat mechanism:** Context-matching Media Engine, Technical Architecture & Data Network Effect (Động cơ ghép nối hình ảnh theo ngữ cảnh, Kiến trúc kỹ thuật và Hiệu ứng mạng dữ liệu).

If we deploy [N] times in [thị trường creators/L&D], the following improve:
1. Thuật toán Multi-Agent hiểu ngữ cảnh văn bản để tìm và gán hình ảnh/video minh hoạ (B-roll) sẽ ngày càng chính xác và thông minh hơn nhờ học từ các thao tác re-search và upload custom media của người dùng.
2. Kho lưu trữ các phân cảnh, template, và metadata (tagging) của stock media nội bộ trở nên phong phú và được tinh chỉnh tốt hơn.
3. Người dùng sẽ tạo ra các luồng kịch bản mẫu (recipes/templates) và chia sẻ trong cộng đồng, tăng độ gắn kết với nền tảng.

**Why competitors cannot easily replicate this:**
> 1. **Kỹ thuật:** Các đối thủ lớn tập trung vào Generative AI (gen ra pixel từ đầu) vốn đòi hỏi chi phí tính toán (compute) khổng lồ và khó kiểm soát đầu ra. Chúng ta tập trung vào bài toán "Retrieval" (truy xuất) và "Assembly" (lắp ráp) thông minh kết hợp kiến trúc Multi-Agent (Splitter & Director) phân tách rõ ràng, tạo ra chi phí LLM cực rẻ, tránh lỗi ảo giác và tốc độ render cực nhanh.
> 2. **Trải nghiệm:** Thay vì "one-click" đóng kín, giao diện Human-in-the-loop cho phép người dùng tùy chỉnh từng scene (thay đổi scene type, tải media riêng, layout fullscreen/cinema) tạo ra rào cản chuyển đổi (switching cost) cao khi họ đã quen với workflow của chúng ta. Càng nhiều video được tạo và chỉnh sửa, hệ thống matching văn bản - hình ảnh càng được fine-tune tốt hơn đối thủ.

---

## 6. Initial TAM / SAM / SOM view

| Layer | Estimate | Key assumptions | Confidence |
| :--- | :--- | :--- | :--- |
| **TAM** | $2.5B - $5B/year | Dựa trên dự báo thị trường phần mềm Video Editing SaaS và AI Video Generators toàn cầu (2025-2026). | high |
| **SAM** | $500M/year | Thị phần phục vụ cho SMEs và Creators chuyên về mảng nội dung Education/News/L&D. | med |
| **SOM** | $2M - $5M | Mục tiêu 12-24 tháng đầu: Chiếm lĩnh thị trường creators và SME tại Việt Nam & một số nước Đông Nam Á. | low |

**Top 3 unknowns requiring further research:**
1. Mức độ sẵn sàng trả phí (Willingness to Pay) của nhóm Creator cá nhân so với khách hàng Doanh nghiệp (L&D/Marketing).
2. Chi phí vận hành thực tế (API LLM, TTS, Stock Video API) cho 1 phút video để đảm bảo biên lợi nhuận (margin) dương.
3. Người xem cuối (End-users) có chấp nhận và duy trì tỷ lệ giữ chân (retention) đối với định dạng video "lắp ráp" tự động này về lâu dài hay không.

**Judgment:**
- [x] Worth pursuing now
- [ ] Worth pursuing but not now (need to validate [...] first)
- [ ] Not worth pursuing as currently framed

---

## 7. Positioning Note (2 sentences)

**What we are:**
> Chúng tôi là một cỗ máy tự động hóa quy trình sản xuất (Automated Pipeline) kết hợp giao diện rà soát tinh chỉnh (Human-in-the-loop), giúp chuyển đổi nhanh chóng bất kỳ kịch bản nào thành một video kiến thức/tin tức hoàn chỉnh, chuyên nghiệp với quyền kiểm soát tối đa và chi phí cực thấp.

**What we are not / not yet:**
> Chúng tôi KHÔNG phải là một công cụ tạo video điện ảnh (như Sora, Runway), KHÔNG tự vẽ ra video từ pixel, hay phần mềm chỉnh sửa video thủ công chuyên sâu (như Premiere) để tạo ra các tác phẩm nghệ thuật phức tạp.

---

## 8. Self-assessment before Day 17

Trong 6 mắt xích (Idea, Customer, Need, Strategy, Moat, Market Size), mắt xích nào yếu nhất?
> **Market Size & Need validation:** Doanh nghiệp (L&D) có ngân sách nhưng quy trình duyệt mua thường phức tạp, trong khi Content Creators cần công cụ nhanh rẻ nhưng lại quen với việc xài đồ miễn phí. Cần xác định rõ nhu cầu trả phí thực sự đến từ tập khách hàng nào đầu tiên để tồn tại.

**Open questions chúng tôi muốn khám phá thêm ở Day 17:**
1. Chân dung khách hàng cụ thể (Early Adopters) nào sẵn sàng trả tiền ngay cho giải pháp này ở thời điểm hiện tại?
2. Làm thế nào để thiết kế một trải nghiệm người dùng cốt lõi (Core UX) khiến khách hàng cảm thấy "wow" ngay từ lần tạo video đầu tiên?
3. Mô hình giá (Pricing model) nên tính theo phút video tạo ra hay tính theo gói thuê bao tháng để đảm bảo khả năng mở rộng?