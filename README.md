[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574046&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.tungpt@vinuni.edu.vn
**Name:** Phạm Thanh Tùng

---

## Mo ta

Bài lab này xây dựng một ETL Pipeline tự động để xử lý dữ liệu sản phẩm từ file JSON. Pipeline thực hiện 4 bước chính:

Extract (Trích xuất): đọc dữ liệu
Validate (Kiểm tra): lọc bỏ dữ liệu lỗi như giá âm, category rỗng
Transform (Biến đổi): tính giá giảm 10%, chuẩn hóa category
Load (Tải dữ liệu): lưu kết quả ra file CSV

Ngoài ra, bài lab còn bao gồm thí nghiệm stress test so sánh kết quả của AI Agent khi sử dụng dữ liệu sạch và dữ liệu rác, cho thấy tầm quan trọng của chất lượng dữ liệu (Data Quality) trong hệ thống AI.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Tao du lieu rac
python generate_garbage.py

# Chay agent voi ca 2 bo du lieu (clean va garbage)
python agent_simulation.py
```

### Chay tests
```bash
pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
├── agent_simulation.py      # Script mo phong AI Agent
├── generate_garbage.py      # Script tao du lieu rac
├── raw_data.json            # Du lieu dau vao
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records dau vao:** 5
- **Records hop le (valid):** 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped):** 2 (Mystery Box - gia am, Phone - category rong)
- **Output:** `processed_data.csv` voi 3 records da duoc transform (discounted_price, Title Case category, timestamp)
