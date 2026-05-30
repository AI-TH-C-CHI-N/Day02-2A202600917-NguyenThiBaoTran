## Case : **Quản lý các đơn hủy và đặt hàng của chuỗi cửa hàng**

Chị Hương là quản lý vận hành của chuỗi cửa hàng thực phẩm BNB. Mỗi ngày, chị phải lên đơn đặt hàng cho hàng trăm mặt hàng dựa trên báo cáo bán hàng, tồn kho và hàng hủy của ngày trước đó.

Hiện nay, việc đặt hàng chủ yếu dựa vào kinh nghiệm và thói quen. Nếu một mặt hàng bị hủy nhiều, chị sẽ giảm lượng đặt cho ngày hôm sau; nếu bán hết nhanh, chị sẽ tăng thêm số lượng nhập. Tuy nhiên, chị không có công cụ để dự báo chính xác nhu cầu khách hàng dựa trên các yếu tố như xu hướng bán hàng, thời tiết, cuối tuần hay chương trình khuyến mãi.

Điều này dẫn đến hai vấn đề chính: nhiều mặt hàng bị đặt dư và phải hủy bỏ, trong khi một số mặt hàng bán chạy lại không được nhập đủ, gây tình trạng hết hàng và mất doanh thu. Ngoài ra, chị Hương phải dành 2–3 giờ mỗi ngày để xem báo cáo và lập kế hoạch đặt hàng nhưng kết quả vẫn phụ thuộc nhiều vào kinh nghiệm cá nhân.

## Vì sao đây là ví dụ tốt?

- Có actor cụ thể.
- Có workflow lặp lại hằng ngày.
- Có bottleneck rõ.
- Có tác động kinh doanh trực tiếp.
- Có dữ liệu đo lường.
- Có thể so sánh Rule / Workflow / Agent.
- Có thể vẽ before/after workflow.

---

# 01 — Individual Problem Scan

## Scan rộng

| #  | Lăng kính          | Problem quan sát được                                                            | Ai đang đau?                   | Dấu hiệu thật                           |
| -- | ------------------ | -------------------------------------------------------------------------------- | ------------------------------ | --------------------------------------- |
| 1  | Lặp lại            | Mỗi ngày phải lập đơn đặt hàng cho hàng trăm SKU dựa trên kinh nghiệm cá nhân    | Quản lý vận hành               | Mất 2–3 giờ/ngày                        |
| 2  | Tốn thời gian      | Phải xem nhiều báo cáo bán hàng, tồn kho, hàng hủy trước khi quyết định đặt hàng | Quản lý vận hành               | Mở nhiều file Excel và dashboard        |
| 3  | AI có thể tốt hơn  | Không dự báo được nhu cầu ngày mai dựa trên xu hướng bán hàng                    | Quản lý vận hành               | Đặt hàng chủ yếu theo cảm tính          |
| 4  | Pain từ người khác | Cửa hàng thường xuyên hết các mặt hàng bán chạy vào giờ cao điểm                 | Nhân viên cửa hàng, khách hàng | Khách không mua được sản phẩm mong muốn |
| 5  | Tốn chi phí        | Đặt dư hàng dẫn đến hủy hàng do hết hạn hoặc giảm chất lượng                     | Công ty                        | Tỷ lệ hủy hàng cao                      |
| 6  | AI có thể tốt hơn  | Không phát hiện sớm các mặt hàng đang có xu hướng bán tăng mạnh                  | Quản lý vận hành               | Hàng bán chạy thường bị thiếu           |
| 7  | Pain từ người khác | Nhà cung cấp nhận đơn hàng thay đổi thất thường mỗi ngày                         | Nhà cung cấp                   | Khó chuẩn bị nguồn hàng                 |
| 8  | Lặp lại            | Mỗi ngày phải điều chỉnh số lượng nhập theo cùng một cách thủ công               | Quản lý vận hành               | Quy trình giống nhau mỗi ngày           |
| 9  | Tốn thời gian      | Không có cảnh báo SKU có nguy cơ hết hàng hoặc tồn kho quá mức                   | Quản lý vận hành               | Phải tự kiểm tra từng mặt hàng          |
| 10 | AI có thể tốt hơn  | Không tận dụng được dữ liệu thời tiết, ngày lễ, khuyến mãi để dự báo nhu cầu     | Công ty, quản lý vận hành      | Quyết định đặt hàng thiếu chính xác     |


Vì sao phần scan này mạnh:

- Có scan rộng trước khi hội tụ.
- Có nhiều lăng kính khác nhau.
- Mỗi problem có actor và dấu hiệu thật.
- Không bắt đầu bằng "làm chatbot" hoặc "xây agent".

## Top 3

