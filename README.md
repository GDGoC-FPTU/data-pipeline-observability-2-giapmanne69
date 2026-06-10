[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112708&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** giap200496@gmail.com
**Name:** Nguyễn Thế Giáp

---

## Mô tả

Bài lab xây dựng ETL pipeline gồm 4 bước extract, validate, transform, load trên dữ liệu JSON. Pipeline loại bỏ record không hợp lệ (price <= 0, category rỗng), tính discounted_price giảm 10%, chuẩn hóa category về Title Case và thêm timestamp processed_at trước khi ghi ra CSV.

---

## Cách chạy (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chạy ETL Pipeline
```bash
python solution.py
```

### Chạy Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python -c "from agent_simulation import simulate_agent_response; print('CLEAN:', simulate_agent_response('What is the best electronic product?', 'processed_data.csv')); print('GARBAGE:', simulate_agent_response('What is the best electronic product?', 'garbage_data.csv'))"
python -m pytest tests/test_autograder.py -v
```

---

## Cấu trúc thư mục

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Kết quả

- ETL pipeline chạy thành công và tạo file processed_data.csv.
- Validation summary: 3 valid, 3 dropped.
- Agent với clean data trả lời hợp lý: Laptop at $1200.
- Agent với garbage data bị ảnh hưởng outlier: Nuclear Reactor at $999999.
- Local autograder: 9/9 tests passed.
