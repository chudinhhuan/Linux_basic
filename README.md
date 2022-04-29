# CƠ BẢN VỀ LINUX 
![image](https://user-images.githubusercontent.com/90398366/165110928-f1a8881b-dba2-4581-a927-7c61adc4a6aa.png)

## A. VỀ CÁC DÒNG LỆNH

### 1. Các dòng lệnh với file system
- pwd ( print name of current ) -> xem vị trí hiện tại
- cd  ( Change directory ) -> đổi vị trí - di chuyển vị trí 
- cd.. -> trở về thư mục cha
- ls ( list directory contents ) -> xem nội dung trong vị trí hiện tại
- ls -l -> liệt kê đội dung chi tiết
- ls -l/ -> liệt kê gốc
- ls -la -> tương tự 
- ls /name_file -> liệt kê thư mục chỉ định

### 2.Thủ thuật gõ lệnh 
- Dùng các mũi tên lên xuống
- ctrl + C -> hủy lệnh
- ctrl + L hoặc clear -> clear màn hình
- ctrl + R -> tìm lại lệnh đã gõ 
- history -> xem lịch sử gõ lệnh 
- sau khi history muồn dùng lệnh đó thì cú pháp : ! num_lệnh 
### 3.Tạo - xóa foder và file
- mkdir name_foder -> tạo foder 
- touch name_file -> tạo file
- ******
- rm -> xóa foder và file
- rm -r name_foder -> xóa foder chọn
- rm -rf foder_name -> xóa all thư mục trong foder đó

### 4. Trình soạn thảo văn bản vi
> Trình soạn thảo vi có 3 chế độ :
- command -> di chuyển, cắt , dán (esc)
- insert -> soạn thảo (i)
- ex -> lưu và thoát văn bản ( shift : )
> Các tập lệnh
- vi name_file -> tạo hoặc mở
- i -> soạn thảo văn bản
- esc -> thoát khỏi chế độ insert
- shift + : -> vào extra
- : + wq -> lưu và thoát khỏi extra
- : + quit! -> chỉ xem không lưu kết quả
- ******
- cat name_file -> xem file
- yy -> copy
- p -> paste
- dd -> delete
- u -> back
- / find_name -> tìm kiếm
> Các thay thế chữ - chỉ thay thế được ký tự in thường
- shift + : -> %s/text_old/text_new/g -> thay thế
- :set nu -> cài đặt hiện số dòng trong file vi
- :set nonu -> bỏ đánh số dòng trong file vi

### 5.Copy , di chuyển và đổi tên file - foder
> cp -> copy
> mv -> move(di chuyển )
>  ***** Cú Pháp *****
>  Copy
- cp file_source / file_dict 
- cp -rv foder_source / foder_dict
> Đổi tên
- mv name_file_old name_file_new  và foder tương tự như vậy
> Di chuyển
- mv file_source /file_dict với foder tương tự như vậy
### 📓 Note tùy vào nếu gõ lệnh bị lỗi thì thử bỏ "/" này đi 
🦫 
### 6. Đọc nội dung file
### 📓 Note tùy vào nếu gõ lệnh bị lỗi thì thử bỏ "/" này đi 
> cat , more ,less(*) ,head ,tail(*) -> * quan trọng
- cat /file_read -> đọc all content file
- more /file_read -> đọc từng đoạn và muốn xem thì bấm spack
- less /file_read -> tùy ý đọc có thể di chuyển lên xuống để đọc và cũng có thể tìm kiếm nữa , muốn thoát thì ấn "q"
- head /file_read -> đọc đoạn đầu
- head -n num_row -> đọc số lượng dòng đầu mong muốn 
- tail /file_read và tail -n num_row -> tương tự như head
- tail -f /file_read -> giúp đọc file log và giúp fix lỗi

### 7.Tìm kiếm file
### 3 cách tìm kiếm:
- theo tên -> name
- theo kích thước -> size
- theo lịch sử bị thay đổi -> ctime
> Ví dụ :
* find / -name name_file
* find /etc -name *.config -> tìm theo đuôi
* find /etc -size 1000k or +1000k or -1000k -> tìm theo kích thước
* find /etc -ctime -2 -> tìm theo thời gian thay đổi 
* find /etc -size +1000k name *.bin -ctime -10 -> kết hợp 3 cachs thức tìm kiếm

### 8.Tạo xóa người dùng
- useradd -> tạo người dùng
- passwd -> tạo mật khẩu
- su -> chuyển đổi người dùng
- userdel -> xóa người dùng
- note :
-  File người dùng và mật khẩu thường được lưu trên:
- /etc/passwd
- /etc/shadow 
> VÍ DỤ
- less/etc/passwd (thông tin)  và less /etc/shadow (mật khẩu )
- useradd nguoidung -> tạo người dùng
- tail -n1 /etc/passwd -> kiểm tra người dùng
- cat / etc/shadow -> check mật khẩu người dùng
- passwd nguoidung -> gõ mật khẩu set 

> Ví dụ chuyển người dùng
- su - nguoidung1 -> chuyển người dùng
- su - root -> chuyển sang người dùng root -> cần password vì root có đặc quyền cao nhất
- exit thoát ra khỏi người dùng
- userdel name_user -> xóa người dùng
### 9.Thay đổi người / nhóm sở hữu file (chown)
>chown 
- 
>Vi du: 
- ls -l abc.txt -> thông tin file
- chown sohuu1 abc.txt -> thay đổi người sở hữu
- chown .name_group abc.txt -> thay đổi nhóm sở hữu
- chown name_Sh.name_group abc.txt -> thay đổi cả người sở hữu và nhóm sở hữu
- chown name_Sh:name_group abc.txt -> thay đổi cả người sở hữu và nhóm sở hữu

### 10.Thay đổi quyền của file  ( chmod)
>Linux có 3 quyền cơ bản ( read -r , write -w ,execute -x
- Có 2 cách là bằng chữ và bằng số 
- Một file được sở hữu bởi 3 đối tượng : user owner - u , group owner - g và Others - o
- Lệnh chmod thay đổi quyền
-  Vidu : chmod u + w abc.txt , chmod g+w abc.txt , chmod o + x abc.txt
> Thay đổi quyền lệnh chmod bằng số
- read =4, write =2 , excute = 1
- VÍ dụ :
> chmod 775 abc.txt
> với user owner có quyền read, write, execute : 4+2+1=7,
> với group owner có read, write, execute : 4+2+1=7,
> với Others : read, Others : 4+1 =5

## 11. Dữ liệu vào/ ra chuẩn lỗi
> Nôm na là như lưu input lỗi và không lỗi vào file chứ không hiển thị ra màn hình
- Chuyển hướng dữ liệu và file
> stdout > file ,
> stderr2 > file ,
> stdout + stderr &> file 
- VD:
> ls > stdin.txt -> chuyển hướng file ko lỗi 
> ls  fileko ton tai 2> stderr.txt 
> xem lại file cat stderr.txt 
> Chuyển hướng cả 2 lỗi và không lỗi vào một file : 
> ls file* afnsafa &> all.txt -> chuyển hướng cả lỗi và ko lỗi vào 1 file

- alsnk,fasdfsadf

