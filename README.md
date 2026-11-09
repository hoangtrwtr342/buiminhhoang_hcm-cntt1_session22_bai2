# Bài 2 : Xử lý lỗi thư viện mã nguồn mở bằng GitHub Issues


## 1. Cách lọc và ưu tiên bình luận trên GitHub Issues
Khi một issue có hàng chục phản hồi trái chiều, việc đọc từ trên xuống dưới rất dễ dẫn đến thử nghiệm sai hướng. Cần lọc thông tin theo 3 đặc điểm nhận diện sau:

- Tỉ lệ Reaction khẳng định (:+1: Thumbs Up, :heart: Heart, :tada: Hooray):

    - Ưu tiên các bình luận có số lượng Thumbs Up (:+1:) hoặc Trái tim (:heart:) vượt trội. Trong cộng đồng nguồn mở, đây là tín hiệu trực tiếp xác nhận "Cách này đã khắc phục được lỗi trên máy của tôi".
    
    - Cảnh báo: Tránh xa các bình luận nhận nhiều biểu tượng Thumbs Down (:-1:) hoặc Confused (:confused:) — đây là dấu hiệu giải pháp đó gây lỗi phát sinh (side-effects) hoặc không hoạt động.
 
- Huy hiệu của người bình luận (Author Badges):

  - Ưu tiên bình luận có gắn nhãn cạnh tên người dùng:

    - Maintainer / Collaborator / Owner: Thành viên phát triển dự án. Bình luận của họ thường chỉ ra chính xác nguyên nhân gốc (root cause) hoặc xác nhận một giải pháp tạm thời an toàn.
    
    - Author: Người mở issue xác nhận giải pháp đó hoạt động.

- Bình luận được "Ghim" hoặc đánh dấu phản hồi chính (Pinned Comment / Outdated mark):

    - Kiểm tra xem Maintainer có ghim một bình luận lên đầu thread hay không. Đồng thời, chú ý các đoạn mã bị đánh dấu gạch ngang (fold/collapsed) kèm nhãn Outdated để bỏ qua ngay.
 
##2. Khái niệm "Workaround" và Lý do không nên chờ bản vá chính thức
* Khái niệm Workaround
  Workaround (Giải pháp tạm thời / Đường vòng) là phương án xử lý sự cố bằng cách thay đổi cấu hình, hạ phiên bản (downgrade), viết thêm một đoạn mã bọc ngoài (wrapper), hoặc monkey-patch nhằm bỏ qua hoặc vô hiệu hóa đoạn mã bị lỗi mà không làm thay đổi trực tiếp mã nguồn gốc đã phát hành của thư viện.

* Workaround không giải quyết triệt để lỗi từ gốc rễ của thư viện, nhưng giúp hệ thống tiếp tục vận hành bình thường.

## Tại sao không nên chờ bản cập nhật chính thức ngay lúc đó?

- Chu kỳ phát hành phần mềm (Release Lifecycle) có độ trễ lớn:Kể cả khi lập trình viên sửa xong lỗi ngay lập tức, quy trình từ khi tạo Pull Request --> Review code $\rightarrow$ Chạy CI/CD kiểm thử --> Đóng gói --> Phát hành phiên bản mới lên package registry (npm, PyPI, Maven...) thường mất từ vài ngày đến vài tuần.

- Tiến độ dự án (Deadlines & Uptime):

* Công việc cá nhân, tiến độ bài tập lớn hoặc hệ thống vận hành không thể dừng lại chờ một bên thứ ba. Sử dụng workaround cho phép bạn tiếp tục phát triển tính năng khác mà không bị nghẽn (block).

- Bảo vệ mã nguồn dự án:

* Một workaround chuẩn (như khóa tạm phiên bản trước đó trong file cấu hình dependencies) an toàn hơn nhiều so với việc mạo hiểm tự sửa trực tiếp trong thư mục mã nguồn thư viện bên thứ ba (node_modules, site-packages...)
