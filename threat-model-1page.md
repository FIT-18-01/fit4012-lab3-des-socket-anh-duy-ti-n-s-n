# Threat Model - Lab 3

## Thông tin nhóm
- Thành viên 1: Đỗ Huy Anh Duy - MSSV: [1871020190]
- Thành viên 2: Đỗ Tiến Sơn - MSSV: [1871020508]

## Assets
Các tài sản cần được bảo vệ trong hệ thống:
- Nội dung message (plaintext)
- Encryption key (DES key)
- Initialization Vector (IV)
- Tính toàn vẹn (integrity) của dữ liệu
- Kết nối giữa Sender và Receiver

## Attacker model
Kẻ tấn công được giả định có khả năng:
- Nghe lén lưu lượng mạng (sniffing traffic)
- Chặn và sửa đổi packet (Man-in-the-Middle)
- Gửi packet giả đến Receiver
- Replay lại các packet đã gửi trước đó

Kẻ tấn công không cần quyền truy cập trực tiếp vào hệ thống, chỉ cần nằm trên cùng mạng.

## Threats
Các mối đe doạ chính:

1. Lộ key và IV:
   Vì key và IV được gửi dưới dạng plaintext qua TCP, attacker có thể dễ dàng lấy được và giải mã toàn bộ message.

2. Man-in-the-Middle (MITM):
   Attacker có thể chặn, sửa hoặc thay thế message trước khi đến Receiver.

3. Data tampering:
   Không có cơ chế kiểm tra integrity → dữ liệu có thể bị sửa mà không bị phát hiện.

4. Replay attack:
   Attacker có thể gửi lại packet cũ để đánh lừa hệ thống.

## Mitigations
Các biện pháp giảm thiểu:

1. Sử dụng TLS:
   Thay TCP thường bằng TLS để mã hoá toàn bộ kênh truyền.

2. Không gửi key trực tiếp:
   Sử dụng cơ chế trao đổi khoá an toàn như Diffie-Hellman.

3. Thêm kiểm tra integrity:
   Sử dụng HMAC để đảm bảo dữ liệu không bị thay đổi.

4. Sử dụng thuật toán mạnh hơn:
   Thay DES bằng AES vì DES đã lỗi thời và dễ bị tấn công.

## Residual risks
Các rủi ro còn lại sau khi áp dụng biện pháp:

- Sai cấu hình TLS vẫn có thể dẫn đến lỗ hổng bảo mật
- Attacker có thể tấn công ở mức người dùng (social engineering)
- Lỗi lập trình có thể gây rò rỉ thông tin
