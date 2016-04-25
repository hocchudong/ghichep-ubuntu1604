# Cài đặt Ubuntu server 16.04 và thiết lập ssh cho root
# Mục lục
<h4><a href="#setup">1. Cài đặt Ubuntu server 16.04</a></h4>
<ul>
<li><a href="#requirement">1.1. Yêu cầu</a></li>
<li><a href="#stepbystep">1.2. Các bước cài đặt</a></li>
</ul>
<h4><a href="#configip">2. Cấu hình IP cho 2 card mạng (static và dynamic)</a></h4>
<h4><a href="#configssh">3. Cấu hình SSH cho phép ssh với tài khoản root</a></h4>

---

<h4><a name="setup">1. Cài đặt Ubuntu server 16.04</a></h4>
<ul>
<li><a name="requirement">1.1. Yêu cầu</a>
<ul>
<li>Cài đặt ubuntu 16.04  server 64bit trên VMware</li>
<li>Máy có 2 HDD</li>
<li>HDD1 50GB cài hệ điều hành</li>
<li>HDD2 70GB - không cài gì</li>
<li>Sử dụng 2 NIC: NAT và Hostonly</li>
<li>Thực hành đặt IP động và tĩnh cho các card mạng</li>
<li>Cài ssh để sử dụng putty</li>
</ul>
</li>
<li><a name="stepbystep">1.2. Các bước cài đặt</a>
<ul>
<li>Bật VMware, gõ Ctrl+N tạo máy ảo mới
<br><br>
<img src="http://i.imgur.com/TxKlgeQ.png"/>
<br><br>
</li>
<li>Duyệt tới file iso ubuntu server 14.04
<br><br>
<img src="http://i.imgur.com/nFkypyJ.png"/>
<br><br>
</li>
<li>Đặt tên cho máy ảo và tạo thư mục chứa máy ảo
<br><br>
<img src="http://i.imgur.com/oNnDwCi.png"/>
<br><br>
</li>
<li>Thiết lập ram cho máy ảo, khoảng 1.5 GB -  2GB
<br><br>
<img src="http://i.imgur.com/pM6eXnP.png"/>
<br><br>
</li>
<li>Chọn chế độ kết nối mạng (NAT). Để config 2 card mạng ta cấu hình lại sau.
<br><br>
<img src="http://i.imgur.com/Md39aBT.png"/>
<br><br>
</li>
<li>Tạo ổ đĩa cài hệ điều hành (cỡ 50 GB)
<br><br>
<img src="http://i.imgur.com/bwTooQc.png"/>
<br><br>
</li>
<li>Click Next tới khi chuẩn bị hoàn tất quá trình thiết lập thì cấu hình thêm card mạng mới chế độ Host-only (VMnet2)
<br><br>
<img src="http://i.imgur.com/byNFA4T.png"/>
<br><br>
<br><br>
<img src="http://i.imgur.com/NzyRqjO.png"/>
<br><br>
</li>
<li>Thêm ổ đĩa mới (70 GB)
<br><br>
<img src="http://i.imgur.com/Nn8zVqd.png"/>
<br><br>
<br><br>
<img src="http://i.imgur.com/16qAnZD.png"/>
<br><br>
</li>
<li> Kiểm tra lại lần cuối trước khi cài đặt
<br><br>
<img src="http://i.imgur.com/wXp6mvx.png"/>
<br><br>
</li>
<li>Khởi tạo quá trình cài đặt, chọn ngôn ngữ (English)
<br><br>
<img src="http://i.imgur.com/G51wnIU.png"/>
<br><br>
<br><br>
<img src="http://i.imgur.com/C7YARHB.png"/>
<br><br>
</li>
<li>Chọn vị trí địa lý để thiết lập thời gian cho hệ thống
<br><br>
<img src="http://i.imgur.com/rNd4jwC.png"/>
<br><br>
</li>
<li>Chọn kiểu mã cho ngôn ngữ mặc định cho hệ thống
<br><br>
<img src="http://i.imgur.com/yp24LLg.png"/>
<br><br>
</li>
<li>Thiết lập keyboard layout
<br><br>
<img src="http://i.imgur.com/I85YNSw.png"/>
<br><br>
<img src="http://i.imgur.com/zC2WfWn.png"/>
<br><br>
<img src="http://i.imgur.com/IBSJXla.png"/>
<br><br>
</li>
<li>
Chọn card mạng mặc định 
<br><br>
<img src="http://i.imgur.com/Hvetiwh.png"/>
<br><br>
</li>
<li>Đặt tên host
<br><br>
<img src="http://i.imgur.com/oSOx7MF.png"/>
<br><br>
</li>
<li>Tạo người dùng mới
<br><br>
<img src="http://i.imgur.com/dClrOQw.png"/>
<br><br>
<img src="http://i.imgur.com/tyxwwnd.png"/>
<br><br>
<img src="http://i.imgur.com/1Z8nybj.png"/>
<br><br>
</li>
<li>Chọn không mã hóa thư mục home
<br><br>
<img src="http://i.imgur.com/9zYUp53.png"/>
<br><br>
</li>
<li>Chọn ổ cài hệ điều hành (ổ 50GB)
<br><br>
<img src="http://i.imgur.com/eh9LqCv.png"/>
<br><br>
</li>
<li>
Chia ổ này thành 3 phân vùng (/, /home, swap). Trước hết tạo phân vùng swap cỡ 2GB
<br><br>
<img src="http://i.imgur.com/rc9H74W.png"/>
<br><br>
</li>
<br><br>
<img src="http://i.imgur.com/fPdkWM8.png"/>
<br><br>
<br><br>
<img src="http://i.imgur.com/fqnRvbf.png"/>
<br><br>
<br><br>
<img src="http://i.imgur.com/IRhVdzx.png"/>
<br><br>
<br><br>
<img src="http://i.imgur.com/dCHFVMr.png"/>
<br><br>
<li>Tương tự tạo 2 phân vùng / và /home (phân vùng / chọn làm primary), kết quả như sau:
<br><br>
<img src="http://i.imgur.com/7nJylff.png"/>
<br><br>
</li>
<li>Xác nhận việc chia phân vùng
<br><br>
<img src="http://i.imgur.com/BxiLg1j.png"/>
<br><br>
</li>
<li>Chọn HTTP proxy để kết nối ra mạng ngoài, nếu không có thì enter bỏ qua
<br><br>
<img src="http://i.imgur.com/bIEa4ss.png"/>
<br><br>
</li>
<li>Chọn cách thức cập nhật hệ thống (Install security updates automatically)
<br><br>
<img src="http://i.imgur.com/pxPnIh9.png"/>
<br><br>
</li>
<li>Chọn một số phần mềm cần thiết cài đặt thêm
<br><br>
<img src="http://i.imgur.com/JTd208g.png"/>
<br><br>
</li>
<li>Sau khi cài đặt xong phần mềm, cài đặt grub boot loader
<br><br>
<img src="http://i.imgur.com/Aixjhd7.png"/>
<br><br>
<img src="http://i.imgur.com/eCW7X68.png"/>
<br><br>
</li>
<li>Sau khi hoàn tất, khởi động lại kiểm tra lại các ổ đĩa, gõ lệnh: 
<code>lsblk</code> được kết quả như hình
<br><br>
<img src="http://i.imgur.com/NhgV4Bi.png"/>
<br><br>
</li>
</ul>
</li>
</ul>
<h4><a name= "configip">2. Cấu hình IP cho 2 card mạng (static và dynamic)</a></h4>
<li>Gõ <code>ifconfig</code> kiểm tra các card mạng, lần đầu máy chỉ nhận 1 card (chế độ NAT), tên là ens33
<br><br>
<img src="http://i.imgur.com/ayWK2Oy.png"/>
<br><br>
</li>
<li>Gõ: <code>ip link</code> để hiển thị các card mạng: 
<br><br>
<img src="http://i.imgur.com/J46eN5X.png"/>
<br><br>
</li>
<li>Quan sát thấy card ens34 chưa được khai báo, ta mở file: <code>vi /etc/network/interfaces</code> , rồi add thêm card ens34 chế độ dhcp (cấp phát địa chỉ ip động cho card ens34)
<br><br>
<img src="http://i.imgur.com/2eWYf1H.png"/>
<br><br>
</li>
<li>Lưu lại file <i>interfaces</i> rồi restart lại các card mạng: <code>ifdown -a && ifup -a</code>
<br><br>
<img src="http://i.imgur.com/g6C9q7D.png"/>
<br>
</li>
<li>Cấu hình static cho các card mạng. Mở file: <code>vi /etc/network/interfaces</code> , chỉnh sửa lại như bên dưới. <br>
<pre>
<code>
auto ens33
iface ens33 inet static
address 172.16.69.133/24
gateway 172.16.69.1
dns-nameservers 8.8.8.8

