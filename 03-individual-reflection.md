
# 03 — Individual Reflection

| Hoạt động               | Tôi đã làm gì?                                                       | Kết quả                                                             |
| ----------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Problem Scan            | Xác định 10 vấn đề trong hoạt động vận hành chuỗi cửa hàng thực phẩm | Tìm được 3 vấn đề có impact cao nhất                                |
| Prioritization          | Đánh giá và chọn Top 3 problems                                      | Xác định được bài toán trọng tâm là dự báo nhu cầu và đặt hàng      |
| Workflow Analysis       | Phân tích quy trình đặt hàng hiện tại và tương lai                   | Xác định bottleneck nằm ở bước dự báo nhu cầu                       |
| Research                | Tìm hiểu các giải pháp Demand Forecasting và Inventory Replenishment | Hiểu được các doanh nghiệp đang giải quyết bài toán này như thế nào |
| Rule / Workflow / Agent | So sánh các mức độ tự động hóa                                       | Kết luận Workflow là hướng phù hợp nhất                             |
| Problem Statement       | Hoàn thiện Problem Statement và Success Metrics                      | Xác định được phạm vi pilot rõ ràng                                 |


## Bảng dùng AI trong reflection

| Phase                   | Tôi dùng AI để làm gì?                         | AI hữu ích ở đâu?                                             | AI sai/hời hợt ở đâu?                            | Tôi sửa gì                                  |
| ----------------------- | ---------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------ | ------------------------------------------- |
| Problem Scan            | Brainstorm các vấn đề trong vận hành bán lẻ    | Gợi ý thêm các pain liên quan đến tồn kho và dự báo nhu cầu   | Một số vấn đề quá rộng hoặc không có workflow rõ | Loại bỏ các ý không đo lường được           |
| Prioritization          | So sánh các problem theo impact và feasibility | Giúp nhìn rõ nguyên nhân gốc và hệ quả                        | Có xu hướng chọn quá nhiều vấn đề liên quan      | Gom các vấn đề thành một bài toán trung tâm |
| Workflow                | Vẽ current state và future state               | Giúp xác định bottleneck và AI intervention point             | Một số bước bị đơn giản hóa quá mức              | Bổ sung bước review của người quản lý       |
| Research                | Tìm các giải pháp tương tự trên thị trường     | Hiểu được pattern phổ biến là AI đề xuất, con người phê duyệt | Một số giải pháp quá lớn so với quy mô BNB       | Thu hẹp phạm vi về pilot nhỏ                |
| Rule / Workflow / Agent | Phân tích mức độ tự động hóa phù hợp           | Làm rõ vì sao chưa cần Agent                                  | Đề xuất Agent hơi sớm                            | Giữ giải pháp ở mức Workflow                |


## Bài học
Một bài toán tốt không nhất thiết phải phức tạp mà cần có workflow rõ ràng và tác động đo lường được.
Nhiều vấn đề nhìn có vẻ khác nhau thực chất lại xuất phát từ cùng một nguyên nhân gốc.
Trong case này, thiếu hàng và hủy hàng đều bắt nguồn từ việc dự báo nhu cầu chưa chính xác.
Không phải bài toán nào cũng cần Agent. Workflow kết hợp AI và Human Review thường thực tế hơn trong giai đoạn đầu.
Việc xác định rõ Human Boundary giúp giảm rủi ro và tăng khả năng triển khai thực tế.

Nếu làm lại:

```text
Tôi sẽ phỏng vấn thêm quản lý cửa hàng hoặc bộ phận mua hàng để có dữ liệu thực tế hơn về tỷ lệ hủy hàng, tỷ lệ hết hàng và thời gian lập đơn hàng, thay vì chỉ dựa trên giả định và quan sát quy trình hiện tại.
```

---

