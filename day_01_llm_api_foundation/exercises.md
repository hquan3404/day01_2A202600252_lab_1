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

Output so sánh:
=== Comparing models ===
gpt4o_response: Temperature controls how *sharp or random* the choice of each next token is, while top_p controls *how large a slice of the probability mass* (from most to least likely tokens) the model is allowed to sample from at each step.
mini_response: Temperature rescales logits to make the whole distribution flatter (higher T) or sharper (lower T), while top_p (nucleus sampling) limits choices to the smallest set of tokens whose cumulative probability ≥ p and samples from that truncated set.
gpt4o_latency: 5.230492115020752
mini_latency: 3.31669282913208
gpt4o_cost_estimate: 0.0005333333333333334

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> với temperature càng cao thì mô hình càng sáng tạo và khó đoán hơn

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> em sẽ đặt temperature = 0.5 cho chatbot hỗ trợ khách hàng vì nó sẽ trả lời chính xác và đáng tin cậy hơn, không bịa đặt thông tin

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> 16,7 lần

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> Khi người dùng cần câu trả lời tốt về độ chính xác, suy luận tốt hơn, giải quyết các bài toán khó hơn thì GPT-4o là lựa chọn tốt hơn
> Khi người dùng cần câu trả lời nhanh và chính xác, chi phí thấp, GPT-4o-mini là lựa chọn tốt hơn


### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
- Streaming quan trọng nhất trong trường hợp người dùng cần câu trả lời nhanh và chính xác, chi phí thấp, GPT-4o-mini là lựa chọn tốt hơn
- Non-streaming phù hợp hơn trong trường hợp người dùng cần câu trả lời tốt về độ chính xác, suy luận tốt hơn, giải quyết các bài toán khó hơn thì GPT-4o là lựa chọn tốt hơn

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
