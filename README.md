


---

1. Data at Rest & Data in Transit

Data at Rest: Dữ liệu được lưu trữ tĩnh, không thay đổi hoặc di chuyển (ví dụ: file trên ổ cứng, dữ liệu trong database).

Data in Transit: Dữ liệu đang được truyền qua mạng (ví dụ: khi bạn gửi email hoặc tải trang web).

Mã hóa dữ liệu (Encryption): Giúp bảo vệ dữ liệu khỏi bị đánh cắp hoặc thay đổi. Có hai loại mã hóa chính:

Encryption at Rest: Dữ liệu được mã hóa ngay cả khi nó không di chuyển.

Encryption in Transit: Dữ liệu được mã hóa khi truyền qua mạng.



Ví dụ thực tế:
Khi bạn lưu tài liệu quan trọng trên Google Drive, Google sẽ dùng Encryption at Rest để bảo vệ dữ liệu. Khi bạn tải tài liệu đó lên hoặc xuống, Google dùng Encryption in Transit để mã hóa trong lúc truyền tải.


---

2. SSL/TLS & HTTPS

SSL/TLS là gì?

SSL (Secure Sockets Layer): Giao thức bảo mật giúp mã hóa dữ liệu giữa client (trình duyệt) và server.

TLS (Transport Layer Security): Phiên bản nâng cấp của SSL, an toàn hơn.

HTTPS (HyperText Transfer Protocol Secure): Là phiên bản bảo mật của HTTP, sử dụng SSL/TLS để mã hóa dữ liệu.


Ví dụ thực tế:
Bạn đăng nhập vào ngân hàng trực tuyến. Nếu website có HTTPS, thông tin đăng nhập của bạn sẽ được mã hóa, hacker không thể đọc được.


---

3. Mã hóa đối xứng (Symmetric) và bất đối xứng (Asymmetric)

Mã hóa đối xứng (Symmetric Encryption)

Chỉ sử dụng một khóa duy nhất để mã hóa và giải mã.

Ưu điểm: Nhanh và hiệu quả cho dữ liệu lớn.

Nhược điểm: Nếu kẻ tấn công lấy được khóa, họ có thể giải mã dữ liệu.


Ví dụ thực tế:
Bạn và bạn bè có chung một mật khẩu để mở file ZIP đã mã hóa. Ai có mật khẩu đó đều có thể mở file.

Mã hóa bất đối xứng (Asymmetric Encryption)

Sử dụng hai khóa:

Public key: Dùng để mã hóa.

Private key: Dùng để giải mã.


Public key có thể chia sẻ cho bất kỳ ai, nhưng private key phải được giữ bí mật.

Hệ thống này giúp bảo vệ dữ liệu ngay cả khi có nhiều người truy cập.


Ví dụ thực tế:
Khi bạn gửi email bảo mật bằng PGP:

1. Bạn sử dụng public key của người nhận để mã hóa email.


2. Chỉ người nhận có private key mới có thể giải mã.



Ứng dụng của cả hai loại mã hóa

HTTPS kết hợp cả hai loại mã hóa:

Dùng mã hóa bất đối xứng để trao đổi khóa an toàn.

Sau đó, dùng mã hóa đối xứng để truyền dữ liệu nhanh chóng.




---

4. Chứng chỉ số & Certificate Authority (CA)

Chứng chỉ số (Digital Certificate): Giống như một thẻ căn cước chứng minh danh tính của website.

Certificate Authority (CA): Tổ chức phát hành chứng chỉ số, đảm bảo rằng website là đáng tin cậy.


Cách trình duyệt kiểm tra chứng chỉ:

1. Khi bạn truy cập https://example.com, trình duyệt kiểm tra xem website có chứng chỉ hợp lệ không.


2. Nếu chứng chỉ được cấp bởi một CA đáng tin cậy, trình duyệt hiển thị biểu tượng ổ khóa.


3. Nếu không, bạn sẽ thấy cảnh báo "Kết nối không an toàn".



Ví dụ thực tế:

Let’s Encrypt là một CA miễn phí cấp chứng chỉ cho các website nhỏ.

Google Chrome tin tưởng các CA lớn như DigiCert, GlobalSign...



---

5. DNS - Hệ thống phân giải tên miền

DNS là gì?

DNS (Domain Name System) là hệ thống giúp chuyển đổi tên miền (VD: google.com) thành địa chỉ IP (VD: 8.8.8.8).


Tại sao cần DNS?

Máy tính sử dụng địa chỉ IP để giao tiếp, nhưng con người thì nhớ tên miền dễ hơn.


Cách DNS hoạt động:

1. Bạn nhập facebook.com vào trình duyệt.


2. Trình duyệt hỏi DNS server: "Địa chỉ IP của facebook.com là gì?"


3. DNS server trả về địa chỉ IP.


4. Trình duyệt kết nối đến Facebook.



Ví dụ thực tế:

Google có DNS server công cộng: 8.8.8.8

Cloudflare có DNS rất nhanh: 1.1.1.1



---

6. SSL Offloading & Istio

SSL Offloading (SSL Termination)

Là quá trình xử lý mã hóa/giải mã SSL/TLS ở một máy chủ trung gian (proxy) thay vì backend server.

Giúp giảm tải cho backend, tối ưu hiệu suất.


Ví dụ thực tế:

Nginx hoặc AWS Load Balancer có thể thực hiện SSL Offloading, giúp backend server chỉ xử lý logic mà không cần lo về mã hóa.


Istio & Service Mesh

