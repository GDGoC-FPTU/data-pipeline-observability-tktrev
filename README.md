[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573995&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** fktt831@gmail.com
**Name:** Trần Kiên Trường

---

## Mo ta

Day 10 Lab tập trung vào xây dựng một ETL pipeline tự động và đánh giá tác động của chất lượng dữ liệu lên kết quả của AI Agent.

**Những gì đã làm:**
1. Hoàn thành các hàm ETL: extract (đọc JSON), validate (lọc price > 0, category không rỗng), transform (tính discounted_price, chuẩn hóa category sang Title Case, thêm timestamp), load (lưu CSV)
2. Chạy thí nghiệm so sánh Agent response giữa Clean Data và Garbage Data
3. Phân tích các vấn đề dữ liệu: duplicate IDs, wrong data types, outliers, null values

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Mo ta cach ban chay thi nghiem Clean vs Garbage data
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

**ETL Pipeline:**
- Tổng records trong raw_data.json: 5
- Records hợp lệ (đã xử lý): 3
- Records bị loại (validation): 2

**Experiment Report:**
- Clean Data: Agent trả lời đúng → Laptop $1200 (electronics)
- Garbage Data: Agent trả lời sai → Nuclear Reactor $999999 (outlier)

**Kết luận:** Quality Data > Quality Prompt. Dữ liệu rác dẫn đến AI đưa ra câu trả lời sai hoàn toàn.
