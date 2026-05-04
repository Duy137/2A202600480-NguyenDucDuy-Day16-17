# 📊 Dự toán chi phí Production (AutoClip Video)

> Đây là bản dự toán mình đã ngồi tính lại và tối ưu kiến trúc để ép chi phí sản xuất xuống dưới 2.000 VNĐ/video. Mục tiêu là để chạy mô hình SaaS phục vụ scale lớn mà margin vẫn dày.

**Các thông số mình dùng để tính:**
- **Thời lượng trung bình:** 1 phút (tầm 1100 ký tự tiếng Việt)
- **Cấu trúc:** 10 phân cảnh (scenes)
- **LLM/VLM:** Dùng `gpt-4o-mini` (rẻ mà vẫn xử lý ngon cả Text và Vision)
- **Mô hình:** Freemium (có tier Free và tier VIP trả phí)

---

## 1. Phương án tối ưu chi phí (Ép giá vốn)

Để tránh vết xe đổ đốt tiền API và server, mình quyết định thay đổi 3 phần cốt lõi trong kiến trúc:

### A. Cắt hẳn tiền mua API Stock Video (Tiết kiệm ~12.500đ/video)
Mình sẽ không gọi API từ các trang stock trả phí nữa vì chi phí theo tháng quá chát.
- **Cách làm:** Mình sẽ tự build một kho Media nội bộ (Local Library). Viết script cào khoảng 5.000 - 10.000 video miễn phí (từ Pexels, Pixabay) về quăng lên Amazon S3. Sau đó dùng VLM chạy auto-tagging.
- Lúc user tạo video, hệ thống chỉ search trong kho S3 này thôi.
- **Kết quả:** Chi phí media gần như = **0 VNĐ**, chỉ tốn chút tiền duy trì S3 chia đều cho hàng chục ngàn video.

### B. Render Serverless (Không có user thì không tốn tiền)
Thuê server GPU/CPU mạnh chạy 24/7 lúc chưa có đông user là tự sát.
- **Cách làm:** Đẩy khâu render lên **AWS Lambda (Remotion Lambda)**.
- Ai bấm "Tạo video" thì Lambda mới chạy. Render xong tắt luôn. Nếu có 100 người vào cùng lúc thì nó tự scale lên 100 luồng.
- **Kết quả:** AWS tính tiền theo giây. 1 phút video với 10 phân cảnh sẽ mất thời gian render lâu hơn một chút để xử lý chuyển cảnh, tốn cỡ $0.04 (**~1.000 VNĐ**).

### C. Chia tier cho Giọng đọc (TTS)
- **User Free:** Mặc định xài `Edge-TTS` (Hàng free 100%).
- **User VIP (Trả phí):** Được xài API của `Vbee VIP+`. Mình check giá thì 1 video 1 phút tốn tầm **~450 VNĐ** (đã tính cả gói mua thêm luồng đồng thời).

---

## 2. Bảng phân tích chi phí cuối cùng (COGS)

| Hạng mục | Khách hàng MIỄN PHÍ | Khách hàng TRẢ PHÍ (VIP) |
|----------|---------------------|--------------------------|
| **LLM & VLM** (`gpt-4o-mini`) | 50 VNĐ | 50 VNĐ |
| **Âm thanh** | 0 VNĐ (`Edge-TTS`) | 450 VNĐ (`Vbee VIP+`) |
| **Bản quyền Video** (Lưu trữ S3) | ~100 VNĐ | ~100 VNĐ |
| **Server Render** (AWS Lambda) | 1.000 VNĐ | 1.000 VNĐ |
| **TỔNG GIÁ VỐN / VIDEO 1 PHÚT** | **~ 1.150 VNĐ / Video** | **~ 1.600 VNĐ / Video** |

---

## 3. Bài toán kinh doanh (Unit Economics)

Với cái giá vốn đã ép xuống đáy thế này, mình tính chiến lược giá như sau:

1. **Bán lẻ theo Credit (Pay as you go):**
   - Định giá tầm **5.000đ - 10.000đ / video**.
   - Margin siêu ổn, lãi gấp 3 đến 6 lần chi phí.

2. **Bán gói Thuê bao (Subscription - Hướng chính cho Creator):**
   - Đẩy gói **399.000đ/tháng**, cho user tạo tối đa 100 video VIP (1 phút/video). Dành cho các creator làm kênh kiến thức/tin tức cần cày cuốc số lượng lớn (3-4 video/ngày).
   - Nếu user xài max 100 video, giá vốn là: 100 * 1.600đ = 160.000đ.
   - Mình vẫn lãi gộp **239.000đ** trên mỗi khách hàng gia hạn mỗi tháng. Margin đạt ~60% (vẫn cực kỳ Healthy cho mô hình AI).

3. **Chi phí đầu tư ban đầu cho Vbee API:**
   - Mua gói cơ bản 1.050.000 VNĐ/năm (3 triệu ký tự).
   - Mua thêm 5 luồng (250.000 VNĐ) để chống nghẽn nghẽn giờ cao điểm.
   - Tổng cộng tốn khoảng 1.300.000 VNĐ. Số tiền này quá nhẹ nhàng để bắt đầu.
