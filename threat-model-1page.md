# Threat Model - Lab 3

## Thông tin nhóm
<<<<<<< HEAD
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
=======
- Thành viên 1: Đỗ Huy Anh Duy - MSSV: 1871020190
- Thành viên 2: Đỗ Tiến Sơn - MSSV: 1871020508

## Assets
- Bản tin gốc (plaintext) gửi giữa sender và receiver.
- DES key 8 byte và IV 8 byte được truyền qua mạng.
- Ciphertext và header độ dài.

## Attacker model
Kẻ tấn công có quyền lắng nghe luồng TCP nội bộ và có thể thay đổi gói tin trên đường truyền. Kẻ tấn công không kiểm soát hoàn toàn hai đầu sender/receiver nhưng có thể can thiệp vào mạng.

## Threats
- Kẻ tấn công nghe được key và IV plaintext khi chúng được truyền cùng packet.
- Kẻ tấn công sửa ciphertext (tamper) khiến giải mã sai hoặc lộ dữ liệu không chính xác.
- Kẻ tấn công thực hiện replay lại packet cũ.
- Kẻ tấn công có thể thay đổi header độ dài và làm hỏng quá trình đọc dữ liệu.

## Mitigations
- Không bao giờ truyền key và IV plaintext trong cùng luồng dữ liệu; cần dùng kênh an toàn hoặc cơ chế trao đổi key.
- Dùng MAC / HMAC để phát hiện thay đổi ciphertext và header.
- Dùng phiên bản thuật toán mạnh hơn như AES-GCM thay vì DES-CBC.
- Thực hiện kiểm tra tính toàn vẹn độ dài packet và reject packet không đúng định dạng.

## Residual risks
Hệ thống vẫn chịu rủi ro nếu kẻ tấn công nắm quyền truy cập mạng nội bộ, vì DES bản thân đã yếu và không bảo vệ chống replay nếu không có thông tin phiên.
>>>>>>> b34f85548015b3d5e2d97d4be20e21f73b922d3e
