
# 02 — Group Problem Statement

## Shortlist và score

| Candidate                            | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | AI phù hợp | Tổng |
| ------------------------------------ | -------: | ----------: | ---------------: | -------------: | ---------: | ---: |
| Dự báo nhu cầu và đặt hàng hằng ngày |        5 |           5 |                5 |              5 |          5 |   25 |
| Hàng bán chạy bị thiếu               |        5 |           4 |                5 |              5 |          4 |   23 |
| Hủy hàng do nhập dư                  |        5 |           4 |                5 |              5 |          4 |   23 |

Nhóm chọn: **Dự báo nhu cầu và đặt hàng hằng ngày**.

Vì sao chọn
- Là nguyên nhân gốc tạo ra cả hai vấn đề còn lại:
- Thiếu hàng bán chạy.
- Hủy hàng do nhập dư.
- Có workflow rõ ràng và diễn ra hằng ngày.
- Có dữ liệu lịch sử sẵn có:
- Doanh số bán hàng.
- Tồn kho.
- Hàng hủy.
- Chương trình khuyến mãi.
- Tác động trực tiếp đến:
- Doanh thu.
- Chi phí.
- Hiệu quả vận hành.
- Có thể đo lường hiệu quả sau khi triển khai.
Vì sao không chọn các bài khác:
| Candidate              | Vì sao chưa chọn                                                           |
| ---------------------- | -------------------------------------------------------------------------- |
| Hàng bán chạy bị thiếu | Là hậu quả của việc dự báo nhu cầu chưa chính xác.                         |
| Hủy hàng do nhập dư    | Cũng là hậu quả của việc đặt hàng theo kinh nghiệm thay vì dự báo dữ liệu. |


## Quick validation

Quan sát quy trình hiện tại cho thấy:

Người quản lý chủ yếu dựa vào báo cáo ngày hôm trước để ra quyết định.
Chưa có công cụ dự báo nhu cầu cho ngày tiếp theo.
Quy trình mất khoảng 2–3 giờ mỗi ngày.
Thường xuyên xảy ra hai tình trạng:
Hết hàng đối với sản phẩm bán chạy.
Hủy hàng đối với sản phẩm bán chậm.

Insight sau validation:

```text
Vấn đề cốt lõi không phải là hủy hàng hay thiếu hàng.

Vấn đề thực sự nằm ở việc không có khả năng dự báo nhu cầu
để hỗ trợ quyết định đặt hàng hằng ngày.
```

## Research giải pháp

