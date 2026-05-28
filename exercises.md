# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**
> 

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi giá trị temperature tăng dần từ 0.0 lên 1.5, câu trả lời chuyển từ trạng thái rập khuôn, dễ đoán sang trạng thái sáng tạo và phong phú hơn về từ vựng. Tuy nhiên, ở mức tối đa 1.5, mô hình bắt đầu mất kiểm soát, câu văn trở nên lan man, thiếu logic, cấu trúc ngữ pháp có thể bị phá vỡ hoặc sinh ra thông tin sai lệch

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Đối với chatbot hỗ trợ khách hàng, mức temperature lý tưởng nên được đặt rất thấp, khoảng 0.1 đến 0.3. Lý do là trong dịch vụ khách hàng, độ chính xác, tính nhất quán và việc tuân thủ nghiêm ngặt chính sách/thông tin của công ty là ưu tiên hàng đầu; việc đặt temperature thấp giúp loại bỏ sự "sáng tạo" không cần thiết, ngăn chặn rủi ro bot tự bịa ra thông tin làm ảnh hưởng đến trải nghiệm và quyền lợi của người dùng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Xét theo đơn giá (dựa trên bảng giá 0.010 USD/1K token của gpt-4o và 0.0006 USD/1K token của gpt-4o-mini), GPT-4o đắt hơn GPT-4o-mini xấp xỉ 16.67 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi: Ứng dụng yêu cầu khả năng tư duy logic sâu sắc, lập luận phức tạp hoặc hiểu biết ngữ cảnh sắc thái cao. Ví dụ: Một trợ lý ảo phân tích hợp đồng pháp lý, gỡ lỗi (debug) các đoạn code phức tạp, hoặc tư vấn y tế/tài chính chuyên sâu.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming đặc biệt quan trọng trong các giao diện tương tác trực tiếp với người dùng, nơi việc hiển thị từng chữ một ngay lập tức sẽ giúp giảm thiểu đáng kể thời gian chờ đợi, giữ chân người dùng và tạo cảm giác giao tiếp tự nhiên như con người. Ngược lại, non-streaming lại phù hợp hơn cho các tác vụ xử lý ngầm hoặc xử lý hàng loạt mà không có người dùng trực tiếp ngồi nhìn màn hình chờ đợi — ví dụ như hệ thống tự động tóm tắt hàng trăm email vào cuối ngày, dịch thuật nguyên một tài liệu dài, hoặc pipeline phân tích và lưu trữ dữ liệu vào database, nơi hệ thống chỉ cần toàn bộ chuỗi văn bản hoàn chỉnh để thực hiện bước tiếp theo.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
