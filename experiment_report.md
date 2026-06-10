# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600912
**Name:** Nguyễn Thế Giáp
**Date:** 2026-06-10

---

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dữ liệu sạch, giá trị electronics hợp lý, output có ý nghĩa với ngữ cảnh mua sắm. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Outlier rất lớn và dữ liệu sai chất lượng khiến agent chọn kết quả vô lý. |

---

## 2. Phân tích & nhận xét

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Agent trả lời sai vì logic của agent đang ưu tiên giá cao nhất trong nhóm electronics, nên outlier 999999 lập tức trở thành lựa chọn "tốt nhất" dù không phù hợp thực tế. Bộ dữ liệu garbage còn có duplicate ID, kiểu dữ liệu không nhất quán (ten dollars), và null values, làm giảm độ tin cậy của toàn bộ tập dữ liệu. Khi pipeline không có bước ràng buộc chất lượng dữ liệu trước suy luận, agent dễ bị "poison" bởi các bản ghi bất thường. Điều này cho thấy chất lượng data ảnh hưởng trực tiếp đến độ đúng của câu trả lời, kể cả khi prompt không đổi.

---

## 3. Kết luận

**Quality Data > Quality Prompt?** Đồng ý. Prompt tốt chỉ giúp diễn đạt yêu cầu rõ hơn, nhưng nếu dữ liệu đầu vào sai hoặc bẩn thì output vẫn sai. Chất lượng dữ liệu là điều kiện nền để AI trả lời đúng và ổn định.