| Nguồn / Tool / Case                                                                                                                 | Họ giải quyết phần nào?                  | Điểm mạnh                                   | Khoảng trống / Rủi ro                            | Bài học rút ra                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------- | ------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------ |
| [Blue Yonder](https://blueyonder.com?utm_source=chatgpt.com)                                                                        | Demand Forecasting & Replenishment       | Dự báo nhu cầu và đề xuất nhập hàng tự động | Chi phí triển khai lớn, phù hợp doanh nghiệp lớn | Dữ liệu lịch sử là yếu tố quan trọng nhất để dự báo                      |
| [SAP Integrated Business Planning (IBP)](https://www.sap.com/products/scm/integrated-business-planning.html?utm_source=chatgpt.com) | Supply Chain Planning                    | Kết hợp bán hàng, tồn kho và dự báo         | Hệ thống phức tạp                                | Quyết định đặt hàng nên dựa trên nhiều nguồn dữ liệu                     |
| [Oracle Retail Demand Forecasting](https://www.oracle.com/retail/retail-demand-forecasting/?utm_source=chatgpt.com)                 | Forecast nhu cầu bán lẻ                  | Dự báo theo từng SKU và cửa hàng            | Cần dữ liệu chất lượng cao                       | AI nên hỗ trợ từng SKU thay vì dự báo tổng thể                           |
| [Microsoft Fabric Forecasting Solutions](https://www.microsoft.com/fabric?utm_source=chatgpt.com)                                   | Phân tích dữ liệu và dự báo              | Tích hợp dữ liệu từ nhiều nguồn             | Cần đội ngũ dữ liệu vận hành                     | Có thể tận dụng dữ liệu sẵn có thay vì xây mới toàn bộ                   |
| [Google Cloud Supply Chain AI](https://cloud.google.com/supply-chain-center?utm_source=chatgpt.com)                                 | Dự báo nhu cầu và quản lý chuỗi cung ứng | Khả năng xử lý dữ liệu lớn                  | Chi phí và tích hợp hệ thống                     | AI nên đóng vai trò hỗ trợ ra quyết định thay vì tự quyết định hoàn toàn |


Research takeaway:
Qua nghiên cứu các giải pháp hiện có, có thể thấy rằng:
```text
Không nên xây một AI Agent tự động đặt hàng ngay từ đầu.

Hầu hết các giải pháp thành công đều đi theo hướng:
1. Thu thập dữ liệu bán hàng và tồn kho
2. Dự báo nhu cầu
3. Đề xuất số lượng đặt hàng
4. Người quản lý review và phê duyệt
```

## Problem Statement v0

| Field              | Nội dung                                                                                                                |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| **Actor**          | Chị Hương – Quản lý vận hành chuỗi cửa hàng thực phẩm BNB.                                                              |
| **Workflow**       | Xem báo cáo bán hàng → Xem tồn kho → Xem hàng hủy → Ước lượng nhu cầu → Lập đơn hàng → Gửi nhà cung cấp.                |
| **Bottleneck**     | Việc dự báo nhu cầu ngày hôm sau hoàn toàn dựa trên kinh nghiệm và dữ liệu của ngày trước đó.                           |
| **Impact**         | Mất 2–3 giờ mỗi ngày để lập đơn hàng; thường xuyên xảy ra tình trạng nhập dư gây hủy hàng hoặc nhập thiếu gây hết hàng. |
| **Success Metric** | Giảm thời gian lập đơn xuống dưới 30 phút; giảm tỷ lệ hủy hàng và tỷ lệ hết hàng.                                       |
| **Boundary**       | Không tự động gửi đơn hàng; quyết định cuối cùng vẫn thuộc về người quản lý.                                            |


## Rule / Workflow / Agent

| Mức          | Phương án                                                                            | Khi nào đủ                                | Rủi ro                                                         | Chọn?      |
| ------------ | ------------------------------------------------------------------------------------ | ----------------------------------------- | -------------------------------------------------------------- | ---------- |
| **Rule**     | Nếu hàng hủy nhiều thì giảm nhập, nếu bán hết thì tăng nhập                          | Đủ khi số lượng SKU ít và nhu cầu ổn định | Không phản ánh được xu hướng thị trường, thời tiết, khuyến mãi | Không chọn |
| **Workflow** | Thu thập dữ liệu → AI dự báo nhu cầu → AI đề xuất số lượng đặt hàng → Quản lý review | Phù hợp với quy trình đặt hàng hiện tại   | Dự báo có thể sai nếu dữ liệu thiếu                            | Chọn       |
| **Agent**    | AI tự dự báo, tạo đơn hàng và gửi nhà cung cấp                                       | Chỉ phù hợp khi độ tin cậy rất cao        | Rủi ro tài chính lớn nếu đặt hàng sai                          | Chưa chọn  |


Mức chọn:

```text
Workflow.
```

Vì sao:

- Workflow đặt hàng có các bước rõ ràng và lặp lại mỗi ngày.
- AI phù hợp với nhiệm vụ dự báo và đề xuất.
- Người quản lý vẫn giữ quyền kiểm soát quyết định cuối cùng.
- Chưa cần mức độ tự động hóa cao như Agent.

## Problem Statement v1

| Field                            | Nội dung                                                                                                                                 |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor**                        | Chị Hương – Quản lý vận hành chuỗi cửa hàng thực phẩm BNB.                                                                               |
| **Workflow**                     | Xem báo cáo bán hàng → Kiểm tra tồn kho → Đánh giá hàng hủy → Dự báo nhu cầu → Lập đơn hàng → Gửi nhà cung cấp.                          |
| **Bottleneck**                   | Dự báo nhu cầu ngày hôm sau mất nhiều thời gian và phụ thuộc vào kinh nghiệm cá nhân.                                                    |
| **Impact**                       | Mỗi ngày mất 2–3 giờ lập đơn; phát sinh hàng hủy do nhập dư và mất doanh thu do hết hàng.                                                |
| **Success Metric**               | Thời gian lập đơn < 30 phút; tỷ lệ hủy hàng < 4%; tỷ lệ hết hàng < 5%.                                                                   |
| **Boundary**                     | AI không tự gửi đơn hàng và không thay thế quyết định của người quản lý.                                                                 |
| **AI Intervention Point**        | Sau khi dữ liệu bán hàng, tồn kho và hàng hủy được tổng hợp, trước bước lập đơn hàng.                                                    |
| **Mức chọn**                     | Workflow: AI dự báo nhu cầu và đề xuất số lượng đặt hàng, quản lý review trước khi phê duyệt.                                            |
| **Rủi ro & người thật kiểm tra** | Dự báo sai do dữ liệu bất thường hoặc thay đổi đột ngột của thị trường. Người quản lý phải kiểm tra và phê duyệt trước khi gửi đơn hàng. |


## Final decision

| Field                     | Nội dung                                                                                                                                                                                                        |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Actor**                 | Chị Hương – Quản lý vận hành chuỗi cửa hàng thực phẩm BNB.                                                                                                                                                      |
| **Workflow**              | Mỗi ngày chị Hương xem báo cáo bán hàng, tồn kho và hàng hủy để quyết định số lượng đặt hàng cho hàng trăm mặt hàng vào ngày hôm sau.                                                                           |
| **Bottleneck**            | Việc dự báo nhu cầu chủ yếu dựa trên kinh nghiệm cá nhân và dữ liệu ngắn hạn nên tốn nhiều thời gian và dễ sai lệch.                                                                                            |
| **Impact**                | Dẫn đến hai vấn đề lớn: nhập dư gây hủy hàng và nhập thiếu gây hết hàng, ảnh hưởng trực tiếp đến chi phí vận hành và doanh thu.                                                                                 |
| **Success Metric**        | Giảm thời gian lập đơn từ 2–3 giờ xuống dưới 30 phút; giảm tỷ lệ hủy hàng từ 8% xuống dưới 4%; giảm tỷ lệ hết hàng từ 12% xuống dưới 5%.                                                                        |
| **Boundary**              | AI chỉ hỗ trợ dự báo nhu cầu và đề xuất số lượng đặt hàng; không tự động gửi đơn hoặc thay thế quyết định của người quản lý.                                                                                    |
| **AI Intervention Point** | Sau bước tổng hợp dữ liệu bán hàng và tồn kho, trước bước quyết định số lượng đặt hàng.                                                                                                                         |
| **Mức chọn**              | Workflow.                                                                                                                                                                                                       |
| **Rủi ro & Human Review** | AI có thể dự báo chưa chính xác trong các trường hợp bất thường như lễ lớn, khủng hoảng nguồn cung hoặc thay đổi hành vi mua sắm. Chị Hương là người chịu trách nhiệm kiểm tra và phê duyệt đơn hàng cuối cùng. |


---