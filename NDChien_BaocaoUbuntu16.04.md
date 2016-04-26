#Cài đặt Ubuntu Server 16.04
====================
**Mục Lục:**

[1. Ubuntu Server 16.04](#1)

[2. Cài đặt](#2)

[3. Cài thêm card mạng và ổ cứng cho máy ảo](#3)

- [3.1 Thêm card mạng, ổ cứng](#3.1)

- [3.2 Đặt địa chỉ IP cho card mạng](#3.2)

[4. Triển khai ssh](#4)

===================

<a name="1"></a>
###1. Ubuntu Server 16.04
- Ubuntu 16.04 (Xenial Xerus) server vừa phát hành vào ngày 21/4/2016, được hỗ trợ từ Canonical trong vòng 5 năm, đến tháng 4/2021.
- Ubuntu 16.04 được xây dưng trên Linux Kernels 4.4, phát hành với tháng 1 năm 2016.
- Ubuntu 16.04 sử dụng OpenSSH 7.2p2, xóa bỏ giao thức SSH 1 và không cho phép dùng DSA (ssh-dss) keys
- Ubuntu 16.04's sử dụng PHP phiên bản v7.0.
- Ubuntu 16.04 mặc định được cài với Python 3.5.1 và bộ thư viện python3 binary. Nếu bạn muốn sử dụng Python 2, hãy dùng câu lệnh dưới đây

`sudo apt-get install python`

- Hỗ trợ cho phần cứng mới của Intel và AMD.
Improved Intel Skylake processor support
3D support in the virtual GPU driver
New driver for Corsair Vengeance K90
Support for TPM 2.0 chips
Journaled RAID 5 support
- Cập nhật lên Tomcat (v8), Postgresql (v9.5), Docker v(1.10), Puppet (v3.8.5), Qemu (v2.5), Libvirt (v1.3.1), LXC (v2.0), and MySQL (v5.6)

<a name="2"></a>
###2. Cài đặt
Link tải các phiên bản Ubuntu http://www.ubuntu.com/download

Các phần mềm: 

- VMwork Station
- File iso Ubuntu Server 16.04 
- putty
  
**Chuẩn bị máy ảo cài đặt và khởi động máy**
<img src=http://i.imgur.com/rqTCRYL.png>

**Chọn ngôn ngữ**

<img src=http://i.imgur.com/IygpuRJ.png>

**Chọn khu vực**
<img src=http://i.imgur.com/urKV2M2.png>

**Cài đặt bàn phím**

<img src=http://i.imgur.com/sdrONuE.png>

**Đặt tên hiển thị cho server**
<img src=http://i.imgur.com/9NWWaYn.png>

**Đặt tên đầy đủ cho user**
<img src=http://i.imgur.com/T74aXXK.png>

**Đặt username**

<img src=http://i.imgur.com/xY2AOhf.png>

**Đặt mật khẩu cho username ở trên**
<img src=http://i.imgur.com/xY2AOhf.png>

**Mã hóa thư mục /home**
<img src=http://i.imgur.com/7OxwLOn.png>

**Cấu hình múi giờ**

<img src=http://i.imgur.com/oxZrbS0.png>

**Phân vùng ổ cứng cho ubuntu**

<img src=http://i.imgur.com/sI8gbqc.png>

`Guided - use entire disk: Tự động phân vùng`

`Guided - use entire disk and with set up LVM: Tự động phân vùng với LVM`

`Guided - use entire disk and with set encrypted up LVM: Tự động phân vùng và mã hóa LVM`

`Manual: Phân vùng bằng tay`

**Cấu hình http proxy**
<img src=http://i.imgur.com/LvgkV46.png>

**Tùy chọn cập nhật các gói**
<img src=http://i.imgur.com/IF6vfMm.png>

**Chọn các gói phần mềm sẽ được cài đặt cùng với ubuntu**
<img src=http://i.imgur.com/ypK1Hpy.png>
 
**Cài đặt boot loader (GRUB) trên ổ đĩa**
 <img src=http://i.imgur.com/X46nrXV.png>
 
**Nhận continues để khởi động lại máy**
<img src=http://i.imgur.com/WdV47DK.png>

**Giao diện**

<img src=http://i.imgur.com/whTS2UM.png>

<a name="3"></a>
###3. Cài thêm card mạng và ổ cứng cho máy ảo

<a name="3.1"></a>
**3.1 Thêm card mạng, ổ cứng**

Tắt máy và làm theo các bước để ad thêm card mạng và ổ cứng

<img src=http://i.imgur.com/QtjRfho.png>

Chọn chế độ mạng cho card mạng

<img src=http://i.imgur.com/JsEfZBa.png>

Chọn chế độ cho ổ cứng 
- IDE (Integrated Drive Electronics): Tốc độ truyền tải dữ liệu tối đa là 100 MB/giây
- SCSI (Small Computer System Interface): thực chất là 1 thẻ giao diện dùng để kết nối các thiết bị phần cứng trong và ngoài PC, thường được dùng trong các máy chủ.
- SATA: Tốc độ truyền tải dữ liệu tối đa lên đến 150 - 300 MB/giây.

<img src=http://i.imgur.com/Ou9Bu6R.png>

Chọn dung lượng cho ổ

<img src=http://i.imgur.com/eoyMqUY.png>

Kiểm tra các thành phần đã thêm và khởi động máy
  
<img src=http://i.imgur.com/4bx46QJ.png>

Đăng nhập và kiểm tra ổ đĩa với lệnh  `fdisk -l`

<img src=http://i.imgur.com/khefmLP.png>

<a name="3.2"></a>
**3.2 Đặt địa chỉ IP cho card mạng**

Chuyển sang root để cài đặt mạng

<img src=http://i.imgur.com/2Ch5uHm.png>

Dùng lệnh `ifconfig -a | grep ens` để kiểm tra có bao nhiêu card mạng và tên card

<img src=http://i.imgur.com/LFKzSWJ.png?1>

Ta có 2 card mạng ens33 và ens 38
Card ens33 đã được đặt IP

Vào file cấu hình card mạng 
`vi /etc/network/interfaces`

Ta có card ens33 đã đặt IP động
Ta sẽ đặt IP tĩnh cho ens38

<img src=http://i.imgur.com/PYz2L2S.png?1>

Kiểm tra địa chỉ 

<img src=http://i.imgur.com/L6sdI5B.png?1>

<a name="4"></a>
###4. Triển khai ssh

Ta đã chọn cài dịch vụ ssh ở trên.

Truy cập file cấu hình:

` vi /etc/ssh/sshd_config`

- port truy cập là 22
- Đổi PermitRootLogin thành yes để cho phép ssh với user root

<img src=http://i.imgur.com/vTV0qBB.png?1>

<img src=http://i.imgur.com/FbjjcSD.png?1>

Tham khảo:

[1]- https://www.digitalocean.com/community/tutorials/what-s-new-in-ubuntu-16-04

[2]- http://www.ubuntu.com/server
