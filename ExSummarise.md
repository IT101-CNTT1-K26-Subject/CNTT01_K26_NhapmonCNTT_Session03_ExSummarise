**EXERCISE SUMMARISE**  
## Phần 1 — Kiến trúc Hệ điều hành  
- Việc chạy đồng thời Word, Chrome, VS Code và phần mềm nộp bài là hoạt động của chức năng Quản lý tiến trình (Process Management) kết hợp với Quản lý bộ nhớ (Memory Management) của Hệ điều hành. Các phần mềm này chạy được cùng lúc mà không xung đột vì Hệ điều hành sử dụng cơ chế chia sẻ thời gian (Time-sharing) của CPU, phân phối các lát cắt thời gian cực nhanh cho từng tiến trình tạo cảm giác chúng chạy song song. Đồng thời, hệ thống cung cấp không gian bộ nhớ ảo (Virtual Memory) riêng biệt và cơ chế bảo vệ bộ nhớ, khiến vùng nhớ của ứng dụng này bị cô lập hoàn toàn với ứng dụng khác, ngăn chặn việc ghi đè dữ liệu lẫn nhau.  
- Khi bạn double-click vào file báo cáo, hành động đó được xử lý qua lớp Shell trước, sau đó mới đến Kernel. Shell đóng vai trò là giao diện trung gian (ở đây là Graphical User Interface - GUI của Windows Explorer) nhận yêu cầu từ người dùng và dịch nó thành lời gọi hệ thống (system call) gửi xuống cho Kernel. Kernel là lõi của hệ điều hành, chịu trách nhiệm quản lý trực tiếp phần cứng, phân phối tài nguyên CPU và bộ nhớ để khởi chạy tiến trình đọc file. Người dùng không tương tác trực tiếp với Kernel vì Kernel hoạt động ở vùng nhớ đặc quyền (Kernel space), mọi thao tác sai sót trực tiếp ở tầng này có thể gây treo hệ thống hoặc lỗi màn hình xanh (BSOD), trong khi Shell cung cấp môi trường an toàn và trực quan để thao tác.  
## Phần 2 — Cây thư mục & Ổ đĩa  
1. Dựa vào cây thư mục ở mục 3b:  
  2. Root Directory (Thư mục gốc): D:\  
  3. Parent Directory trực tiếp của file anh 1.jpg: Thư mục Hinh anh  
  4. File anh 1.jpg đóng vai trò là "lá" (Leaf) trong mô hình cây thư mục vì nó là nút kết thúc, không chứa các thư mục con bên dưới.  
2. Việc lưu toàn bộ dự án ở Desktop hoặc Downloads (thuộc User Profile trên ổ C:) là một lựa chọn cực kỳ nguy hiểm vì hai lý do kỹ thuật sau:  
  4. Thứ nhất, ổ C:\ là phân vùng chứa Hệ điều hành. Khi hệ thống gặp sự cố phải cài lại Windows hoặc phân vùng hệ thống bị lỗi, toàn bộ dữ liệu trên Desktop và Downloads sẽ bị mất trắng.  
  5. Thứ hai, đường dẫn User Profile mặc định thường chứa tên người dùng có dấu tiếng Việt hoặc khoảng trắng (ví dụ: C:\Users\Nguyễn Văn A\Desktop), điều này rất dễ gây ra lỗi cú pháp, lỗi "File Not Found" hoặc lỗi đường dẫn khi bạn làm việc với các công cụ dòng lệnh, biên dịch code, hoặc khi copy sang máy tính khác của giảng viên.Nơi lưu trữ đúng là trên phân vùng dữ liệu riêng biệt (như ổ D:\) được tổ chức khoa học.  
## Phần 3 — Đường dẫn Path  
1. Absolute Path (Đường dẫn tuyệt đối) đầy đủ và chính xác của file anh 1.jpg:  
  2. D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh\anh 1.jpg  
2. Relative Path (Đường dẫn tương đối) để chèn file logo.png vào trong file report.html:assets/logo.png  
  2. Sử dụng Relative Path trong trường hợp này giúp dự án không bị lỗi khi nén thư mục BaiTapLonIT101 gửi cho giảng viên sang một máy tính khác vì đường dẫn được tính dựa trên vị trí hiện tại của file report.html. Nó không phụ thuộc vào tên ổ đĩa hay cây thư mục cấp cao trên máy của người nhận (dù là ổ C:\, D:\ hay máy Mac/Linux), miễn là cấu trúc bên trong thư mục dự án được giữ nguyên.  
## Phần 4 — Quy tắc Đặt tên chuẩn  
- Đổi tên file Báo cáo bài tập lớn IT101 (bản cuối) v2.docx sang chuẩn kebab-case:bao-cao-bai-tap-lon-it101-ban-cuoi-v2.docx  
## Phần 5 — Tổ chức & Dọn dẹp Ổ đĩa  
1. Đường dẫn ở mục 3b đang lồng tổng cộng 9 cấp thư mục (tính từ gốc ổ D:\, không tính tên ổ và file: Nam1 -> HocKy1 -> MonHoc -> CongNgheThongTin -> BaiTapLon -> Session02 -> BaoCaoCuoiKy -> Chuong1 -> Hinh anh). Đường dẫn này đã vi phạm nghiêm trọng Quy tắc 3 Cấp Thư Mục, chứa tiếng Việt có dấu và khoảng trắng.                          
Thiết kế lại đường dẫn chứa file anh 1.jpg trên ổ D:\ tuân thủ mô hình 4 Trụ Cột và Quy tắc 3 Cấp:  
- Cấp 1 (Trụ cột): D:\01_HocTap  
- Cấp 2 (Môn học/Dự án): D:\01_HocTap\IT101  
- Cấp 3 (Nhóm nội dung): D:\01_HocTap\IT101\Images  
Đường dẫn mới hoàn chỉnh cho file ảnh:D:\01_HocTap\IT101\Images\anh-1.jpg  
## Phần 6 — Đuôi file & File ẩn  
- File hiển thị là de-thi-dap-an.pdf nhưng máy đang ẩn đuôi mở rộng là một cạm bẫy giả mạo phần mở rộng (Extension Spoofing). Kẻ gian lợi dụng tính năng mặc định của Windows là ẩn phần mở rộng của các định dạng quen thuộc để che giấu đuôi thực thi thật sự ở phía sau.  
- Tên file thật có khả năng cao là một file mã độc thực thi như: de-thi-dap-an.pdf.exe hoặc de-thi-dap-an.pdf.scr. Khi bạn nhấp đôi chuột, Windows sẽ thực thi file chương trình .exe thay vì mở tài liệu PDF, khiến máy tính bị nhiễm mã độc.  
- Thao tác cụ thể trong Windows File Explorer để phát hiện sự thật này trước khi mở: Trên thanh menu phía trên của cửa sổ File Explorer, bạn chuyển sang tab View, sau đó tìm và tích chọn vào ô File name extensions (Phần mở rộng tên tệp). Ngay lập tức, Windows sẽ hiển thị toàn bộ phần đuôi thật của file, giúp bạn nhận diện chính xác đây có phải là file tài liệu an toàn hay không.  
   
