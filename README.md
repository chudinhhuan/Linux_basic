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

## 12. Lệnh đường ống  ( echo ) -pipe command 
> cho phép kết hợp nhiều lệnh với nhau -> thao tác và xử lý dữ liệu linh hoạt
- command1 | command2|....command n
- vd : echo "foo bar baz" | wc -w 


## 13. Thao tác dữ liệu bằng grep và cut
- grep -> lọc dữ liệu theo dòng
- cut -> lọc dữ liệu theo cột

- vd : grep dinhhuan /etc/paswd  
-  grep root /etc/paswd
-  grep -n root /etc/passwd -> xem ở dòng bao nhiêu
-  grep -i huan /etc/passwd -> tìm cái tên 

- xem nội dung trong file  nào đó  kiểu như ký tự phân cách lấy dữ liệu theo cột hoặc hàng dựa vào ký tự phân cách .
- cut -d' ' -f2 name_file -> lấy cột 2 
- cut -d':' -f2 name_file

## 14. Tiến trình - Process
- ps -> xem tiến trình
- kill pid -> xóa tiến trình
- vd : kill -9 num_process -> xóa tiến trình
- vd: ps aux -> liệt kê toàn bộ tiến trình trên hệ thống

## 15. Xem cấu hình CPU , RAM ,HDD
- cat /proc/cpuinfo -> xem CPU
- cat /proc/meminfo -> xem RAM
- free -> xem thông tin về RAM
- df -h -> xem HDD

## 16. Thiết lập cấu hình mạng trên linux - IP v4 
![image](https://user-images.githubusercontent.com/90398366/166085269-e78dd4e5-c3a8-4804-baf5-ab7f6953342b.png)
- Lệnh xem địa chỉ mạng : 
- ip a -> xem địa chỉ ip
- ip route -> xem defaugateway
- cat/etc/resolv-conf -> xem DNS
- /etc/sysconfig/network-scripts : - ifcfg-l0 và - ifcfg-enp0s3
> demo config ip :
- B1 :vào /etc/sysconfig/network-scripts 
- B2:  vi ifcfg-enp0s3
- B3:  chỉnh BOOTPROTO = static , PEERDNS =no 
- B4: khai báo : IPADDR=....., NETMASK=..... , GATEWAY=.....
- B5: lưu -> :wq
- B6: khởi động lại -> service network restart  -> Thành công  và đăng nhập lại

> Khai báo DNS servers 
- vi etc/resolv-conf
- nameserver 8.8.8.8 -> ping google.com   

## 17.Cài đặt gói tin Linux -rpm ( Red Hat Package ) dùng rpm hoặc yum ( tự động)

- Ví dụ muốn cài 1 file trong http://mirror.centos.org/ lên servers linux 
- Ta cần cài đặt https://winscp.net/eng/download.php ( WINCP)
- Vào wincp điền các thông số máy muốn cài vào : host name , port number , user name , password ...
- sau khi mở wincp  có 2 màn hình windown và linux 
- kéo file dowload từ windown sang linux bằng cách dùng chuột kéo
- Setup như sau : rpm -ivh name_file (telnet-0.17....)
- kiểm tra lại thì gõ name_file
- rpm -qa | grep từ khóa file
- gỡ : rpm -e name_file

## 18.Cài đặt gói tin Linux -rpm ( Red Hat Package ) dùng rpm hoặc yum ( tự động) dùng yum

- cd/etc/yum.repos.d/ -> khai báo vị trí servers chứa các file đã cài đặt
- less CentOS-sources.repo -> xem file đó
- setup : yum search telnet -> ví dụ cài telnet
- yum install name_program   -> y -> y ->hoàn thành
- yum remove name_program -> y -> xóa 

## 19 . Thiết lập cấu hình mạng IP v4 trên Linux
- Các lệnh xem địa chỉ mạng : ip a -> xem địa chỉ ip v4 , ip route -> xem địa default gateway , cat/etc/resolv.conf -> khai bao DNS server 
- /etc/sysconfig/network-scripts : ifcfg-lo and ifcfg-enp0s3 -> cạc mạng
> vd đổi địa chỉ ip 
- cd /etc/sysconfig/network-scripts 
- vi ifcfg-enp0s3 
- sửa đổi các thông số : bootproto = "stastic" , peerdns = "no" , khai báo ipaddr = 192.168.1.1 , netmask = 255.255.255.0, gateway = 192.168.1.1
- service network restart -> reset lại mạng
- đăng nhập và kiểm tra -> ip a 

## 20 .Các lệnh troubleshoot mạng cơ bản   - ip a , ping , nslookup ,telnet
> các lệnh này giúp kiểm tra kết nối mạng để nhằm khắc phục sự cố cho máy chủ
- yum install bind-utils -> setup gói tin chứa lệnh nslookup -> tra cứu các bản ghi DNS xem trả về ip address không 
- yum install telnet -y -> setup lệnh telnet
- telnet vnexpress.net 80  -> check chạy dịch vụ HTTP
- thoat : "ctrl" + "]" -> quit

# NOTE Back root : su -> input password
## 21 Cài đặt Iptables và thiết lập luật firewall cơ bản
- Framework lọc gói tin là netfilter ( theo IP và Port )
- Disable firewalld
> Các lệnh
- rpm -qa | grep firewalld -> check filewalld^c
- systemctl stop fire
- systemctl disable firewalld^c
- rpm -qa | grep iptables -> check xem iptable 
-  yum install iptables -services -> cài đặt iptables
-  systemctl enable iptables -> cài dịch vụ iptables
-  systemctl start iptables -> bật
-  systemctl status iptables -> xem kích hoạt chưa
-  iptables -L -> xem bản ip tables
> Cài dịch vụ http  -> mở port 80 trên iptables 
- vi etc/sysconfig/iptables ->copy dòng có :  dport 22
- "ii" + "p" kéo tới 22 thay băng 80 -> chấp nhận cổng 80 mở
- :wq -> lưu lại và thoát
- systemctl restart iptables -> khởi động lại 
- iptables -L -> kiểm tra 
