# BT1. Phát triển ứng dụng trên nền web

TẠO SOLUTION GỒM CÁC PROJECT SAU:
1. DLL đa năng, keyword: c# window library -> Class Library (.NET Framework) bắt buộc sử dụng .NET Framework 2.0: giải bài toán bất kỳ, độc lạ càng tốt, phải có dấu ấn cá nhân trong kết quả, biên dịch ra DLL. DLL độc lập vì nó ko nhập, ko xuất, nó nhận input truyền vào thuộc tính của nó, và trả về dữ liệu thông qua thuộc tính khác, hoặc thông qua giá trị trả về của hàm. Nó độc lập thì sẽ sử dụng được trên app dạng console (giao diện dòng lệnh - đen sì), cũng sử dụng được trên app desktop (dạng cửa sổ), và cũng sử dụng được trên web form (web chạy qua iis).
2. Console app, bắt buộc sử dụng .NET Framework 2.0, sử dụng được DLL trên: nhập được input, gọi DLL, hiển thị kết quả, phải có dấu án cá nhân. keyword: c# window Console => Console App (.NET Framework), biên dịch ra EXE
3. Windows Form Application, bắt buộc sử dụng .NET Framework 2.0**, sử dụng được DLL đa năng trên, kéo các control vào để có thể lấy đc input, gọi DLL truyền input để lấy đc kq, hiển thị kq ra window form, phải có dấu án cá nhân; keyword: c# window Desktop => Windows Form Application (.NET Framework), biên dịch ra EXE
4. Web đơn giản, bắt buộc sử dụng .NET Framework 2.0, sử dụng web server là IIS, dùng file hosts để tự tạo domain, gắn domain này vào iis, file index.html có sử dụng html css js để xây dựng giao diện nhập được các input cho bài toán, dùng mã js để tiền xử lý dữ liệu, js để gửi lên backend. backend là api.aspx, trong code của api.aspx.cs thì lấy được các input mà js gửi lên, rồi sử dụng được DLL đa năng trên. kết quả gửi lại json cho client, js phía client sẽ nhận được json này hậu xử lý để thay đổi giao diện theo dữ liệu nhận dược, phải có dấu án cá nhân. keyword: c# window web => ASP.NET Web Application (.NET Framework) + tham khảo link chatgpt thầy gửi. project web này biên dịch ra DLL, phải kết hợp với IIS mới chạy được.

# Bài Làm.
## Giới thiệu đề tài 
Đề tài của em thiên về giải trí  có tên là an ủi những người cô đơn.

1. Mục đích:
   
Trang web được thiết kế để an ủi, chia sẻ và cũng như làm vui lòng người dùng khi họ đang cảm thấy cô đơn hoặc tâm trạng không tốt. Người dùng nhập tên và tâm trạng hiện tại, hệ thống sẽ gửi lại lời nhắn nhẹ nhàng, động viên.

2. Giao diện:

Giao diện đơn giản, dễ sử dụng.

Có hai ô nhập: “Tên của bạn” và “Cảm xúc hiện tại”.

Nút Gửi để gửi thông tin lên server.

Kết quả sẽ hiển thị ngay dưới nút, trong một ô riêng biệt, giúp người dùng nhìn thấy phản hồi ngay lập tức.

3. Công nghệ sử dụng:

Front-end: HTML, CSS, JavaScript (Ajax với fetch)

Back-end: ASP.NET WebForms (C#)

Dữ liệu người dùng được gửi lên server qua POST request, server trả về JSON.

Không cần reload trang để nhận kết quả, trải nghiệm mượt mà.

4. Cách hoạt động:

Người dùng nhập tên và tâm trạng.

Nhấn nút Gửi, JavaScript gửi thông tin lên api.aspx.

Server C# nhận dữ liệu, tạo thông điệp an ủi.

Server trả về JSON chứa thông điệp.

JS nhận JSON và hiển thị vào ô kết quả.

5. Tính năng nổi bật:

Phản hồi ngay lập tức, không cần load lại trang.

Có thể mở rộng thêm các tính năng như: icon cảm xúc, màu sắc thay đổi theo tâm trạng, lưu lịch sử, hoặc gửi email động viên.

#### Tạo Solution trống

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a57c9bf5-1818-470f-bea6-ce70aaa60ae5" />

#### Đặt tên là lonelyComfortSolution.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8306095f-d362-49fe-8492-b1be261639d4" />

#### Thêm Project

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/516afda6-dc57-4106-a627-7125ab796f76" />

#### Thêm Project Class Library (DLL)

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/d1019531-97cd-4d76-a367-ba9d43db45f1" />

#### Đặt tên: ComfortLib

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2e00f8e3-d20e-402c-b567-617b348256f3" />

#### Thêm Project Console App

<img width="1906" height="1080" alt="image" src="https://github.com/user-attachments/assets/aa354459-c189-46c8-b409-2cc051ac8f92" />

#### Console Application tích hợp vào 1 solution

<img width="1915" height="1074" alt="image" src="https://github.com/user-attachments/assets/bfa96dcb-03ea-41dd-8c98-d147db68a5e0" />

#### Tạo project Windows Form App

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c690db94-9034-4740-a9ae-f323825d29e8" />

#### Tạo Web Project

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ad86cd12-6125-48ca-861d-b9fa546b0906" />

#### Trang Web cơ bản khi hoàn thành dành cho người cô đơn ^^

<img width="1534" height="755" alt="image" src="https://github.com/user-attachments/assets/9a7522e5-5b68-4403-b484-4ab7d351e5f6" />



