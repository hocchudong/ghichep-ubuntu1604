#Báo cáo về Ubuntu 16.04 64 bit
#Mục lục

* [1. Giới thiệu ](#1)
* [2. Cài đặt](#2)
* [3. Thêm HDD](#3)
* [4. Thêm card mạng, thiết lập ip động, tĩnh.](#4)
* [5. SSH - Cài đặt SSH](#5)
	* [5.1: Giới thiệu về SSH](#5.1)
	* [5.2: Cách thức hoạt động SSH](#5.2)
	* [5.3: Cài đặt SSH](#5.3)

----
<a name="1"></a>
##1. Giới thiệu về Ubuntu 16.04 server
* Ubuntu 16.04 (Xenial Xerus) server vừa phát hành vào ngày 21/4/2016, đây là phiên bản LTS (Long Term Support), và được hỗ trợ từ 
Canonical trong vòng 5 năm, đến tháng 4/2021.
* Ubuntu 16.04 được xây dưng trên Linux Kernels 4.4, phát hành với tháng 1 năm 2016.
* `SSH`: Ubuntu 16.04 mặc định sử dụng OpenSSH 7.2p2 (which disables the SSH version 1 protocol, and disallows the use of DSA (ssh-dss) 
keys).
* `PHP 7`: Ubuntu 16.04's mặc định sử dụng php phiên bản v7.0. 
* `Python`: Ubuntu 16.04 mặc định được cài với Python 3.5.1 và bộ thư viện python3 binary. Nếu bạn muốn sử dụng Python 2, hãy dùng câu 
lệnh dưới dấy
```sh
    sudo apt-get install python
```

----
<a name="2"></a>
##2. Cài đặt
* Các bạn có thể tải về file iso hệ điều hành Ubuntu 16.04 64bit tại đường dẫn 
http://www.ubuntu.com/download/server hoặc http://releases.ubuntu.com/16.04/

* Tiếp theo, các bạn tiến hành cài đặt hệ điều hành Ubuntu lên máy ảo với các bước theo các hình sau:
  * Chọn file iso đã tải về:
  ![](http://i.imgur.com/tzKUHtb.png)
  * Thiết lập mật khẩu, tài khoản:
  ![](http://i.imgur.com/s6502HN.png)
  * Chọn dung lượng và cấu hình ổ đĩa cài hệ điều hành:
  ![](http://i.imgur.com/5jK8UO6.png)
  * Sau khi thực hiện các bước trên thì hệ điều hành sẽ được tự động cài vào máy ảo Vmwware.
  
----
<a name="3"></a>
##3. Thêm hdd
* Chọn máy ảo cần thêm, chọn `Edit virtual machine settings`, tiếp tục chọn `Add` và chọn `Hard Disk`.

![](http://i.imgur.com/KhVXwm4.png)

* Tiếp theo, ta chọn chuẩn ổ đĩa, có 3 loại ổ đĩa là :
![](http://i.imgur.com/mPjWz7j.png)
	* IDE (Integrated Drive Electronics): Tốc độ truyền tải dữ liệu tối đa là 100 MB/giây
	* SCSI (Small Computer System Interface): thực chất là 1 thẻ giao diện dùng để kết nối các thiết bị phần cứng trong và ngoài PC, thường được dùng trong các máy chủ.
	* SATA: Tốc độ truyền tải dữ liệu tối đa lên đến 150 - 300 MB/giây. 

* Tiếp theo, các tùy chọn disk, có 3 tùy chọn là :
![](http://i.imgur.com/Q7JdNnY.png)
	* Create a new virtual disk: Tạo 1 ổ đĩa ảo mới.
	* Use an existing virtual disk: Sử dụng 1 ổ đĩa ảo đã tồn tại.
	* Use a physical disk: Sử dụng ổ đĩa vật lý.
* Tiếp theo, chọn dung lượng disk.
![](http://i.imgur.com/bUE9J7V.png) 
* Cuối cùng, đặt tên file disk và kết thúc.
* Thử kiểm tra xem ổ đĩa có trong linux chưa. Ta dùng lệnh `fdisk -l`
![](http://i.imgur.com/UptSnP3.png)

----
<a name="4"></a>
##4. Thêm card mạng, thiết lập ip động, tĩnh.
* Ta cấu hình theo các bước như trong link dưới đây:
https://github.com/hieppso194/baocao_vnware/blob/master/vnware.md

----
<a name="5"></a>
##5. SSH - Cài đặt SSH
<a name="5.1"></a>
###5.1: Giới thiệu về SSH
* SSH (Secure Shell) là một giao thức mạng dùng để thiết lập kết nối mạng một cách bảo mật.
* SSH hoạt động ở lớp trên trong mô hình phân lớp TCP/IP.
* Mỗi khi dữ liệu được gửi bởi một máy tính vào mạng, SSH tự động mã hoá nó. Khi dữ liệu được nhận vào, SSH tự động giải mã nó.

<a name="5.2"></a>
###5.2: Cách thức hoạt động của SSH
* SSH làm việc thông qua 3 bước đơn giản:
  * **Định danh host**: xác định định danh của hệ thống tham gia phiên làm việc SSH.
  * **Mã hoá**: thiết lập kênh làm việc mã hoá.
  * **Chứng thực**: xác thực người sử dụng có quyền đăng nhập hệ thống.
* Chi tiết từng bước:  
* **Định danh host**:
  Việc định danh host được thực hiện qua việc trao đổi khoá. Mỗi máy tính có hỗ trợ kiểu truyền thông SSH có một khoá định danh duy 
  nhất. Khoá này gồm hai thành phần: khoá riêng và khoá công cộng. Khoá công cộng được sử dụng khi cần trao đổi giữa các máy chủ với 
  nhau trong phiên làm việc SSH, dữ liệu sẽ được mã hoá bằng khoá công khai và chỉ có thể giải mã bằng khoá riêng. Khi có sự thay đổi
  về cấu hình trên máy chủ: thay đổi chương trình SSH, thay đổi cơ bản trong hệ điều hành, khoá định danh cũng sẽ thay đổi. Khi đó mọi 
  người sử dụng SSH để đăng nhập vào máy chủ này đều được cảnh báo về sự thay đổi này. Khi hai hệ thống bắt đầu một phiên làm việc SSH,
  máy chủ sẽ gửi khoá công cộng của nó cho máy khách. Máy khách sinh ra một khoá phiên ngẫu nhiên và mã hoá khoá này bằng khoá công 
  cộng của máy chủ, sau đó gửi lại cho máy chủ. Máy chủ sẽ giải mã khoá phiên này bằng khoá riêng của mình và nhận được khoá phiên. 
  Khoá phiên này sẽ là khoá sử dụng để trao đổi dữ liệu giữa hai máy. Quá trình này được xem như các bước nhận diện máy chủ và máy 
  khách.

* **Mã hoá**:
  Sau khi hoàn tất việc thiết lập phiên làm việc bảo mật (trao đổi khoá, định danh), quá trình trao đổi dữ liệu diễn ra thông qua một 
  bước trung gian đó là mã hoá/giải mã. Điều đó có nghĩa là dữ liệu gửi/nhận trên đường truyền đều được mã hoá và giải mã theo cơ chế 
  đã thoả thuận trước giữa máy chủ và máy khách. Việc lựa chọn cơ chế mã hoá thường do máy khách quyết định. Các cơ chế mã hoá thường 
  được chọn bao gồm: 3DES, IDEA, và Blowfish. Khi cơ chế mã hoá được lựa chọn, máy chủ và máy khách trao đổi khoá mã hoá cho nhau. Việc
  trao đổi này cũng được bảo mật dựa trên đinh danh bí mật của các máy. Kẻ tấn công khó có thể nghe trộm thông tin trao đổi trên đường 
  truyền vì không biết được khoá mã hoá. Các thuật toán mã hoá khác nhau và các ưu, nhược điểm của từng loại:
    * **3DES** (cũng được biết như Triple-DES) -- phương pháp mã hoá mặc định cho SSH.
    * **IDEA**—Nhanh hơn 3DES, nhưng chậm hơn Arcfour và Blowfish.
    * **Arcfour**—Nhanh, nhưng các vấn đề bảo mật đã được phát hiện.
    * **Blowfish**—Nhanh và bảo mật, nhưng các phương pháp mã hoá đang được cải tiến.
    
* **Chứng thực**:
  Việc chứng thực là bước cuối cùng trong ba bước, và là bước đa dạng nhất. Tại thời điểm này, kênh trao đổi bản thân nó đã được bảo 
  mật. Mỗi định danh và truy nhập của người sử dụng có thể được cung cấp theo rất nhiều cách khác nhau. Chẳng hạn, kiểu chứng thực 
  rhosts có thể được sử dụng, nhưng không phải là mặc định; nó đơn giản chỉ kiểm tra định danh của máy khách được liệt kê trong file 
  rhost (theo DNS và địa chỉ IP). Việc chứng thực mật khẩu là một cách rất thông dụng để định danh người sử dụng, nhưng ngoài ra cũng 
  có các cách khác: chứng thực RSA, sử dụng ssh-keygen và ssh-agent để chứng thực các cặp khoá.

<a name="5.3"></a>
###5.3: Cài đặt SSH
* Lệnh cài đặt
```sh
apt-get install -y ssh
```
* Cấu hình file **sshd_config**:
```sh
Port 22	//Đổi port ssh
ListenAddress 0.0.0.0	//Chỉ cho phép đăng nhập SSH từ một IP cố định
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes	//xác thực bằng thuật toán rsa
PubkeyAuthentication yes	//xác thực khóa công khai
AuthorizedKeysFile	%h/.ssh/authorized_keys	//đường dẫn file authorized key (file chứa public-key)

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

PermitEmptyPasswords no	/cho phép mật khẩu trống

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no	//cấu hình xác thực bằng mật khẩu hoặc key

UsePAM yes
AllowUsers user1 user2 user3 user4 user5	//các user truy cập ssh
```
----
