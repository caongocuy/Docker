# Docker

Docker for Beginer

#### Giới Thiệu

Trên các diễn đàn, group công nghệ thời gian gần đây có một chủ đề đang được bàn tán sôi nổi, thu hút sự chú ý của nhiều người ham mê công nghệ, Docker vâng chính là
Docker, hiện nay Docker đang được các tay to công nghệ như Google, Amazon, IBM, Microsoft ....chú ý và đã hhox trợ trên nền tảng của họ.

#### 1. Docker là gì ?

Vậy chốt hạ lại Docker là gì, có ăn được ko, ăn có ngon không ?

"An open-source project that automates the deployment of software applications inside containers by providing an additional layer of 
abstraction and automation of OS-level virtualization on Linux." - wiki defines

###### 1.1 Các Thành Phần, Khái niệm

- Image: là file ảnh, file nền của một hệ điều hành, một nền tảng, một ngôn ngữ (vd: ubuntu image, ruby image, rails image, mysql image…). Từ các image này, bạn sẽ dùng nó để tạo ra các container.
Các image là dạng file-chỉ-đọc (read only file).

- Container: Là một máy ảo ( đại loại là vậy ), được cấu thành từ 1 image và được đắp thêm 1 lớp "vỏ" writable-file-layer. Các thay đổi trong máy ảo này (cài thêm phần mềm, tạo thêm file…) sẽ được lưu ở lớp vỏ này.
Các container này sẽ dùng chung tài nguyên của hệ thống (RAM, Disk, Network…), chính nhờ vậy, những container của bạn sẽ rất nhẹ, việc khởi động, kết nối, tương tác sẽ rất nhanh gọn.

- Docker engine: Chính là thằng quản lý. Nó quản lý việc bạn tạo image, chạy container, dùng image có sẵn hay tải image chưa có về, 
kết nối vào container, thêm, sửa, xóa image và container, cả vấn đề về network luôn, khi một container chạy nó khá giống 1 máy ảo , cũng có card mạng, ip .....

- Docker hub: là dịch vụ cloud để chia sẻ ứng dụng, lưu trữ image, có thể thao tác pull/push với các images khá giống với githup.

- Docker file: là một file chứa tập hợp các lệnh để Docker có thể đọc và thực hiện để đóng gói một image theo yêu cầu người dùng.

###### 1.2 Docker vs Virtual machine

Như trên tôi đã nói Docker Container giống như một máy ảo, vậy thì nó giống nhau ntn và khác nhau ntn để phân biệt được.

![img](http://image.prntscr.com/image/a499820cb7ce4d428c38dfbcecffd23d.png "img")

Điểm khác lớn nhất giữa 2 thanh niên này là ở Docker thì các container sử dụng chung kernel với HostOS nên các thao tác bật, tắt sẽ rất nhanh và nhẹ, ngoài ra còn một số điểm khác nữa khi sử dụng các bạn sẽ nhận ra và tôi sẽ không nói ở đây, để các bạn tự trải nghiệm.

Nếu chỉ có vậy thôi thì có nên dùng Docker không, khi mà máy ảo đang làm rất tốt công việc của nó, câu trả lời sẽ có ngay sau đây thôi.

Ngày xửa ngày xưa khi mà công nghệ ảo hóa chưa phát triển rầm rộ lắm thì người ra dùng thường là một máy chủ vật lý, chạy một HĐH và một ứng dụng nào đó - mô hình này dần dần lộ ra khuyết điểm như là lãng phí tài nguyên, mở rộng vất vả. Sau đó ảo hóa phát triển lúc này mô hình là: 1 máy chủ vật lý nhiều OS chạy trên OS mẹ, nhiều ứng dụng, tài nguyên đã dc sử dụng triệt để hơn
nhưng vẫn có gì đó tốn kém ( con người luôn tham lam mà ), chưa kể các vấn đề về hiệu suất cần được đặc biệt quan tâm. Tiếp sau đó 
