#heading 1. phân tích kiến trúc
Đề xuất kiến trúc Layered Architecture để có thể phân chia dễ dàng giữa các lớp
- Lớp trình bày (Presentation): Xử lý cho các tương tác của người dùng (ví dụ: nhân viên nhập dữ liệu thẻ chấm công hoặc chọn phương thức thanh toán).
- Lớp dữ liệu (Databate) :kết nối với cơ sở dữ liệu
- Lớp logic (Business) : quản lý tính toán bản lương, chấm công...
- Lớp tích hợp (Persistence): Giao diện với hệ thống ngân hàng để thực hiện các giao dịch gửi tiền trực tiếp.
  ![](https://www.planttext.com/api/plantuml/png/X5HBJiCm4Dtx55PNiEWLK6aYKQcXei9YFt8ZssfgXxH6HAXhLfm28LOL-sR1WfFa15m1Ewr3FYva4sdcvRrvRqRvBZv7wmra6xrA44g1Be75U43A_Rja-4g0mWjH5izoW9yGnZI1zRegXoAMCmxophohbdaeBuiNUSEraenmJOdfSw90dfqV0AmiTc8CaWKSLe51LOrjZtYkGP9CH9R8aT-RMfGxIST8EUHZK06e2dpas_QjH8e9YcUCMpSfVYYBjwObewgdt13NCplTHntbfopPoViKpfnZM8fuHJBe-Vupa9gMY8DWAunDitZQDCbqZccvtwKuB8iFd5ZpkkaxKBSgr94PVLxb6-hBsda2-JNOeKpWz2XIVpZbghl-HElkUWm5uJOw8LkjbaD3rOoWGUUBBB4BxmNcC_-renoRatnDcuudSJNHZ86SmA-QNNF0THvBCqwzNaFRE_RXyC9pBl_WtBZ8U-8MsjepwX-JnVYsTGBQ2HLv3jp2EccWzhKTYPmbVxSbWqQnNDX_oGy0003__mC0)
##heading 2.cơ chế phân tích  
- Cơ sở dữ liệu: Xử lý việc lưu trữ dữ liệu nhân viên và bảng lương (ví dụ: thẻ chấm công, thanh toán).
- Bảo mật: Đảm bảo nhân viên có thể truy cập dữ liệu của riêng họ và quản trị viên tính lương có các đặc quyền riêng.
- Quản lý giao dịch: Giao dịch an toàn, đáng tin cậy để thanh toán tiền gửi trực tiếp cho ngân hàng đến người dùng.
- Xử lý lỗi: Xử lý các lỗi trong quá trình tính lương hoặc tích hợp hệ thống ngân hàng.
###heading 3. Phân tích ca sử dụng Payment
Xác định các lớp phân tích cho ca sử dụng Payment
Employee(nhân viên): chứa các chi tiết như ID nhân viên, Tên và Phương thức thanh toán. Chịu trách nhiệm lưu trữ và cung cấp quyền truy cập vào thông tin cụ thể của nhân viên.
PaymentController(trình thanh toán): Quản lý việc lựa chọn và cập nhật phương thức thanh toán. Phối hợp với hệ thống ngân hàng khi cần thiết.
BankSystem(Hệ thông ngân hàng): gửi tiền trực tiếp, yêu cầu các chi tiết như Tên ngân hàng và Số tài khoản.


Mô tả hành vi thông qua biểu đồ sequence
  ![](https://www.planttext.com/api/plantuml/png/b9EnJiCm48PtFyMDC23s3gYYOaU20KRBH7NKv6AI2r9c9eGO-WOf224g8HM9AHuw6EKz_0Iy0XUWb3P8JRCuiU__yl_s-SFE-nd9bF8u4b9Hai9HRAAa209XU3fKeP58S2oBE40Q94Xf4aL1kh9wA75qKcGKn48ivB1tq5RrOA2zlKCmkfxL4nm2yVUpua6Y1ahS14LBrQ0Ms1wSksaEobTFEQlSMyC8My2DDd8kPSYZQLdPGUsh5mHAlNrbPw6lvWRsuJANN5BF-5NflF3s6c6a4ryzuAwG4S7fCiDliG1-kWTw7tjxAvdlxSrItptBNxq8yABbQztvblx8JH5mwEuHj2lvjrUkXCpRCQ-KuGgqk-ajeFywNNPV3yxSHC7F0QvdNJtHh-tPa7p07FEDewRPIjv7rRISwBEQhymd0000__y30000)
