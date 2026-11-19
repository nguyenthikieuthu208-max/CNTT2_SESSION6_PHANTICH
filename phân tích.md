


# BÁO CÁO PHÂN TÍCH TRADE-OFF CÁC GIẢI PHÁP PROMPTING
**Chủ đề:** Tối ưu hóa quy trình Gia sư Feynman & Chấm bài tự động theo Rubric trong Ứng dụng AI cho Học tập & Nghiên cứu

---

## 1. Tổng quan bài toán & Mục tiêu phân tích

Trong quy trình **Gia sư Feynman** kết hợp **Rubric chấm bài tự động**, AI vừa đóng vai trò người hướng dẫn kiểm tra mức độ hiểu sâu qua cách diễn đạt đơn giản, vừa đóng vai trò giám khảo chấm điểm khách quan theo tiêu chí. Tuy nhiên, nếu thiết kế prompt quá sơ sài thì dễ gặp hiện tượng chấm cảm tính hoặc bỏ sót lỗi dữ liệu; ngược lại, nếu nhồi nhét quá nhiều quy tắc thì dễ tốn token, khó bảo trì và chậm phản hồi.

Báo cáo này đề xuất **2 phương án prompt** (Đơn giản vs. Chi tiết), lập bảng đánh giá **Trade-off** theo các tiêu chí cốt lõi, lựa chọn phương án tối ưu và chạy thử nghiệm thực tế để làm cơ sở nộp bài.

---

## 2. Bước 1: Đề xuất 2 prompt mẫu

### 2.1. Giải pháp 1: Prompt đơn giản, ngắn gọn (Lightweight Prompt)

Phù hợp khi cần phản hồi nhanh, tiết kiệm token, dùng cho các buổi tự học nhẹ hoặc kịch bản thử nghiệm ban đầu.

```markdown
Bạn là gia sư phương pháp Feynman kiêm người chấm bài theo Rubric.
Hãy nhận xét lời giải thích của người học về chủ đề, chấm điểm theo thang Rubric được cung cấp, chỉ ra chỗ còn hiểu chưa đúng hoặc chưa rõ, giải thích lại ngắn gọn cho dễ hiểu và đặt 1 câu hỏi kiểm tra.

Chủ đề: {{TOPIC_OR_QUESTION}}
Lời giải thích của người học: {{LEARNER_EXPLANATION}}
Rubric chấm điểm: {{RUBRIC_CRITERIA}}
