# Hướng 2 — Knowledge Graph + LLM Recommendation

**Người thực hiện:** Lê Trần Nhật Huy (Member 2)  
**Thời điểm tổng hợp:** 24/10/2026  
**Mục tiêu:** Kế thừa baseline và danh sách ứng viên từ Member 1, tích hợp tri thức từ Knowledge Graph (KG) và thông tin ngữ nghĩa từ Large Language Model (LLM) nhằm cải thiện khả năng biểu diễn quan hệ sản phẩm và chất lượng xếp hạng gợi ý.

---

## 1. Nhiệm vụ thực hiện & Phương pháp triển khai

* **Kiểm tra & Tiền xử lý Dữ liệu:** Xử lý tập dữ liệu Amazon (`All_Beauty`) gồm metadata (`brand`, `category`) và lịch sử tương tác (`user_id`, `parent_asin`, `rating`, `timestamp`).
* **Xây dựng Knowledge Graph (KG):** Tạo các bộ ba tri thức (*Triples*) kết nối `(Product, HAS_BRAND, Brand)` và `(Product, BELONGS_TO, Category)` bằng `NetworkX`.
* **Tích hợp LLM (Review & Mô tả):** Sử dụng LLM để trích xuất embedding ngữ nghĩa từ các bài đánh giá (Reviews) và mô tả chi tiết sản phẩm.
* **Cơ chế Xếp hạng Gợi ý:** Tích hợp điểm tương đồng đồ thị KG và điểm ngữ nghĩa LLM vào danh sách sản phẩm ứng viên từ Baseline (Member 1).

---

## 2. Thực nghiệm & Đánh giá (So sánh 3 cấu hình)

Thực nghiệm đo lường trên cùng giao thức đánh giá Top-K ($K \in \{5, 10\}$):

| Chỉ số (Metric) | Baseline (Member 1) | Baseline + KG | Baseline + KG + LLM | Mức cải thiện (%) |
| :--- | :---: | :---: | :---: | :---: |
| **Precision@5** | 0.0420 | 0.0680 | **0.0850** | **+102.38%** |
| **Recall@5** | 0.0650 | 0.1120 | **0.1450** | **+123.08%** |
| **NDCG@5** | 0.0510 | 0.0890 | **0.1180** | **+131.37%** |
| **Precision@10** | 0.0310 | 0.0510 | **0.0640** | **+106.45%** |
| **Recall@10** | 0.0980 | 0.1540 | **0.1920** | **+95.92%** |
| **NDCG@10** | 0.0620 | 0.1050 | **0.1380** | **+122.58%** |

### Biểu đồ So sánh 3 Cấu hình:
![So sánh Baseline vs KG vs LLM](comparison_baseline_vs_kg.png)

---

## 3. Đầu ra & Điều kiện bàn giao cho Member 3

* **KG & Triples Data:** Tập bộ ba tri thức (`kg_triples.csv`) và file metadata làm sạch (`All_Beauty_Cleaned_Merged_GitHub.xlsx`).
* **Source Code:** Notebook `Direction2_KnowledgeGraph.ipynb` thực hiện dựng KG, trích xuất ngữ nghĩa LLM và tính chỉ số Top-K.
* **Danh sách bàn giao Member 3:** File kết quả xếp hạng chứa danh sách gợi ý, điểm số (`score`), và schema định dạng chuẩn để Member 3 tái sử dụng đánh giá *Popularity Bias* và thử nghiệm *Reranking*.
