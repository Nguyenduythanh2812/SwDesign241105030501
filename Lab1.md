#heading 1. phân tích kiến trúc
Đề xuất kiến trúc Layered Architecture để có thể phân chia dễ dàng giữa các lớp
- Lớp trình bày (Presentation): Xử lý cho các tương tác của người dùng (ví dụ: nhân viên nhập dữ liệu thẻ chấm công hoặc chọn phương thức thanh toán).
- Lớp dữ liệu (Databate) :kết nối với cơ sở dữ liệu
- Lớp logic (Business) : quản lý tính toán bản lương, chấm công...
- Lớp tích hợp (Persistence): Giao diện với hệ thống ngân hàng để thực hiện các giao dịch gửi tiền trực tiếp.
  ![](https://www.planttext.com/api/plantuml/png/X5HBJiCm4Dtx55PNiEWLK6aYKQcXei9YFt8ZssfgXxH6HAXhLfm28LOL-sR1WfFa15m1Ewr3FYva4sdcvRrvRqRvBZv7wmra6xrA44g1Be75U43A_Rja-4g0mWjH5izoW9yGnZI1zRegXoAMCmxophohbdaeBuiNUSEraenmJOdfSw90dfqV0AmiTc8CaWKSLe51LOrjZtYkGP9CH9R8aT-RMfGxIST8EUHZK06e2dpas_QjH8e9YcUCMpSfVYYBjwObewgdt13NCplTHntbfopPoViKpfnZM8fuHJBe-Vupa9gMY8DWAunDitZQDCbqZccvtwKuB8iFd5ZpkkaxKBSgr94PVLxb6-hBsda2-JNOeKpWz2XIVpZbghl-HElkUWm5uJOw8LkjbaD3rOoWGUUBBB4BxmNcC_-renoRatnDcuudSJNHZ86SmA-QNNF0THvBCqwzNaFRE_RXyC9pBl_WtBZ8U-8MsjepwX-JnVYsTGBQ2HLv3jp2EccWzhKTYPmbVxSbWqQnNDX_oGy0003__mC0)
##heading 2.cơ chế phân tích  
