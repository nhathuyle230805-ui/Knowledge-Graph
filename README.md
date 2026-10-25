# Hướng 2 — Knowledge Graph Recommendation

**Người thực hiện:** Lê Trần Nhật Huy (Member 2)  
**Thời điểm tổng hợp:** 24/10/2026  

## Mục tiêu
Kế thừa tập ứng viên baseline từ Member 1 (Cường Quốc), xây dựng và khai thác Đồ thị tri thức (Knowledge Graph - KG) để mở rộng mối quan hệ thực thể (User, Product, Brand, Category), cải thiện độ chính xác của hệ thống gợi ý và bàn giao dữ liệu đã xử lý cho Member 3 (Giảng Nguyên) tiếp tục tích hợp LLM và Reranking.

---

## Cấu trúc thư mục mã nguồn
* `All_Beauty_Cleaned_Merged_GitHub.xlsx`: Dataset đã được làm sạch và chuẩn hóa.
* `kg_triples_csv.ipynb`: Notebook xử lý trích xuất bộ ba tri thức (Triples).
* `Direction2_KnowledgeGraph.ipynb`: Notebook chính thực thi xây dựng đồ thị NetworkX, đánh giá đối chứng và xuất file bàn giao.
* `requirements.txt`: Các thư viện Python cần thiết (`pandas`, `numpy`, `networkx`, `matplotlib`, `openpyxl`).

---

## Kết quả đánh giá đối chứng (Baseline vs. Baseline + KG)

Thực nghiệm so sánh hiệu năng giữa thuật toán Lọc cộng tác cơ sở của Cường Quốc và mô hình cải tiến tích hợp Đồ thị tri thức:

| Metric | Baseline (ItemCF - Member 1) | Baseline + KG (Member 2) |
| :--- | :---: | :---: |
| **Precision@5** | 0.0420 | **0.0680** |
| **Recall@5** | 0.0650 | **0.1120** |
| **NDCG@5** | 0.0510 | **0.0890** |
| **Precision@10** | 0.0310 | **0.0510** |
| **Recall@10** | 0.0980 | **0.1540** |
| **NDCG@10** | 0.0620 | **0.1050** |

---

## Biểu đồ trực quan hóa
Biểu đồ so sánh chi tiết hiệu năng giữa hai cấu hình đã được lưu tại: `comparison_baseline_vs_kg.png`.

---

## Bàn giao cho Member 3 (Giảng Nguyên)
Đầu ra phục vụ cho quá trình tích hợp LLM và xử lý thiên lệch (Reranking):
* **File dữ liệu bàn giao:** `kg_recommendations_for_member3.csv`
* **Các trường thông tin chính:** `user_id`, `recommended_items`, `score_kg`, `schema_metadata`.
