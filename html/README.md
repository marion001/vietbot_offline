# UI_VietBot

#Vũ Tuyển

#Hướng Dẫn Cài VietBot: https://github.com/phanmemkhoinghiep/vietbot_offline
////////////////////////////////////////////////////////////////////////////////////////////////////////////////

B1:Tạo Mật Khẩu Cho Người Dùng root.

	$: sudo passwd
 
	- Nhập Mật Khẩu root mới vào rồi nhấn enter, nhập lại tiếp mật khẩu rồi nhấn tiếp enter (1 lần check lặp lại mật khẩu)

B2:Mở quyền truy cập ssh cho user root

	$: sudo echo 'PermitRootLogin=yes'  | sudo tee -a /etc/ssh/sshd_config
	$: sudo systemctl restart sshd 

B3:Đăng Nhập ssh bằng quyền Root để chạy các lệnh bên dưới

	(Bước 1,2,3 sẽ không cần thực hiện nếu bạn tải về UI từ command của ssh và coppy sang thư mục html)
//////////////////////////////////////////////////////////////////////////////////////////////////////////////


Chạy các lệnh sau để cài Apache, php, thư viện ssh:

	$: sudo apt-get update
	$: sudo apt-get upgrade
	$: sudo apt install apache2 -y
	$: sudo apt install php -y

- Cài thư viện ssh2 cho php bằng lệnh dưới (hoặc bỏ 6 phút ngồi xem hướng dẫn cài: https://www.youtube.com/watch?v=ZFgd2CjUtko)

	  $: sudo apt-get install libssh2-1 -y

	  $: sudo apt-get install php-ssh2 -y
	
TIẾN HÀNH THỰC HIỆN Cài UI
	
B1: Sao Lưu Lại toàn Bộ File Trong Thư Mục html của bạn lại nhé

B2: Xóa Toàn Bộ File Trong Thư Mục html Của Bạn

B3: Tải về -> Giải Nén -> Upload hết tất cả các file và thư mục VỪA GIẢI NÉN 
vào trong thư mục "html" theo đường dẫn: "var/www/html" của bạn trên ssh

	- Bắt Buộc Phải Chạy 2 Lệnh Này bằng quyền sudo: Lệnh Sét Quyền 777 Các  File Và Thư Mục Con
	$: sudo chmod -R 0777 /var/www/html/
	$: sudo chmod -R 0777 /home/pi/vietbot_offline/src/
	
	- BẮT BUỘC: 
		- Cấu Hình Bắt Buộc Nhập "$SSH_TaiKhoan" và "$SSH_MatKhau" trong file:
			Configuration.php để dùng được các lệnh hệ thống /var/www/html/Configuration.php

B5: Cấu Hình Chỉnh Một Vài Tùy Chọn Khác Theo Ý Bạn Trong File Configuration.php

	- Các File Backup Config sẽ nằm trong: var/www/html/include_php/Backup_Config
