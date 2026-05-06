# 📊 Bảng RICE & Ma trận Value-Effort (AutoClip AI)

## 1. Bảng chấm điểm RICE

**Công thức:** `RICE Score = (Reach × Impact × Confidence) / Effort`
*   **Reach (R):** Số lượng user tiếp cận tính năng trong 1 quý (Giả định tập 500 user trả phí).
*   **Impact (I):** 3 (Massive), 2 (High), 1 (Medium), 0.5 (Low), 0.25 (Tiny).
*   **Confidence (C):** 100%, 80%, 50%.
*   **Effort (E):** Person-month (Người-tháng).

| Tính năng | Reach (R) | Impact (I) | Confidence (C) | Effort (E) | **RICE Score** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Giao diện Human-in-the-loop (Review/Đổi ảnh)** | 500 | 3 (Massive) | 80% | 1.5 | **800** |
| **2. Tích hợp TTS Tiếng Việt (Vbee API)** | 500 | 2 (High) | 100% | 1.0 | **1000** |
| **3. Kho Local Media Library 100k assets** | 500 | 3 (Massive) | 80% | 4.0 | **300** |
| **4. Auto-publish lên TikTok/Shorts API** | 100 (20%) | 0.5 (Low) | 80% | 2.0 | **20** |
| **5. AI Script Writer (Tự sinh kịch bản)** | 250 (50%) | 0.5 (Low) | 50% | 5.0 | **12.5** |

---

## 2. Ma trận Value-Effort (2x2 Matrix)

Dựa trên bảng RICE, phân loại các tính năng vào 4 ô chiến lược:

*   🟢 **QUICK WINS (Value Cao - Effort Thấp): Làm ngay - Lấy đà**
    *   **Tích hợp TTS Tiếng Việt (Vbee API)** *(Score 1000)*
    *   **Giao diện Human-in-the-loop (Review/Đổi ảnh)** *(Score 800)*

*   🔴 **STRATEGIC BETS (Value Cao - Effort Cao): Đầu tư dài hạn = Moat**
    *   **Kho Local Media Library 100k assets** *(Score 300)* - Rất tốn nguồn lực nhưng sẽ giảm giá vốn API, tạo "hào rãnh" phòng thủ vững chắc trước đối thủ.

*   🟡 **FILL-INS (Value Thấp - Effort Thấp): Làm khi rảnh**
    *   **Auto-publish lên TikTok/Shorts API** *(Score 20)* - Rất ít user quan tâm vì họ muốn tải video về để kiểm tra chéo trước khi tự đăng.

*   🗑️ **NON-STARTERS (Value Thấp - Effort Cao): Vứt vào sọt rác**
    *   **AI Script Writer (Tự sinh kịch bản)** *(Score 12.5)* - User (Creators/L&D) đã có sẵn kịch bản chất lượng cao. Tính năng này làm cồng kềnh hệ thống, rủi ro ảo giác (hallucination) cao mà không giải quyết đúng "pain-point" chính. Bỏ thẳng khỏi roadmap.
