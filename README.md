 Hướng 2: Nâng cao với Đồ thị tri thức (Knowledge Graph - KG)

# 1. Đặt vấn đề (Problem Statement)
* Các phương pháp Lọc cộng tác (Collaborative Filtering - CF) truyền thống chỉ dựa vào lịch sử tương tác giữa Người dùng - Sản phẩm.
* **Hạn chế:** Bỏ qua các thông tin mô tả phong phú từ metadata của sản phẩm (thương hiệu, danh mục, thuộc tính) và dễ gặp phải sự cố "Khởi động lạnh" (Cold-start) khi dữ liệu tương tác còn ít.

---

## 2. Quá trình thực hiện (Implementation Process)

### Phương pháp thực hiện (Workflow):
1. **Thu thập & Tiền xử lý dữ liệu:**
   * Trích xuất các thuộc tính từ dữ liệu Amazon (`All_Beauty`) bao gồm: `parent_asin`, `brand`, `main_category`, `sub_category`, `price`, `rating`.
2. **Xây dựng Đồ thị tri thức (Knowledge Graph Construction):**
   * Chuyển đổi dữ liệu thành các bộ ba tri thức (*Triples*): `(Head, Relation, Tail)`.
   * Định nghĩa các mối quan hệ cấu trúc:
     * `(Product, HAS_BRAND, Brand)`
     * `(Product, BELONGS_TO, Category)`
3. **Khai thác đồ thị & Trực quan hóa:**
   * Sử dụng thư viện `NetworkX` trong Python để liên kết các thực thể, biểu diễn mạng lưới quan hệ đa chiều giữa các sản phẩm.

---

## 3. Nội dung & Mã nguồn (Source Code)
* `Direction2_KnowledgeGraph.ipynb`: Mã nguồn Python xử lý và vẽ đồ thị tri thức NetworkX.
* `kg_triples_csv.ipynb`: Mã nguồn tự động trích xuất file bộ ba tri thức (`kg_triples.csv`).
* `All_Beauty_Cleaned_Merged_GitHub.xlsx`: Tập dữ liệu chuẩn đã làm sạch dùng cho huấn luyện và liên kết đồ thị.

---

## 4. Kết quả đạt được (Results)
* Xây dựng thành công mạng lưới Đồ thị tri thức biểu diễn rõ ràng mối liên kết thuộc tính giữa các sản phẩm.
* Cải thiện khả năng gợi ý sản phẩm liên quan dựa trên điểm chung về thương hiệu (`brand`) và danh mục (`categories`).

---

## 5. Khoảng trống nghiên cứu & Lý do chọn Hướng 3 (Research Gap & Transition to Direction 3)

### ⚠️ Khoảng trống nghiên cứu của Hướng 2:
1. **Thiếu yếu tố Thời gian (Static Graph):** Đồ thị tri thức truyền thống chỉ lưu trữ các mối quan hệ cố định, không phản ánh được sự thay đổi trong hành vi, xu hướng tiêu dùng và sở thích biến đổi theo thời gian của người dùng.
2. **Chưa tối ưu ngữ nghĩa phức tạp:** Đồ thị cấu trúc chưa khai thác hết ngữ nghĩa tự nhiên trong đánh giá (*reviews*) và mô tả chi tiết của sản phẩm.

### 🚀 Định hướng phát triển (Chuyển sang Hướng 3):
* Để khắc phục khoảng trống trên, nhóm quyết định nâng cấp lên **Hướng 3: Đồ thị tri thức theo thời gian (Temporal Knowledge Graph - TKG) kết hợp Mô hình ngôn ngữ lớn (LLM)**.
* Hướng 3 sẽ bổ sung nhãn thời gian (*Timestamp*) vào các bộ ba tri thức và tích hợp LLM để phân tích ngữ nghĩa, giúp hệ thống gợi ý chính xác hơn theo từng thời điểm.