Istio là một Service Mesh giúp quản lý giao tiếp giữa các microservices.

Nó cung cấp mã hóa tự động giữa các dịch vụ, giúp bảo mật nội bộ mà không cần thay đổi code.


Ví dụ thực tế:

Một hệ thống K8S có nhiều container, Istio giúp mã hóa tất cả giao tiếp giữa chúng mà không cần cấu hình SSL riêng lẻ.



---
Chi tiết hơn về cách kết hợp mã hóa đối xứng và bất đối xứng trong HTTPS

1️⃣ Mã hóa đối xứng là gì?

Mã hóa đối xứng giống như việc bạn và bạn của bạn có cùng một chiếc chìa khóa để mở một chiếc hộp.

Bạn dùng chìa khóa này để khóa hộp, rồi gửi cho bạn của bạn.

Khi nhận được, bạn của bạn dùng đúng chìa khóa đó để mở hộp và đọc thư bên trong.


Ưu điểm: 🔥 Rất nhanh, dữ liệu được mã hóa và giải mã nhanh chóng.
Nhược điểm: 🔑 Nếu ai đó lấy được chìa khóa, họ có thể mở tất cả các hộp khác.

📌 Vấn đề lớn: Làm sao gửi chìa khóa đối xứng một cách an toàn?


---

2️⃣ Mã hóa bất đối xứng là gì?

Mã hóa bất đối xứng dùng hai loại khóa riêng biệt:

1. Public key (khóa công khai) – ai cũng có thể biết.


2. Private key (khóa riêng tư) – chỉ chủ sở hữu biết.



Giống như:

Bạn có một hộp thư có khe bỏ thư vào (public key).

Chỉ có bạn có chìa khóa mở hộp thư (private key).

Ai cũng có thể bỏ thư vào, nhưng chỉ bạn mới có thể lấy thư ra.


Ưu điểm: 🔐 An toàn hơn, vì không cần gửi khóa riêng tư.
Nhược điểm: 🐢 Chậm hơn nhiều so với mã hóa đối xứng.


---

3️⃣ Vấn đề của cả hai phương pháp

➡️ Vậy giải pháp là gì?
➡️ Dùng mã hóa bất đối xứng để gửi khóa đối xứng, sau đó dùng mã hóa đối xứng để truyền dữ liệu nhanh hơn!


---

4️⃣ HTTPS kết hợp cả hai như thế nào?

Ví dụ dễ hiểu:
👉 Bạn muốn gửi tin nhắn bí mật cho một người bạn qua mạng.

🚀 Bước 1: Máy chủ gửi Public Key

Máy chủ web (VD: https://example.com) có một cặp public key / private key.

Máy chủ gửi public key của mình cho trình duyệt của bạn.


🚀 Bước 2: Trình duyệt tạo và mã hóa khóa đối xứng

Trình duyệt của bạn tự tạo ra một khóa đối xứng ngẫu nhiên (gọi là session key).

Trình duyệt dùng public key của máy chủ để mã hóa session key và gửi nó đến máy chủ.


🚀 Bước 3: Máy chủ giải mã session key

Máy chủ dùng private key để giải mã session key.

Giờ cả trình duyệt và máy chủ đều có cùng một khóa đối xứng để mã hóa dữ liệu.


🚀 Bước 4: Mã hóa đối xứng bắt đầu làm việc

Từ lúc này, mọi dữ liệu giữa trình duyệt và máy chủ sẽ được mã hóa bằng khóa đối xứng.

Vì mã hóa đối xứng nhanh hơn, nên quá trình truyền dữ liệu sẽ không bị chậm.



---

5️⃣ Ví dụ thực tế – So sánh với gửi thư

📬 Cách truyền thống (Không an toàn):

1. Bạn viết thư và để trong một hộp khóa.


2. Bạn gửi hộp khóa đó cho bạn của bạn.


3. Bạn phải gửi luôn chìa khóa để họ mở hộp.
❌ Nếu ai đó lấy trộm chìa khóa, họ có thể mở hộp và đọc thư.



🔒 Cách HTTPS (An toàn):

1. Bạn của bạn gửi cho bạn một ổ khóa mở sẵn (public key).


2. Bạn khóa thư của bạn( chứa session key do trình duyệt gen ) trong một hộp bằng ổ khóa(public key) này.


3. Bạn gửi hộp đến cho bạn của bạn.


4. Chỉ bạn của bạn có chìa khóa riêng (private key) để mở hộp!


5. Sau khi mở hộp, bạn của bạn tìm thấy một chìa khóa đặc biệt (session key).


6. Cả hai bây giờ có chung một chìa khóa và tiếp tục trao đổi thư bằng chìa khóa này.



🛡️ Kết quả:

Kẻ trộm không thể mở hộp đầu tiên vì họ không có private key.

Sau khi nhận chìa khóa đối xứng, hai người có thể trao đổi thư rất nhanh.



---

6️⃣ Vì sao HTTPS an toàn?

✔ Dữ liệu không thể bị đọc trộm giữa đường (do đã được mã hóa).
✔ Không ai có thể giả mạo máy chủ (nhờ chứng chỉ SSL/TLS).
✔ Bảo vệ dữ liệu khi truy cập ngân hàng, email, v.v.

🚀 Tóm gọn quy trình:

1. Mã hóa bất đối xứng (public/private key) – Dùng để gửi khóa đối xứng an toàn.


2. Mã hóa đối xứng (session key) – Dùng để trao đổi dữ liệu nhanh hơn.



➡️ Đây là lý do tại sao HTTPS bảo mật hơn HTTP!




