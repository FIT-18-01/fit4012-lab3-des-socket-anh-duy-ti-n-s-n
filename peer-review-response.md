# Peer Review Response

## Thông tin nhóm
- Thành viên 1: Đỗ Huy Anh Duy - MSSV: [1871020190]
- Thành viên 2: Đỗ Tiến Sơn - MSSV: [1871020508]

---

## Thành viên 1 góp ý cho thành viên 2
Thành viên 1 nhận thấy phần Receiver được triển khai đúng chức năng nhưng cần cải thiện logging để dễ theo dõi quá trình nhận và giải mã dữ liệu. Ngoài ra, cần bổ sung thêm test case cho các trường hợp lỗi như sai key hoặc dữ liệu bị thay đổi.

---

## Thành viên 2 góp ý cho thành viên 1
Thành viên 2 đánh giá phần Sender hoạt động ổn định, tuy nhiên cần làm rõ hơn cấu trúc packet trong code để dễ hiểu và dễ bảo trì. Bên cạnh đó, nên bổ sung comment trong các hàm mã hoá để tăng tính rõ ràng.

---

## Nhóm đã sửa gì sau góp ý
Sau khi review chéo, nhóm đã thực hiện một số cải tiến:
- Bổ sung logging chi tiết cho cả Sender và Receiver.
- Thêm các test case kiểm tra sai key và tampering dữ liệu.
- Cải thiện comment trong code để dễ hiểu hơn.
- Làm rõ cấu trúc packet (header + IV + ciphertext).