# Các ghi chép về Ubuntu16.04
Bản dịch bài: "What's New in Ubuntu 16.04"

Link gốc: https://www.digitalocean.com/community/tutorials/what-s-new-in-ubuntu-16-04
- - - 
Những điểm mới của Ubuntu 16.4
##I.	Giới thiệu
Phiên bản hỗ trợ dài hạn (Long Term Support-LTS) mới nhất của Hệ điều hành Ubuntu, phiên bản 16.04 (Xenial Xerus) được ra mắt vào ngày 21 tháng 4 năm 2016.

Bản hướng dẫn này dự định sẽ được xem như là một cái nhìn tổng quan về các tính năng mới cũng như những thay đổi đáng kể của hệ thống nói chung từ phiên bản LTS 14.04, từ quan điểm của quản trị viên hệ thống. Nó giới thiệu các ghi chú cập nhật của Xenial Xerus phiên bản chính thức, cùng với một số nguồn khác.
##II.	Phiên bản hỗ trợ dài hạn (LTS) là gì?
Trong khi các phiên bản mới của Ubuntu Desktop và Server xuất hiện đều đặn sáu tháng một lần, các phiên bản LTS lại được ra mắt mỗi hai năm, và được đảm bảo hỗ trợ từ Canonical trong vòng năm năm kể từ khi phát hành. Điều này có nghĩ rằng LTS đã tạo thành một nền tảng ổn định cho việc triển khai các hệ thống sản xuất, và nhận được các cập nhật bảo mật cũng như cách khắc phục các lỗi quan trọng trong một khoảng thời gian đáng kể. Phiên bản 16.04 sẽ tiếp tục được cập nhật cho đến tháng 4 năm 2021.

Bạn có thể tìm đọc bài phân tích chi tiết về chu kỳ phát hành của Ubuntu LTS trên Ubuntu Wiki.
##III.	Hệ thống Init systemd
Người dùng Ubuntu 15.10 hoặc Debian Jessie có thể đã quen thuộc với systemd, hiện là hệ thống khởi tạo mặc định cho phần lớn các chính bản phân phối GNU/Linux. Trên Ubuntu, systemd thay thế cho Upstart của Canonical.

Nếu bạn sử dụng các tập lệnh khởi tạo tùy chỉnh, hoặc thường xuyên thực hiện cấu hình các dịch vụ lâu dài, bạn sẽ cần phải biết những điều cơ bản về systemd. Để có một cái nhìn tổng quan, bạn có thể tìm đọc Systemd Essentials: Working with Services, Units, and the Journal (Systemd Căn bản: Làm việc cùng các dịch vụ, hệ thống và báo cáo)
##IV.	Kerel.
Ubuntu phiên bản 16.04 được xây dựng trên nền tảng loạt 4.4 của Linux Kernels, ra mắt vào tháng 1 năm 2016. 

Trên DigitalOcean, phiên bản Droplets 16.04 mới và Droplets được nâng cấp từ 15.10 sẽ có thể tự quản lý và nâng cấp các hạt nhân (kernel) của riêng mình. Điều này không có trong phiên bản Droplets được nâng cấp từ Ubuntu 14.04 LTS.
##V.	SSH
Phiên bản Ubuntu 16.04 mặc định sử dụng OpenSSH 7.2p2, công cụ này sẽ vô hiệu hóa giao thức SSH phiên bản 1, và không cho phép sử dụng các khóa DSA (ssh-dss). Nếu bạn đang sử dụng một khóa cũ hơn hoặc được yêu cầu phải giao tiếp với một máy chủ SSH được kế thừa từ hệ thống của bạn, bạn nên đọc các bản ghi chú cập nhật về SSH. Mặc dù tương đối ít khóa DSA vẫn đang được sử dụng, cũng có một số khả năng là bạn có thể cần phải tạo ra các khóa mới trước khi thực hiện nâng cấp hoặc vô hiệu hóa xác nhận SSH dựa trên mật khẩu trên máy chủ Ubuntu 16.04 mới.

Để có một cái nhìn tổng quan về việc khởi tạo và sử dụng các khóa SSH mới, hãy tìm đọc How To Configure SSH Key-Based Authentication on a Linux Server (Làm thế nào để thiết lập cấu hình xác nhận trên cơ sở khóa SSH trên một máy chủ Linux).
##VI.	Packaging, Software Distribution, và Container
###Apt
Về bản chất, Ubuntu vẫn được xây dựng trên nền tảng dự án Debian, và được mở rộng trên các tập tin .deb được quản lý bởi Apt, Công cụ Quản lý gói phần mềm.

