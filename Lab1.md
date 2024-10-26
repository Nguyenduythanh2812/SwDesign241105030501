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
+ Xác định các lớp phân tích cho ca sử dụng Payment:
Employee(nhân viên): chứa các chi tiết như ID nhân viên, Tên và Phương thức thanh toán. Chịu trách nhiệm lưu trữ và cung cấp quyền truy cập vào thông tin cụ thể của nhân viên.
PaymentController(trình thanh toán): Quản lý việc lựa chọn và cập nhật phương thức thanh toán. Phối hợp với hệ thống ngân hàng khi cần thiết.
BankSystem(Hệ thông ngân hàng): gửi tiền trực tiếp, yêu cầu các chi tiết như Tên ngân hàng và Số tài khoản.

Mô tả hành vi thông qua biểu đồ sequence
  ![](https://www.planttext.com/api/plantuml/png/b9EnJiCm48PtFyMDC23s3gYYOaU20KRBH7NKv6AI2r9c9eGO-WOf224g8HM9AHuw6EKz_0Iy0XUWb3P8JRCuiU__yl_s-SFE-nd9bF8u4b9Hai9HRAAa209XU3fKeP58S2oBE40Q94Xf4aL1kh9wA75qKcGKn48ivB1tq5RrOA2zlKCmkfxL4nm2yVUpua6Y1ahS14LBrQ0Ms1wSksaEobTFEQlSMyC8My2DDd8kPSYZQLdPGUsh5mHAlNrbPw6lvWRsuJANN5BF-5NflF3s6c6a4ryzuAwG4S7fCiDliG1-kWTw7tjxAvdlxSrItptBNxq8yABbQztvblx8JH5mwEuHj2lvjrUkXCpRCQ-KuGgqk-ajeFywNNPV3yxSHC7F0QvdNJtHh-tPa7p07FEDewRPIjv7rRISwBEQhymd0000__y30000)

+ Xác định được nhiệm vụ và quan hệ của từng lớp phân tích:
Employee (Người lao động): Lưu trữ thông tin cá nhân và phương thức thanh toán. Quan hệ 1-1 với PaymentMethod, xác định thông tin chi tiết về thanh toán.
PaymentController(trình thanh toán): Điều phối lựa chọn phương thức thanh toán, giao tiếp với BankSystem nếu cần. Phụ thuộc vào Employee để lấy thông tin nhân viên và PaymentMethod.
BankSystem(Hệ thông ngân hàng): Quản lý giao dịch thanh toán với các ngân hàng. Tương tác với PaymentController để thực hiện thanh toán trực tiếp.

+ Biểu đồ Lớp cho ca sử dụng Payment
![](https://www.planttext.com/api/plantuml/png/T54xZi8m4ErzYX4LIBZODWKA48ejY92M2pZEQB7m9x8dHOJsP1GSQQ-m0Lb6yO8RQzwJtsVyUxsLWOIdtcWcjGW1TgRJRa242uFny0HyLWKeIn6jXS420dbbloDq48D1ItkaaskBwSX-MDIVmCdaE7Ivt4ROymkNjPIkjrJtfa6VSNkXz3YjszPZ28dClRVEadTQeu_-09rtSdmo2JV7sBn8ErWyjUxnleP0Q7AHIdcKL67dWg9vazLOWdZLuA6STZ_xc07dZskwnlyDE5-bU6_ePrHMect7l_u3003__mC0)

Giải thích:
-Employee: sở hữu thông tin thanh toán qua lớp PaymentMethod, giúp cập nhật hoặc thay đổi phương thức một cách linh hoạt.
-PaymentController: đảm nhiệm việc xử lý chọn và cập nhật phương thức thanh toán.
-BankSystem: chỉ được gọi khi nhân viên chọn phương thức thanh toán qua chuyển khoản trực tiếp

####heading 4. Phân tích ca sử dụng Maintain Timecard
+ Xác định các lớp phân tích:
- Employee: Đại diện cho nhân viên, chịu trách nhiệm lưu và gửi bảng chấm công. Thuộc tính gồm EmployeeID, Name, và danh sách Timecard.
- Timecard: Ghi lại thông tin giờ làm việc, gồm Date, HoursWorked, và ChargeNumber.
- TimecardController: Quản lý việc tạo, xác minh, và gửi bảng chấm công, phối hợp với ProjectManagementDatabase.
- ProjectManagementDatabase: Cung cấp và xác minh mã công việc (ChargeNumber) hợp lệ.
+ Biểu đồ Sequence:
![](https://www.planttext.com/api/plantuml/png/b94zIWH148NpFiLZyxt01BAWOkA2mGQcjJrDJql_3BqzWYSmrGC83eEXQ60q7HZCuZtw15x17cGHTGSnAwhgVQz-tkFhOXF8XyPeHZmuZsDJQtSb1AjpMd5LamrOAICu-VBGsU2Tri9_AvzvTo5uM98bAOomuOW2hMcp7yBOpWFpWpte0glKjmxhr7TMWbUfVp3WmukLx7Vto9ZqBt0-j1n6sGfcw3uXk5GfNdCsgS9yOgxb3mIg5BiQEiSJa-so1KxVdXkKAJv1Zze68Oll5AGY--T1Jb9yLFyuo9VjzcPey_9bbZJGmprcszkyXHo1CxOGjXnV_m400F__0m00)

+Nhiệm vụ của các lớp và quan hệ giữa chúng
-Employee: Quản lý và gửi các bảng chấm công, có mối quan hệ với Timecard.
-Timecard: Ghi nhận thông tin giờ làm việc, liên kết với Employee và được xác minh qua TimecardController.
-TimecardController: Điều phối việc xử lý bảng chấm công, xác minh mã công việc qua ProjectManagementDatabase.
-ProjectManagementDatabase: Đảm bảo mã công việc hợp lệ để quản lý chính xác.

+Biểu đồ Lớp
![](https://www.planttext.com/api/plantuml/png/Z9BDIiD058NtynINh5985cwpa4ehwC8YABY-IQxfsFcHEpU58ZwP2n_9Lp29qw58YivY26V2ET-vCryVdyiWoD9Reng38S2rVJN-G0Hl2ePL9k5sNO5s4jKDMgeW26lNJH90w6khvL5RQf3RNE971KTfeTvLJ3bAAMMDClYDUnHkVC_XoVEEsjFSrHQveqrlQ-9V-HPvTnKU9WgXDf-9Mtadx8qXZi403TCGcgWfjgrIxmBQn5R0TiIQW0fePbWM_n_6puzxD7eCE2sMppkdElViNwYHEtJOaIKd0nlM62YrsXFhvyFVdXNKtflHETrxTf51MKBciiIgPkPNbfTfHEVEptAg9RbsV7FV0000__y30000)

Giải thích:
- Employee liên kết nhiều Timecard, mỗi bảng chấm công ghi lại số giờ làm việc theo ngày.
- TimecardController xác minh và gửi bảng chấm công thông qua kiểm tra mã công việc tại ProjectManagementDatabase.
- ProjectManagementDatabase xác thực mã công việc để đảm bảo tính chính xác trong quản lý chi phí
  
#####heading 5. Hợp nhất kết quả phân tích

+Tổng hợp kiến trúc và các lớp phân tích
- Employee: Đại diện cho nhân viên, quản lý các thuộc tính như mã nhân viên (EmployeeID), phương thức thanh toán (PaymentMethod), và bảng chấm công (Timecard).
- PaymentController: Xử lý lựa chọn và cập nhật phương thức thanh toán, tương tác với hệ thống ngân hàng khi cần.
- TimecardController: Quản lý việc tạo và xác minh bảng chấm công, kiểm tra mã công việc qua cơ sở dữ liệu dự án.
- BankSystem: Quản lý giao dịch thanh toán qua ngân hàng.
- ProjectManagementDatabase: Cung cấp mã công việc hợp lệ cho bảng chấm công.
  
+ Quan hệ giữa các lớp
-Employee kết nối với Timecard để ghi lại giờ làm việc và phương thức thanh toán.
-PaymentController và TimecardController đóng vai trò điều phối, liên kết với các hệ thống bên ngoài như BankSystem và ProjectManagementDatabase.

+ Hoạt động của hệ thống qua các ca sử dụng
Trong ca sử dụng Select Payment, hệ thống xác minh và cập nhật phương thức thanh toán của nhân viên, yêu cầu thông tin nếu cần và gửi giao dịch tới BankSystem khi thanh toán qua chuyển khoản. Trong ca sử dụng Maintain Timecard, hệ thống xác minh mã công việc và lưu lại giờ làm việc của nhân viên trong Timecard.