| Rank  | Problem                                                         | Vì sao chọn                                                                                                 | Điều còn chưa chắc                                                                |
| ----- | --------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **1** | Đặt hàng hằng ngày dựa trên kinh nghiệm thay vì dự báo nhu cầu  | Là nguyên nhân gốc gây ra cả hàng hủy và thiếu hàng. Tác động trực tiếp đến doanh thu, chi phí và vận hành. | Cần dữ liệu lịch sử đủ tốt để dự báo chính xác.                                   |
| **2** | Hàng bán chạy bị thiếu do không phát hiện xu hướng tăng nhu cầu | Gây mất doanh thu và ảnh hưởng trải nghiệm khách hàng. Đây là pain mà ban lãnh đạo rất dễ nhìn thấy.        | Cần đo được lượng "lost sales" thực tế.                                           |
| **3** | Hủy hàng nhiều do nhập dư                                       | Gây lãng phí chi phí nhập hàng, lưu kho và xử lý hàng hủy. Có KPI rõ ràng để đo lường.                      | Không phải tất cả hàng hủy đều do dự báo sai, có thể do chất lượng hoặc bảo quản. |


## Problem Card #1 — Đặt hàng hằng ngày dựa trên kinh nghiệm thay vì dự báo nhu cầu

**Problem 1 câu:**  
Mỗi ngày chị Hương phải quyết định số lượng đặt hàng cho hàng trăm mặt hàng dựa trên kinh nghiệm và báo cáo ngày trước đó, dẫn đến việc đặt hàng thiếu chính xác và ảnh hưởng đến hiệu quả kinh doanh.

**Actor:**  
Chị Hương – Quản lý vận hành chuỗi cửa hàng thực phẩm BNB.

**Thời điểm / bối cảnh:**  
Cuối mỗi ngày, trước khi gửi đơn đặt hàng cho nhà cung cấp.

**Current workflow:**

```text
1. Xem báo cáo bán hàng
2. Xem báo cáo tồn kho
3. Xem báo cáo hàng hủy
4. So sánh với các ngày trước
5. Ước lượng nhu cầu ngày mai
6. Điều chỉnh số lượng đặt hàng
7. Gửi đơn cho nhà cung cấp
```

**Bottleneck:**  
Bước 5 — Ước lượng nhu cầu ngày mai.

Quản lý phải tự suy luận dựa trên kinh nghiệm thay vì có công cụ dự báo.

**Impact:**  
Impact
Mất 2–3 giờ mỗi ngày.
Quyết định phụ thuộc vào kinh nghiệm cá nhân.
Độ chính xác không ổn định giữa các quản lý.

**Success metric:**  
Thời gian lập đơn < 30 phút.
Độ chính xác dự báo > 85%.
Giảm số lần điều chỉnh đơn hàng khẩn cấp.

**Non-AI alternative:**  
Quy tắc tăng/giảm theo doanh số hôm trước.
Dashboard thống kê bán hàng.

**AI hypothesis:**  
AI dự báo nhu cầu từng SKU dựa trên lịch sử bán hàng, thời tiết, ngày lễ và chương trình khuyến mãi.

**Quick gut:**  
Workflow.

### Draft current workflow

```text
CURRENT STATE — 2-3 giờ/ngày

[1 Xem báo cáo bán hàng: 30']
→ [2 Xem tồn kho hiện tại: 20']
→ [3 Xem báo cáo hàng hủy: 20']
→ [4 Phân tích từng nhóm hàng: 40']
→ [5 Ước lượng nhu cầu ngày mai: 30']  <-- bottleneck
→ [6 Điều chỉnh số lượng đặt hàng: 20']
→ [7 Gửi đơn cho nhà cung cấp: 10']
```

### Draft future workflow

```text
FUTURE STATE — 20-30 phút/ngày

[1 Tự động lấy dữ liệu bán hàng, tồn kho: 2']
→ [2 AI phân tích xu hướng bán hàng: 2']
→ [3 AI dự báo nhu cầu từng SKU: 3']
→ [4 AI đề xuất số lượng đặt hàng: 2']
→ [5 Quản lý review & điều chỉnh: 15']  <-- human boundary
→ [6 Gửi đơn cho nhà cung cấp: 5']
Human boundary : AI chỉ đề xuất.
    Quản lý vẫn là người quyết định cuối cùng:
    - Chọn số lượng đặt hàng
    - Xử lý các trường hợp đặc biệt
    - Phê duyệt đơn hàng trước khi gửi nhà cung cấp

Fallback: Nếu dự báo AI bất thường hoặc thiếu dữ liệu:
→ Quản lý quay về quy trình đặt hàng thủ công như hiện tại.
```

## Problem Cards #2 và #3 — tóm tắt
| Card                   | Actor            | Bottleneck                                               | Metric                     | Quick gut | Vì sao chưa chọn làm #1                                              |
| ---------------------- | ---------------- | -------------------------------------------------------- | -------------------------- | --------- | -------------------------------------------------------------------- |
| Hàng bán chạy bị thiếu | Quản lý vận hành | Không phát hiện xu hướng tăng nhu cầu trước khi hết hàng | Out-of-Stock 12% → dưới 5% | Workflow  | Thực chất là hậu quả của việc dự báo nhu cầu chưa chính xác          |
| Hủy hàng do nhập dư    | Quản lý vận hành | Không xác định được lượng hàng cần nhập tối ưu           | Hủy hàng 8% → dưới 4%      | Workflow  | Cũng là hệ quả của việc đặt hàng dựa trên kinh nghiệm thay vì dự báo |


---