auto ens34
iface ens34 inet static
address 10.10.10.136/24
</code>
</pre>
<br><br>
Gõ <code>ifdown -a && ifup -a</code> để restart lại các card mạng. 
</li>
<h4><a name="configssh">3. Cấu hình SSH cho phép ssh với tài khoản root</a>
</h4>
<div>Trong quá trình cài đặt, do OpenSSH đã cài nên có thể tiến hành cấu hình ngay. Nhưng trong trường hợp chưa cài, ta thực hiện cài đặt ssh sử dụng lệnh:
<br>
<code>sudo apt-get install ssh</code>
<br>
</div>
<div>Tiến hành cấu hình cho phép ssh với tài khoản root:
<ul>
<li>Trước hết chuyển qua tài khoản root và đặt mật khẩu mới (nếu tài khoản root chưa đặt mật khẩu): 
<pre>
<code>
# chuyen qua tai khoan root
sudo -i 
# dat mat khau moi
passwd
# tien hanh nhap va xac nhan mat khau moi
</code>
</pre>
</li>
<li>
Tiếp đó, mở file cấu hình ssh lên:
<br>
<pre>
<code>
vi /etc/ssh/sshd_config
</code>
</pre>
</li>
<li>Tìm tới dòng 28,  chỉnh sửa lại như sau:
<br>
<pre>
<code>
PermitRootLogin yes
</code>
</pre>
<br><br>
<img src="http://i.imgur.com/6rN66rD.png"/>
<br><br>
</li>
<li>Lưu lại file rồi quay ra hệ điều hành chủ, dùng một ssh client (Super Putty hoặc Moba Xterm, ở đây dùng Moba Xterm), tiến hành ssh vào máy ảo ubuntu với tài khoản root, địa chỉ là 10.10.10.136 (địa chỉ card ens34)
<br>
<pre>
<code>ssh root@10.10.10.136</code>
</pre>
<br>
Nhập mật khẩu xác nhận, ta được kết quả như sau
<br><br>
<img src="http://i.imgur.com/MkkSAwv.png"/>
<br><br>
</li>
</ul>
</div>