# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600268
**Name:** Phạm Thanh Tùng
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dung san pham, dung gia, ket qua chinh xac |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Sai hoan toan, chon outlier vo nghia |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi sử dụng dữ liệu rác (garbage data), Agent đã trả lời hoàn toàn sai vì nhiều lý do liên quan đến chất lượng dữ liệu đầu vào.

Thứ nhất, dữ liệu chứa Duplicate IDs (id = 1 xuất hiện hai lần với sản phẩm khác nhau), khiến Agent không thể phân biệt chính xác giữa các sản phẩm.

Thứ hai, cột price có giá trị sai kiểu dữ liệu (ví dụ: "ten dollars" thay vì số), làm cho việc tính toán và so sánh giá trở nên không đáng tin cậy.

Thứ ba, dữ liệu chứa extreme outlier như Nuclear Reactor với giá 999999 đô la, đây là giá trị bất thường khiến Agent chọn nó là sản phẩm tốt nhất chỉ vì giá cao nhất, mặc dù nó không phải là sản phẩm electronics hợp lý.

Thứ tư, các trường null values (id = None, category = None) tạo ra các record không có ý nghĩa, làm nhiễm dữ liệu.

Tất cả những vấn đề này cho thấy rằng nếu không có bước Data Validation và Data Cleaning trước khi đưa dữ liệu vào AI Agent, kết quả trả về sẽ hoàn toàn sai lệch và không thể tin tưởng được.

Pipeline ETL với bước validation giúp loại bỏ các record lỗi, đảm bảo Agent chỉ làm việc với dữ liệu sạch và cho kết quả chính xác.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý hoàn toàn. Dù prompt có tốt đến đâu, nếu dữ liệu đầu vào bị lỗi (outliers, duplicates, null values, wrong types) thì Agent vẫn sẽ cho ra kết quả sai.

Data Quality là nền tảng quan trọng nhất của bất kỳ hệ thống AI nào. Một pipeline ETL tốt với bước validation chặt chẽ sẽ đảm bảo dữ liệu sạch, từ đó giúp Agent đưa ra câu trả lời chính xác và đáng tin cậy hơn.
