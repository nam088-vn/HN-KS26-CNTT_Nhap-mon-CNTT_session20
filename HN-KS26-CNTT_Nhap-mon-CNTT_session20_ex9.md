**Bài 9: Xây Dựng Prompt 3 Thành Phần Giải Mã Thông Báo Lỗi Trạm Sạc Cùng Trợ Lý AI**  
Phần 1: Thiết kế Prompt 3 Thành phần Chuẩn hóa

1. Nguyên nhân khiến AI trả lời sai (Ảo giác AI) Câu hỏi *"AI ơi phần mềm trạm sạc của tôi bị hỏng rồi làm sao đây?"*khiến AI đoán mò vì hai lý do:

* Thiếu ngữ cảnh trầm trọng: AI không thể biết phần mềm đang chạy trên hệ điều hành nào, thuộc thiết bị gì và gặp sự cố cụ thể ra sao.

* Hiện tượng ảo giác (Hallucination): Khi đầu vào quá mơ hồ, AI tự động lấp khoảng trống bằng cách suy đoán những kịch bản phổ biến nhất (như hỏng phần cứng hay đứt dây) thay vì phân tích đúng bản chất phần mềm.

2. Mẫu Prompt 3 Thành phần hoàn chỉnh

- \[Context\] Tôi là kỹ thuật viên trực ca đêm, đang vận hành hệ thống trạm sạc xe điện VoltCharge tại Bến xe Miền Đông.Trụ sạc nhanh số 04 chạy hệ điều hành Windows 11 đột ngột ngừng hoạt động và báo lỗi khi khởi động ControllerDaemon.

- \[Raw Error\] \[TERMINAL ERROR LOG \- VOLTCHARGE CHARGER \#04\] 2026-09-21 21:15:30 \[FATAL\] ControllerDaemon failed to start. System.UnauthorizedAccessException: Access to the path 'C:\\Program Files\\VoltCharge\\data\\session.log' is denied. at System.IO.FileStream.ValidateFileHandle(SafeFileHandle handle) at VoltCharge.Core.SessionManager.Initialize() InnerException: None. Process terminated with exit code 5 (0x00000005).Suggestion: Run the application with elevated administrator privileges or verify NTFS file permissions.

\[Instruction\] Hãy dịch thông báo lỗi trên sang tiếng Việt dễ hiểu, giải thích ngắn gọn nguyên nhân gốc rễ và hướng dẫn 3 bước khắc phục cụ thể tại chỗ trên Windows 11\.

Phần 2: Giải mã Lỗi & Kịch bản Khắc phục

3. Giải thích lỗi bằng tiếng Việt đơn giản

Dịch nhanh log lỗi: Hệ thống bị từ chối truy cập. Không thể ghi hoặc mở file session.log tại đường dẫn C:\\Program Files\\VoltCharge\\data.

Nguyên nhân gốc rễ: Phần mềm VoltCharge cần tạo một file nhật ký (session.log) trong ổ C để ghi lại lịch sử hoạt động.Tuy nhiên, thư mục Program Files trên Windows được bảo mật rất nghiêm ngặt. Do ứng dụng đang chạy bằng tài khoản thường (không có quyền Quản trị viên \- Administrator), Windows đã chặn không cho ghi file, làm phần mềm bị văng ra ngay lập tức.

4. 3 bước xử lý nhanh trên Windows 11

Bước 1: Chạy ứng dụng bằng quyền Quản trị viên (Khắc phục tạm thời)

* Nhấp chuột phải vào biểu tượng VoltCharge trên màn hình Desktop.

* Chọn Run as administrator (Chạy với quyền quản trị viên).

* Kiểm tra xem trụ sạc số 04 đã nhận điện lại chưa.

Bước 2: Cài đặt quyền Admin mặc định (Đảm bảo không bị lại sau khi khởi động lại)

* Nhấp chuột phải vào biểu tượng VoltCharge ➔ chọn Properties.

* Mở thẻ Compatibility.

* Đánh dấu vào ô Run this program as an administrator ➔ nhấn Apply ➔ chọn OK.

Bước 3: Phân quyền ghi file cho thư mục data (Xử lý triệt để)

* Tìm đến đường dẫn C:\\Program Files\\VoltCharge.

* Nhấp chuột phải vào thư mục data ➔ chọn Properties ➔ mở thẻ Security.

* Nhấn nút Edit, chọn tên tài khoản đang dùng, sau đó tích chọn ô Allow tại mục Write (hoặc Full control) ➔ nhấn OK để lưu.

5. Xử lý bẫy an ninh (API Key / Secret Token)

Cách xử lý: Xóa hoàn toàn hoặc sửa đoạn mã đó thành API\_KEY: \[DA\_XOA\] trước khi gửi log cho AI.

Lý do: Các nền tảng AI công cộng có thể lưu lại dữ liệu hội thoại để huấn luyện mô hình. Nếu để lộ API Key hay mật khẩu, kẻ xấu có thể lợi dụng chuỗi mã này để truy cập trái phép, can thiệp vào hệ thống trạm sạc hoặc làm rò rỉ dữ liệu vận hành.  