Ccác công cụ Apt không thay đổi quá nhiều, mặc dù Ubuntu phiên bản 16.04 nâng cấp lên Apt 1.2, bao gồm một số cải tiến về bảo mật. Người dùng chuyển từ các phiên bản cũ hơn có thể cũng sẽ muốn cân nhắc việc sử dụng lệnh apt thay cho các lệnh apt-get and apt-cache truyền thống cho nhiều hoạt động quản lý gói phần mềm. Bạn có thể tìm hiểu thêm chi tiết về lệnh apt trong Package Management Basics: apt, yum, dnf, pkg (Căn bản Quản lý Gói phần mềm: apt, yum, dnf, pkg.)
##VII.	Gói phần mềm Snap
Mặc dù hầu hết người dùng Ubuntu trong các môi trường máy chủ sẽ tiếp tục sử dụng Apt để quản lý gói phần mềm của mình, phiên bản 16.04 cung cấp quyền truy cập vào loại gói phần mềm mới gọi là SNAP, gói phần mềm xuất hiện từ những nỗ lực phát triển Ubuntu phiên bản điện thoại và Internet of Things (IoT). Mặc dù snap dường như không phải là một nhân tố chính để triển khai máy chủ trong chu kỳ của phiên bản 16.04, Canonical đã nhiều lần tuyên bố rằng snaps đại diện cho tương lai gói phần mềm Ubuntu, do đó chúng có khả năng sẽ là một sự phát triển đáng theo đuổi.
##VIII.	LXD
LXD là “một máy ảo hệ điều hành” (container hypervisor), được xây dựng quanh LXC – một giao diện cho tính năng ngăn chặn của hạt nhân Linux (Linux kernel). Bạn có thể tìm đọc phần giới thiệu về LXC và hướng dẫn để bắt đầuLXD trên linuxcontainers.org.
##IX.	ZFS
Ubuntu phiên bản 16.04 bao gồm một mô-đun hạt nhân riêng dành cho ZFS, một hệ thống tập tin tiên tiến được xây dựng từ những năm 2000 tại Sun Microsystems, và hiện đang được phát triển cho các Hệ thống mã nguồn mở (Open Source) trong khuôn khổ dự án OpenZFS. ZFS kết hợp các vai trò truyền thống của một công cụ quản lý hệ thống tệp tin và khối lượng và cung cấp nhiều tính năng hấp dẫn.

Có nhiều tranh cãi xung quanh quyết định phân phối ZFS, kéo theo chỉ trích về các vấn đề cấp phép từ Hiệp hội Bảo vệ Phần mềm và Phần mềm Miễn phí. Tuy nhiên, ZFS là một công nghệ đầy hứa hẹn với một lịch sử phát triển lâu dài – một điểm cân nhắc đặc biệt quan trọng cho các hệ thống tập tin luôn đòi hỏi nhiều năm làm việc trước khi được coi là đủ hoàn thiện cho mục đích sản xuất trên diện rộng. Các quản trị viên hệ thống có thể sẽ muốn theo dõi việc ứng dụng nó trong hệ sinh thái Linux, cả từ góc độ kỹ thuật và pháp lý. 
Bạn có thể tìm đọc thêm về ZFS trên Ubuntu trên trang Ubuntu wiki.
## X.	Ngôn ngữ, Thời gian thi hành và các Công cụ phát triển.
###Go 1.6
Go 1.6 đươc ra mắt vào đầu năm nay, và được bao gồm trong gói Ubuntu phiên bản 16.04.
###PHP 7
Hiện nay, các gói PHP của Ubuntu phiên bản 16.04, được mặc định là v7.0. PHP 7, mang lại các cải tiến hiệu suất lớn hơn các phiên bản trước đó của nó, cùng với các tính năng mới như khai báo kiểu vô hướng cho các thông số chức năng và các giá trị trả về. Nó cũng từ chối một số tính năng kế thừa và loại bỏ một số thành phần mở rộng. Nếu bạn đang triển khai hoặc phát triển phần mềm PHP5, có thể bạn sẽ cần phải thay đổi code hoặc nâng cấp lên các phiên bản mới hơn trước khi di chuyển ứng dụng của mình.
Xem thêm “Getting Ready for PHP 7” (Nhập môn PHPn7) và hướng dẫn chính thức về cách thức di chuyển PHP để biết về danh sách cụ thể các thay đổi.
###Python 3.5
Ubuntu phiên bản 16.04 mặc định đi kèm Python 3.5.1 được cài đặt như là python3 nhị nhân. Python 2 vẫn có thể cài đặt bằng cách sử dụng gói lệnh python:

`sudo apt-get install python`

Đối với những mã hiện có mà vẫn chưa được chuyển tiếp thì đây có thể là gói lệnh cần thiết.
Người dùng của bộ soạn thảo Vim nên lưu ý rằng cấu trúc mặc định của Vim hiện sử dụng phiên bản Python 3, điều này có thể phá vỡ các plugin dựa trên nền tảng Python2.
##KẾT LUẬN
Mặc dù hướng dẫn này chưa đầy đủ, nó có thể mang lại cho người dùng một ý niệm chung về những thay đổi chính và những tính năng mới của Ubuntu phiên bản 16.04.
Cách an toàn nhất để chuyển đổi sang một phiên bản mới thường là cài đặt lại từ đầu phiên bản, cấu hình các dịch vụ đồng thời cẩn thận kiểm tra trong quá trình cài đặt, và di chuyển ứng dụng hoặc dữ liệu người dùng trong một bước riêng biệt. Đối với một số cấu hình phố biển, người dùng có thể sẽ muốn đọc thêm một số tài liệu sau:
 - Initial Server Setup with Ubuntu 16.04 (Cài đặt máy chủ với Ubuntu 16.04)
 - How to Add and Delete Users on Ubuntu 16.04 (Cách thêm và xóa người dùng trên Ubuntu 16.04)
 - How To Install Linux, Apache, MySQL, PHP (LAMP) stack on Ubuntu 16.04 (Cách cài đặt nhóm Linux, Apache, MySQL, PHP (LAMP)  trên Ubuntu 16.04)
 - How to Install Nginx on Ubuntu 16.04 (Cách cài đặt Nginx trên Ubuntu 16.04)
 - How to Install Linux, Nginx, MySQL, PHP (LAMP stack) in Ubuntu 16.04 ( Cách cài đặt Linux, Nginx, MySQL, PHP (LAMP stack) trên Ubuntu 16.04

Người dùng cũng có thể tìm đọc “How to Upgrade to Ubuntu 16.04 LTS” (Cách nâng cấp Ubuntu 16.04 LTS) để biết thêm chi tiết về quá trình nâng cấp một hệ thống hiện có.
