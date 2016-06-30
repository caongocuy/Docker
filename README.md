# Docker begin

#### Giới Thiệu

Trên các diễn đàn, group công nghệ thời gian gần đây có một chủ đề đang được bàn tán sôi nổi, thu hút sự chú ý của nhiều người ham mê công nghệ, Docker vâng chính là
Docker, hiện nay Docker đang được các tay to công nghệ như Google, Amazon, IBM, Microsoft ....chú ý và đã hhox trợ trên nền tảng của họ.

![img](http://image.prntscr.com/image/3d8a01a6a186469dbfe08583da846cdc.png "img")

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
nhưng vẫn có gì đó tốn kém ( con người luôn tham lam mà ), chưa kể các vấn đề về hiệu suất cần được đặc biệt quan tâm. Tiếp sau đó người ta nghĩ ra containerization, đại ý mô hình nó sẽ là như thế này.

![img](http://image.prntscr.com/image/8c39655e4e70473d9add372a9ccb9df5.png "img")

Với kỹ thuật này, trên 1 máy chủ vật lí, sẽ sinh ra nhiều máy con (giống máy ảo - ảo hóa), nhưng cái hay là các máy con này đều dùng chung phần nhân cảu máy mẹ và chia se tài nguyên của máy mẹ, như vậy việc tận dụng tài nguyên sẽ dc tối ưu hơn, ngoài ra việc sử dụng hệ thống file cắt lớp (layer file system) sẽ khiên việc tối ưu hiệu quả hơn.

Vậy thì Docker làm được gì nào: 

- Khi các bạn code và test dưới local thì chạy ngon lành, nhưng khi deploy lên production thì lại tạch. Nguyên nhân là do sự khác nhau giữa môi trường local và server (local chạy Ubuntu, server chạy CentOS chẳng hạn, hay server chạy Ruby 2.2.3 trong khi local chạy Ruby 2.3), với Docker ta có thể tạo môi trường y hệt trên server.

- Dừng được nhiều hđh hơn mà b ko mất công cài đặt, phân bổ tài nguyên ....

- Dùng được nhiều môi trường lập trình mà không ảnh hưởng đến môi trường chính của bạn.

- Chia sẻ môi trường với team: khi container với môi trường bạn test ngon nghe rồi b có thể dể dàng chia sẻ cho mọi người sử dụng chung mà ko làm mất tg hay công sức cài đặt mới.

- Phục vụ test : rõ rồi trên nhiều môi trường, hddh mà lại tốn ít tg, nhanh chóng nữa.
 ....

#### 2. Các thao tác cơ bản

Ở trên chúng ta đã biết Docker là gì, sơ bộ thành phần, chức năng, độ nguy hiểm rồi, bay giờ ta thử bắt tay vào sờ xem nó hình gì nhé.

###### 2.1 Cài đặt

Hiện tại thì Docker có thể sử dụng trên Win, linux, Mac, trong bài viết này tôi chỉ thực hiện trên Linux, win vs mac thì không có điều kiện nên cũng chưa thử được.

Tôi sẽ thực hiện trên ubuntu nhé, bắt đầu

```
sudo apt-get update
sudo apt-get install docker.io
```

sau khi chạy xong ta có thể kiểm tra phiên bản docker

```
docker -v
```

Các bạn đã đọc về Docker container, vậy nó bây giờ ở đầu và làm thể nào để có được.

Có 2 cách: một là bạn có thể tải về từ docker hup, hai là bạn có thể tạo ra 1 cái của mình và dùng, mình sẽ trình bày cách đầu tiên trước

"Hello-world" là một từ khá thần thánh khi bạn vọc vạch vào 1 ngôn ngữ mới hay gì đó, Docker cũng thế, bạn chạy lệnh

```
docker run hello-world
```

lệnh này sẽ call docker engine với message tạo 1 container từ image tên là hello-world, thằng docker engine sẽ timg trong máy bạn xem có image nào như thế chưa, có rồi nó sẽ tạo 1 container chạy trên cái image kia, chưa có
nó sẽ lên docker hub và tải image đó về cho bạn (mỗi lần chạy lệnh docker run nó sẽ tạo 1 container mới).

![img](http://image.prntscr.com/image/c46840925ab148c081c4f3be413f5dff.png "img")

nó sẽ ra như thế này, bạn có thể kiểm tra các images như sau

![img](http://image.prntscr.com/image/fd81c2d49584429b97681e251be0aee1.png "img")

Hiệ tại chỉ có 1 image chúng ta vừa tải về. Nếu b muốn tải thêm các image về thì chạy lại lệnh run với tên image nếu có nó tải về, hoặc bạn lên hub tìm image và chạy lệnh 

```
docker pull (author_name)/(Image_name).ví dụ : docker pull uycn/ubuntu14.04
```

Để liệt kê các container đang chạy, bạn sẽ làm như sau

```
docker ps # list các container đang chạy
docker ps -a # đương nhiên là all rồi
```

ta thử tải image ubuntu về xem nó nặng đén mức nào

```
docker pull ubuntu:14.04 # ubuntu là hàng chính hãng nên ko cần tên ông tác giả đằng trước 
```

![img](http://image.prntscr.com/image/ee19528042204f1295d8aab1e93368d5.png "img")

nặng quá :D

Sau khi tải về rồi thì tạo 1 container và chạy lên thôi

```
docker run -it ubuntu:14.04
```

Sao lại có -it ở đây, đơn giản là nếu ko có thì nó chỉ bật container thôi và ko làm gì cả, thêm i: là để vào terminal, t để show kết quả lệnh bạn chạy trong đó, bạn cứ thử đi, từ đây b có thể làm mọi thứ nhứ trên 1 máy ảo rồi nhé.

Quên mất, để thoát khỏi container mà nó vẫn chạy thì bạn dùng ctrl+p và ctrl+q >> đước này gọi là detach khỏi container, để vào lại (attach) bạn chạy

```
docker attach container_id # ấn thêm 2 lần enter 
```

id thì b chạy lệnh docker ps -a là có nhé

Thoát khỏi container và stop thì b exit là được, nếu muốn chạy lại thì bạn dùng

```
docker start -a container_id
```

Để xóa container

```
docker rm container_id
```

Quên mất, xóa image thì làm dư lày

```
docker rmi image_id
```

Tạm thời như thế này đã, lâu không typing mỏi quá, bài tiếp theo sẽ là tạo 1 image từ đầu và tung lên giời (đẩy lên hub) và tải về .
