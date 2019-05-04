## 1: Nhân Linux ( Kernel ) là gì?
Kernel thực ra là một bộ quản lí tài nguyên, nó điều khiển toàn bộ phần cứng cũng như phần mềm của máy tính. Các tài nguyên gồm: các tiến trình (process), bộ nhớ ( memory ) và các thiết bị phần cứng ( hardwares) . Dễ hiểu thì Kernel là lớp phần mềm nằm giữa phần cứng và các chương trình ứng dụng chạy trên một máy tính. 
<img src="https://imgur.com/WkXpvZ5">
Kernel 

## 2: Quá trình khởi động trong Linux 

Quy trình này diễn ra như sau: 

### Bước 1: BIOS 
   BIOS là chương trình chạy zxđầu tiên khi nhấn nút nguồn hoặc nút reset 
   BIOS thực hiện một công việc gọi là POST ( Power-on Self-test ) kiểm tra các thông số của các phần cứng máy tính. Ngoài ra, BIOS còn cho phép thay đổi các thiết lập, cấu hình của nó. 
   BIOS được lưu trữ trên ROM của bo mạch chủ. 
   Khi quá trình POST kết thúc thành công, BIOS sẽ tìm kiếm và khởi chạy một hệ điều hành được lưu trữ trong các thiết bị lưu trữ như ổ cứng, USB,.. 
   Hệ điều hành được cài trên ổ cứng thì BIOS sẽ tìm đến phần tiếp theo đó là MBR ( Master Boot Record) 
### Bước 2: Master Boot Record ( MBR )
Sau khi BIOS xác định được thiết bị lưu trữ thì BIOS sẽ đọc trong MBR hoặc phân vùng EFI của thiết bị để nạp vào bộ nhớ một chương trình . Chương trình này sẽ định vị và khởi động boot loader. 
### Bước 3: Boot loader 
Linux có 2 boot loader phổ biến trên Linux là GRUB và ISOLINUX 
Chương trình này có mục đích cho phép lựa chọn hệ điều hành có trên máy tính để khởi động, sau đó chúng sẽ nạp kernel của hệ điều hành đó vào bộ nhớ ( RAM ) và chuyển quyền điều khiển máy tính cho kernel này. 
### Bước 4: Linux kernel được khởi nạp và chạy 
Boot loader nạp một phiên bản dạng nén của Linux Kernel. Nó tự giải nén và tự cài đặt vào RAM, nó sẽ ở đó cho tới khi tắt máy 
### Bước 5: Các script trong initrd thực thi 
Sau khi chọn kernel, hệ thống sẽ tự động nạp chương trình init trong thư mục /sbin 
INITRD cung cấp giải pháp đó là khi các chương trình thực thi khi kernel mới được khởi chạy, các chương trình này sẽ dò quét phần cứng của hệ thống và xác định xem kernel cần được hỗ trợ những gì để có thể quản lí được phần cứng đó. Nếu thiếu, chương trình INITRD có thể nạp thêm vào kernel các module bổ trợ.  
Khi chương trình INITRD kết thúc thì quá trình khởi động Linux sẽ tiếp diễn. 
### Bước 6: Chương trình init được thực thi 
Kernel được khởi chạy xong thì nó sẽ gọi duy nhất một chương trình tên là init. 
Tiến trình này có ID = 1 . Init là cha của tất cả các tiến trình khác có trên hệ thống Linux ( Không được sử dụng lệnh kill đối với tiến trình này ) 
### Bước 7: Đăng nhập giao diện đồ họa 
Gần cuối quá trình khởi đông, init sẽ bắt đầu một chế độ đăng nhập text mode. Nhập tên người dùng và mật khẩu của bạn để đăng nhập và truy cập vào hệ thống 
