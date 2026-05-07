# Peer Review Response

## Thông tin nhóm
<<<<<<< HEAD
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
=======
- Thành viên 1: Đỗ Huy Anh Duy - MSSV: 1871020190
- Thành viên 2: Đỗ Tiến Sơn - MSSV: 1871020508

## Thành viên 1 góp ý cho thành viên 2
Mã rõ ràng, nhưng cần thêm kiểm tra lỗi khi `recv_exact` không nhận đủ byte. Đề nghị viết thêm comment cho `des_socket_utils.py` để giải thích header và padding.

## Thành viên 2 góp ý cho thành viên 1
Sender hoạt động tốt, nhưng đầu ra cần ghi log rõ ràng và hỗ trợ biến môi trường để chạy local. Nên điều chỉnh để in ra UTF-8 trên Windows.

## Nhóm đã sửa gì sau góp ý
Chúng tôi đã bổ sung `sys.stdout.reconfigure(encoding='utf-8')` trong cả sender và receiver để tránh lỗi Unicode trên Windows. Chúng tôi cũng thêm `requirements.txt`, hoàn chỉnh tài liệu nhóm và mô tả threat model, và xác nhận bộ test tự động chạy thành công.
>>>>>>> b34f85548015b3d5e2d97d4be20e21f73b922d3e
