#heading 1. phân tích kiến trúc
Đề xuất kiến trúc Layered Architecture để có thể phân chia dễ dàng giữa các lớp
- Lớp trình bày (Presentation): Xử lý cho các tương tác của người dùng (ví dụ: nhân viên nhập dữ liệu thẻ chấm công hoặc chọn phương thức thanh toán).
- Lớp dữ liệu (Databate) :kết nối với cơ sở dữ liệu
- Lớp logic (Business) : quản lý tính toán bản lương, chấm công...
- Lớp tích hợp (Persistence): Giao diện với hệ thống ngân hàng để thực hiện các giao dịch gửi tiền trực tiếp.
- 
