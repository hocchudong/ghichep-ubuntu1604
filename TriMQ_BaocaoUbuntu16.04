#Tìm hiểu về Ubuntu 16.04

##Mục lục:
####[1.Những hiểu biết về Ubuntu 16.04](#hieubiet)
####[2.Cài đặt Ubuntu 16.04](#caidat)
<li>[2.1.Add thêm ổ cứng và cài đặt hệ điều hành](#ocung)</li>
<li>[2.2.Add thêm card mạng và cài đặt ip tĩnh và động cho 2 card](#card)</li>
####[3.Cài đặt ssh để sử dụng putty](#ssh)
<li>[3.1.Giới thiệu công cụ putty](#putty)</li>
<li>[3.2.SSH là gì](#ssh)</li>
<li>[3.3.Sử dụng putty để kết nối vào hệ thống](#ketnoi)</li>

<a name="hieubiet"></a>
####1.Những hiểu biết về Ubuntu 16.04:
- Phiên bản Ubuntu 16.04 (Xenial Xerus) được phát hành vào ngày 21/04/2016
- Là phiên bản *long term support* nghĩa là phiên bản này sẽ được cập nhật cho đến tháng 4 năm 2016, tạo ra 1 nền tảng ổn định cho hệ thống.
- Ubuntu 16.04 được xây dựng trên Linux kernel 4.4, phát hành vào tháng 1 năm 2016.
- Ubuntu 16.04 mặc định sử dụng Openssh 7.2p2, nó sẽ vô hiệu hóa các ssh version 1 và không cho phép việc sử dụng các DSA (ssh-dss).
- Ubuntu 16.04 mặc định sử dụng v7.0. PHP 7,
- Ubuntu 16.04 mặc định sử dung Python 3.5.1, nó được chạy như là python 3, nếu muốn sử dụng python 2 bạn phải sử dụng câu lệnh:
```sh
sudo apt-get install python
```
<a name="caidat"></a>
####2.Cài đặt Ubuntu 16.04:
- Để cài đặt 1 máy ảo chạy hđh Ubuntu 16.04 ta sử dụng phần mềm VMware và dùng file ISO của Ubuntu 16.04-server.

<a name="ocung"></a>
#####2.1:Add thêm ổ cứng và cài đặt hệ điều hành:
<li> Tại mục edit virtual machine settings -> add -> hardware.</li>
<img src="http://i.imgur.com/hcEDxlG.png">

<li> Chọn loại ổ cứng mà ta muốn thêm vào, ở đây ta chọn SCSI</li>
<img src="http://i.imgur.com/8V1YUZC.png">

<li> Chọn dung lượng ổ mà ta mong muốn sau đó lưu lại</li>
<img src="http://i.imgur.com/21N1VCc.png">

<li>Kiểm tra xem máy đã nhận 2 ổ cứng chưa, ta sử dụng lệnh `fdisk`</li>
<img src="http://i.imgur.com/nMHoPGX.png">

- Cài đặt hệ điều hành tương tự như Ubuntu 14.04:
Tham khảo các cài đặt Ubuntu 14.04 tại đây:
*Lưu ý*: Ở đây ta có 2 ổ cứng nên phải chọn 1 ổ cứng để cài đặt hệ điều hành.
<img src="http://i.imgur.com/86wakwU.png">

<a name="card"></a>
#####2.2.Add thêm card mạng cho máy ảo:
- Ở đây ta sẽ có 2 card mạng đó là NAT và Host only
- 1 card sẽ được gán IP tĩnh và 1 card sẽ sử dụng IP động.

<li>Tại mục edit virtual machine settings -> add -> adapter network</li>
<img src="http://i.imgur.com/tSebe0J.png">

<li>Chọn loại card mà ta muốn, ở đây chọn card VMnet 1(hostonly)</li>
<img src="http://i.imgur.com/G3luXbA.png">

- Cài đặt ip tĩnh và động cho 2 card mạng.
Để cấu hình ip ta sử dụng lệnh và sửa file như sau:
```sh
vi /etc/network/interfaces
```
<img src="http://i.imgur.com/2KANIW6.png">

<a name="ssh"></a>
####3.Cài đặt ssh để sử dụng putty:
 Sử dụng lệnh để cài đặt:
 ```sh
 apt-get install openssh-server -y
 ```
 
<a name="putty"></a>
#####3.1.Giới thiệu về công cụ putty:
 Putty là một chương trình truy cập ssh thông dụng dành cho người dùng, Sau khi đăng nhập vào hệ thống, có thể dùng các câu lệnh của Linux, trong chế độ CLI (command line) để quản trị hệ thống.
 
<a name="ssh"></a>
#####3.2.SSH là gì:
 - Là một giao thức mạng dùng để thiết lập kết nối mạng một cách bảo mật. Hoạt động ở lớp trên mô hình TCP/IP.
 - Các công cụ SSH (như là OpenSSH,…) cung cấp cho người dùng cách thức để thiết lập kết nối mạng được mã hoá để tạo một kênh kết nối riêng tư.
 - SSH có cơ chế mã hóa dữ liệu đủ mạnh nhằm bảo mật dữ liệu trên đường truyền.
 - Cách thức hoạt động:
 <ul>
 <li>Định danh host – xác định định danh của hệ thống tham gia phiên làm việc SSH.</li>
 <li>Mã hoá – thiết lập kênh làm việc mã hoá.</li>
 <li>Chứng thực – xác thực người sử dụng có quyền đăng nhập hệ thống.(user|pass)</li>
</ul>

<a name="ketnoi"></a>
#####3.3.Sử dụng putty để kết nối vào hệ thống:
 - Kết nối vào máy chủ thông qua putty, ta cần nhập địa chỉ IP của máy và đăng nhập tài khoản người dùng.
 <img src="http://i.imgur.com/X9OoptF.png">
 - Nếu đăng nhập bằng tài khoản root trên Ubuntu sẽ không đăng nhập được mà ta phải sửa file cấu hình `sshd_config` như sau:
 Ở mục `permit root login` ta chỉnh là thành `yes`
 <img src="http://i.imgur.com/3jD3N8U.png">
 
 
 
 
 
 
 
 
 









