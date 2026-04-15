# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600496
**Name:** Trần Kiên Trường
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 10 | Correct answer - Laptop is valid electronics at reasonable price |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Incorrect - Nuclear Reactor is an outlier, not a real product |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Garbage Data chứa nhiều vấn đề nghiêm trọng ảnh hưởng đến kết quả của Agent:

1. **Duplicate IDs (id=1 xuất hiện 2 lần)**: Gây ra trùng lặp dữ liệu, Agent không biết nên chọn Laptop hay Banana.

2. **Wrong data type (price="ten dollars")**: Agent cố parse nhưng thất bại, record bị loại bỏ hoặc gây lỗi.

3. **Outliers (price=999999 cho Nuclear Reactor)**: Giá trị cực đại này khiến Agent nghĩ đây là "best deal" vì logic của Agent là tìm price cao nhất trong category electronics.

4. **Null values (id trống, price=0, category trống)**: Dữ liệu không hợp lệ không được lọc bỏ, làm ô nhiễm kết quả phân tích.

Tất cả các vấn đề trên dẫn đến Agent đưa ra câu trả lời sai lệch hoàn toàn với thực tế.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý hoàn toàn. Một prompt tốt không thể khắc phục dữ liệu rác (garbage data). Agent chỉ phản hồi dựa trên dữ liệu mà nó nhìn thấy - nếu dữ liệu đầu vào chứa outliers, duplicate IDs, sai dtype, và null values, thì output sẽ sai. ETL pipeline với validation nghiêm ngặt là nền tảng để AI đưa ra câu trả lời chính xác.
