# Report 1 page - Lab 3

## Thông tin nhóm
<<<<<<< HEAD
- Thành viên 1: Đỗ Huy Anh Duy - MSSV: [1871020190]
- Thành viên 2: Đỗ Tiến Sơn - MSSV: [1871020508]

## Mục tiêu
Mục tiêu của bài lab là giúp sinh viên hiểu cách hoạt động của hệ thống giao tiếp giữa Sender và Receiver thông qua TCP socket. Đồng thời, bài lab giúp nắm được cách áp dụng mã hoá DES ở chế độ CBC, sử dụng IV và padding PKCS#7 để đảm bảo dữ liệu có thể mã hoá theo block. Ngoài ra, sinh viên còn học cách xây dựng packet truyền dữ liệu và đánh giá các vấn đề bảo mật trong hệ thống.

## Phân công thực hiện
- Thành viên 1 (Đỗ Huy Anh Duy):
  Phụ trách xây dựng Sender, bao gồm việc nhập message, thực hiện padding, mã hoá DES-CBC và gửi dữ liệu qua socket. Đồng thời xử lý logging phía gửi.

- Thành viên 2 (Đỗ Tiến Sơn):
  Phụ trách xây dựng Receiver, bao gồm nhận packet, tách dữ liệu, giải mã, unpad và hiển thị message. Đồng thời xử lý logging phía nhận.

- Phần làm chung:
  Cả hai cùng thiết kế cấu trúc packet, xây dựng module mã hoá (des_socket_utils), viết test cases, thực hiện threat model và hoàn thiện báo cáo.

## Cách làm
Hệ thống được triển khai gồm hai thành phần chính là Sender và Receiver giao tiếp với nhau qua TCP socket.

## Kết quả
Hệ thống hoạt động đúng với yêu cầu:
- Sender gửi thành công message đã mã hoá.
- Receiver nhận và giải mã chính xác message ban đầu.
- Các test case đều pass, bao gồm:
  + Padding/unpadding đúng
  + Encrypt/decrypt đúng
  + Xử lý message rỗng và message dài

Log chạy thực tế được lưu trong thư mục logs/ để làm minh chứng. Kết quả cho thấy hệ thống hoạt động ổn định trong môi trường local.

## Kết luận
Qua bài lab, nhóm đã hiểu rõ cách hoạt động của mã hoá đối xứng DES-CBC và cách truyền dữ liệu qua socket. Tuy nhiên, hệ thống vẫn tồn tại nhiều hạn chế về bảo mật như việc gửi key và IV dưới dạng plaintext và không có cơ chế xác thực dữ liệu. Điều này giúp nhóm nhận ra tầm quan trọng của các giao thức bảo mật như TLS trong thực tế. Bài lab cung cấp nền tảng quan trọng để phát triển các hệ thống an toàn hơn trong tương lai.
=======
- Thành viên 1: Đỗ Huy Anh Duy - MSSV: 1871020190
- Thành viên 2: Đỗ Tiến Sơn - MSSV: 1871020508

## Mục tiêu
Thiết kế hệ thống gửi/nhận dữ liệu mã hoá DES qua TCP socket, học cách sử dụng DES-CBC với padding PKCS#7, và xây dựng cơ chế header độ dài để định vị ciphertext.

## Phân công thực hiện
Đỗ Huy Anh Duy chịu trách nhiệm chính cho `sender.py`, tạo key/IV, mã hoá dữ liệu và gửi gói tin. Đỗ Tiến Sơn chịu trách nhiệm chính cho `receiver.py`, đọc header, nhận ciphertext và giải mã. Cả hai phối hợp viết `des_socket_utils.py`, kiểm thử tự động và hoàn thiện tài liệu.

## Cách làm
`sender.py` tạo key và IV 8 byte ngẫu nhiên, mã hoá plaintext bằng DES-CBC với padding PKCS#7, rồi gửi tuần tự key + IV + length header + ciphertext qua socket. `receiver.py` lắng nghe kết nối TCP, đọc chính xác 20 byte header, phân tích key, IV và độ dài ciphertext, sau đó đọc ciphertext và giải mã.

## Kết quả
Hệ thống đã chạy thành công với phép kiểm thử cục bộ: Sender gửi bản tin, receiver nhận và giải mã về bản rõ đúng. Bộ test tự động bao gồm kiểm tra padding/header, hợp lệ giao thức, tích hợp sender/receiver local, và hai tình huống negative với dữ liệu bị sửa và sai key.

## Kết luận
Kỹ thuật:
- DES-CBC yêu cầu padding để ciphertext có độ dài bội của 8 byte.
- Header độ dài giúp receiver biết cần đọc bao nhiêu ciphertext.
Bảo mật:
- Gửi key và IV plaintext trên cùng luồng TCP là điểm yếu nghiêm trọng.
- DES và DES-CBC đều không phù hợp cho hệ thống thực tế; cần dùng AES-GCM và trao đổi key an toàn.
>>>>>>> b34f85548015b3d5e2d97d4be20e21f73b922d3e
