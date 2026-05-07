# Report 1 page - Lab 3

## Thông tin nhóm
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