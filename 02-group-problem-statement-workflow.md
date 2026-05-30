Workflow before / after

CURRENT STATE — 2–3 giờ/ngày
[1 Xem báo cáo bán hàng: 30']
→ [2 Xem tồn kho hiện tại: 20']
→ [3 Xem báo cáo hàng hủy: 20']
→ [4 Phân tích từng mặt hàng: 40']
→ [5 Ước lượng nhu cầu ngày mai: 30']  <-- bottleneck
→ [6 Điều chỉnh số lượng đặt hàng: 20']
→ [7 Tạo và gửi đơn hàng: 10']

Các vấn đề hiện tại
- Đặt hàng dựa trên kinh nghiệm cá nhân
- Chỉ nhìn dữ liệu ngày trước đó
- Không tính đến thời tiết, cuối tuần, lễ, khuyến mãi
- Dễ nhập dư gây hủy hàng
- Dễ nhập thiếu gây hết hàng

FUTURE STATE — 20–30 phút/ngày
[1 Tự động lấy dữ liệu bán hàng, tồn kho: 2']
→ [2 AI phân tích xu hướng bán hàng: 2']
→ [3 AI dự báo nhu cầu từng SKU: 3']
→ [4 AI đề xuất số lượng đặt hàng: 3']
→ [5 Chị Hương review & điều chỉnh: 15']  <-- human boundary
→ [6 Gửi đơn cho nhà cung cấp: 5']
Fallback
Nếu AI dự báo bất thường hoặc dữ liệu thiếu:
→ Chị Hương điều chỉnh thủ công dựa trên kinh nghiệm.