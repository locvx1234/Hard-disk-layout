# Ổ cứng - Hard disk drive (HDD)
(Hard disk, hard drive, fixed disk)

## 1.Khái niệm
Ổ cứng là thiết bị lưu trữ dữ liệu sử dụng nhiều đĩa (`platter`) phủ từ tính quay đều quanh trục.
## 2.Cấu tạo
Đĩa cứng chia ra làm 4 phần: cụm đĩa, cụm đầu đọc, cụm mạch điện và vỏ
### a. Cụm đĩa
#### Platter (đĩa)
Đĩa bằng nhôm hay thủy tinh, bề mặt của nó phủ từ tính. 
Các đĩa được bố trí song song đồng trục và quay cùng tốc độ.
Một ổ đĩa có nhiều đĩa, dữ liệu có thể chứa trên hai mặt của đĩa.
##### Track
Trên mỗi đĩa chia thành các vòng tròn đồng tâm, gọi là các `Track`
<img src="https://camo.githubusercontent.com/72163fa2e42a886a6b792481fd2d8430af52b6c6/687474703a2f2f69313336332e70686f746f6275636b65742e636f6d2f616c62756d732f723731342f486f616e674c6f7665397a2f6469736b2f747261636b5f7a7073383370676c72676b2e706e67">
##### Sector 
Track chia làm nhiều `sector`. `Sector` là đơn vị nhỏ nhất không thể phân chia tiếp.
Kích thước chuẩn của một sector là 512 byte.
<img src="https://camo.githubusercontent.com/3da7c24d7701edfffa6592355a5663f6aef3a686/687474703a2f2f69313336332e70686f746f6275636b65742e636f6d2f616c62756d732f723731342f486f616e674c6f7665397a2f6469736b2f736563746f725f7a707369676a7a646561662e706e67">
##### Cylinder
Tập hợp các Track có cùng bán kính trên ổ cứng tạo thành `Cylinder` 
#### Spindle (trục quay)
Trục để gắn và truyền chuyển động cho các đĩa từ.
<img src="https://camo.githubusercontent.com/112a9cd786d2ed466164d5f55d98c1fa8e3f08c0/687474703a2f2f69313336332e70686f746f6275636b65742e636f6d2f616c62756d732f723731342f486f616e674c6f7665397a2f6469736b2f63796c696e6465725f7a7073787273797064346e2e706e67">
### b. Cụm đầu đọc
#### Write/Read Head (Đầu đọc/ghi)
Đọc dữ liệu dưới dạng từ hóa hoặc từ hóa lên các mặt ghi dữ liệu
Số đầu đọc/ghi bằng số mặt hoạt động của các đĩa.
#### Arm (Cần di chuyển đầu đọc/ghi)
 Cần di chuyển song song với các đĩa, dịch chuyển và định vị đầu đọc/ghi từ mép đĩa vào phía trong đĩa.
<img src="i.imgur.com/G8VfZjH.jpg">
### c. Cụm mạch điện
- Mạch điều khiển : điều khiển động cơ trục, điều khiển cần đọc/ghi
- Mạch xử lý dữ liệu : xử lý dữ liệu đọc ghi
- Bộ đệm (cache/buffer)
- Đầu cắm nguồn
- Đầu giao tiếp với máy tính 
### d. Vỏ
Vỏ có tác dụng định vị các chi tiết và ngăn bụi vào trong ổ đĩa.

## 3. Các lệnh làm việc với disk trên Linux 
### Liệt kê các ổ đĩa 

 	$ ls /dev/sd*

<img src="http://i.imgur.com/0F1qjRw.png">

### fdisk
- Các công cụ làm việc với ổ đĩa cần quyền root
- Ví dụ thực hiện trên ổ sdb

	$ fdisk /dev/sdb
	
<img src="http://i.imgur.com/kzWUJH9.png">

- Hiển thị menu: <code>m</code>
<img src="http://i.imgur.com/adId6cb.png">

- In bảng phân vùng: <code>p</code>
<img src="http://i.imgur.com/77HaHnZ.png">

- Tạo một phân vùng: <code>n</code>
<img src="http://i.imgur.com/D2QbH8E.png">

- Xóa một phân vùng: <code>d</code>

### parted
Công cụ tương tự với `fdisk`
Lệnh làm việc với ổ cứng

	$ parted /dev/sdb

<img src="http://i.imgur.com/ChlyTsC.png">
Trợ giúp: `help`
Tạo nhãn: `mklabel msdos`
Tạo phân vùng mới : `mkpart`
Sau đó điền tiếp các thuộc tính.
<img src="http://i.imgur.com/eBPjNxf.png">
In bảng phân vùng : `print`
xóa phân vùng : `rm`

### sfdisk, cfidsk
Tương tự như `fdisk` và `parted`.
Sử dụng lệnh `man` để xem thông tin chi tiết.

##  4. Tham khảo

http://www.binarytides.com/linux-command-check-disk-partitions/

