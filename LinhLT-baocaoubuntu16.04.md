#Báo cáo về Ubuntu 16.04 64 bit
#Mục lục
* [1. Cài đặt](#cai_dat)
* [2. Thêm HDD](#them_hdd)
* [3. Thêm card mạng, thiết lập ip động, tĩnh.](#card_mang)
	* [3.1 Thêm card mạng trong vmware](#them_card_mang)
	* [3.2 Thiết lập ip động - tĩnh](#thiet_lap_ip)
* [4. SSH - Cài đặt SSH](#ssh)
	* [4.1: Giới thiệu về SSH](#gioi_thieu_ssh)
	* [4.2: Cài đặt SSH](#cai_dat_ssh)

<a href="cai_dat"></a>
##1. Cài đặt
* Các bạn có thể tải về file iso hệ điều hành Ubuntu 16.04 64bit tại đường dẫn 
http://www.ubuntu.com/download/server

* Tiếp theo, các bạn tiến hành cài đặt hệ điều hành Ubuntu lên máy ảo với các bước tương tự ở đây
https://github.com/lethanhlinh247/thuctap_vnpt_cloud/blob/master/install_ubuntu_server.md

<a href="them_hdd"></a>
##2. Thêm hdd
* Chọn máy ảo cần thêm, chọn `Edit virtual machine settings`, tiếp tục chọn `Add` và chọn `Hard Disk`.

![](http://i.imgur.com/E0C2wy1.png)

* Tiếp theo, ta chọn chuẩn ổ đĩa:
	* IDE
	* SCSI
	* SATA
* Tiếp theo, các tùy chọn disk:
	* Create a new virtual disk: Tạo 1 ổ đĩa ảo mới.
	* Use an existing virtual disk: Sử dụng 1 ổ đĩa ảo đã tồn tại.
	* Use a physical disk: Sử dụng ổ đĩa vật lý.

![](http://i.imgur.com/TVtMveI.png)

* Tiếp theo, chọn dung lượng disk.

![](http://i.imgur.com/mjYx421.png) 

* Cuối cùng, đặt tên file disk và kết thúc.

* Thử kiểm tra xem ổ đĩa có trong linux chưa. Ta dùng lệnh `fdisk -l`

Kết quả:

![](http://i.imgur.com/a4QJjMB.png)

<a href="card_mang"></a>
##3. Thêm card mạng, thiết lập ip động, tĩnh.

<a href="them_card_mang"></a>
###3.1 Thêm card mạng trong vmware

* Chi tiết về card mạng trong vmware bạn có thể đọc ở đây: 
https://github.com/lethanhlinh247/thuctap_vnpt_cloud/blob/master/vmware_network.md


<a href="thiet_lap_ip"></a>
###3.2 Thiết lập ip động - tĩnh: Sửa file interfaces: `/etc/network/interfaces`

* Thiết lập ip động
```sh
# The primary network interface
auto ens33
iface ens33 inet dhcp
```
* => Trong đó:
	* ens33: là tên card mạng. 
	* dhcp: từ khóa đặt ip động

* Thiết lập IP Tĩnh
```sh
#The second network interface
auto ens38
iface ens38 inet static
address 10.10.10.100
netmask 255.255.255.0
```
* => Trong đó:
	* ens38 là tên card mạng
	* static: từ khóa, đặt ip tĩnh.
	* address: địa chỉ ip.
	* netmask: địa chỉ netmask.
	* Ngoài ra còn một số thông tin như: network, gateway, dns-nameserver,...

* Ví dụ:

![](http://i.imgur.com/nZtLMlw.png)

* Kết quả

![](http://i.imgur.com/8lUOB6H.png)


<a href="ssh"></a>
##4. SSH - Cài đặt SSH

<a href="gioi_thieu_ssh"></a>
###4.1: Giới thiệu về SSH
* SSH (Secure Shell) là một giao thức mạng dùng để thiết lập kết nối mạng một cách bảo mật.
* SSH hoạt động ở lớp trên trong mô hình phân lớp TCP/IP.
* Mỗi khi dữ liệu được gửi bởi một máy tính vào mạng, SSH tự động mã hoá nó. Khi dữ liệu được nhận vào, SSH tự động giải mã nó.

* Kết quả là việc mã hoá được thực hiện trong suốt: người dùng có thể làm việc bình thường, không biết rằng việc truyền thông của họ đã được mã hoá an toàn trên mạng.

* Chi tiết về giao thức SSH các bạn có thể xem ở đây: https://github.com/cosy294/ksec-training/blob/master/ssh%20-%20ssh%20server%20on%20ubuntu.md

<a href="cai_dat_ssh"></a>
###4.2: Cài đặt SSH
* Lệnh cài đặt
```sh
apt-get install -y ssh
```
* 
Các tập tin cấu hình của ssh đều nằm trong thư mục **/etc/ssh** .

Các file trong thư mục này là:

| Tên File | Chức năng |
|:--------:|:---------:|
| moduli | Chứa một nhóm Diffie-Hellman được sử dụng cho việc trao đổi khóa Diffie-Hellman, nó thực sự quan trọng để xây dựng một lớp bảo mật ở tầng vận chuyển dữ liệu.Khi các khóa được trao đổi với nhau bắt đấu ở một phiên kết nối SSH, một share secret value được tạo ra và không thể xác định bởi một trong hai bên kết nối, giá trị này sau đó sẽ được dùng để cung cấp chứng thực cho host.|
| ssh_config |  file cấu hình mặc định cho SSH client của hệ thống.|
| sshd_config |  File cấu hình cho sshd deamon.|
| ssh_host_dsa_key |  DSA private key được sử dụng với sshd deamon.|
| ssh_host_dsa_key.pub |  DSA public key được sử dụng bởi sshd deamon.|
| ssh_host_key |  RSA private key được sử dụng bởi sshd deamon cho phiên bản 1 của giao thức SSH.|
| ssh_host_key.pub |  RSA public key được sử dụng bởi sshd deamon cho phiên bản 1 của giao thức SSH.|
| ssh_host_rsa_key |  RSA private key được sử dụng bởi sshd deamon cho phiên bản 2 của giao thức SSH.|
| ssh_host_rsa_key.pub |  RSA public key được sử dụng bởi sshd deamon cho phiên bản 2 của giao thức SSH.|
| ssh_host_ecdsa_key | ECDSA private key.|
| ssh_host_ecdsa_key.pub | ECDSA public key.|



Cấu hình file **sshd_config**: Có chú thích trong nội dung file
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

* Kết quả

![](http://i.imgur.com/u28mlQ3.png)