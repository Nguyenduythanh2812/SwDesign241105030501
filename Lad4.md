# Phân tích ca sử dụng trong hệ thống Pay roll
## 1.1 Mô tả sự tương tác giữa các đối tượng thiết kế
Mục tiêu: Mô tả sự tương tác giữa các đối tượng chính trong Use Case Login.

Các đối tượng chính bao gồm:

User (Người dùng): Gửi thông tin đăng nhập (email và mật khẩu).
Authentication System (Hệ thống xác thực): Xử lý logic xác thực và kiểm tra thông tin đăng nhập.
Database (Cơ sở dữ liệu): Lưu trữ và kiểm tra thông tin tài khoản người dùng.

### Sơ đồ tuần tự (Sequence Diagram):
![](https://www.planttext.com/api/plantuml/png/N9113e9034NtSug65IGIzomC9fv0eliAHIU16JBjQ3YR2u_a5Pm9GS5bs_z-V_xx-IfPq8dlEuMrM0Sd9gU6iDAr7j0897ilDp9XHj7MG3MoK9y0CiJBDAw80mfUa4cfQ0RvRY4ie2BJG6Ulse0shOMKUjJT1WPaVbZNPEgdZkpiLi2Pd6x71Qlc6-H_JuuatXcuHs8ExeXz9oltGCM8N_ra7HeHpv2ohsjYthOXdtUKgJ94Zqrz0000__y30000)

Giải thích:

- Người dùng gửi thông tin đăng nhập (email và mật khẩu) đến Hệ thống xác thực.
- Hệ thống xác thực gửi yêu cầu đến Cơ sở dữ liệu để kiểm tra thông tin.
- Cơ sở dữ liệu trả về kết quả xác thực (hợp lệ hoặc không hợp lệ).
- Hệ thống xác thực phản hồi người dùng với trạng thái đăng nhập (thành công hoặc thất bại).
## 2 Đơn giản hóa sơ đồ tuần tự sử dụng phân hệ

Mục tiêu: Đơn giản hóa sơ đồ tuần tự bằng cách sử dụng các phân hệ (subsystems).

Trong Use Case Login:

UI Subsystem: Nhận thông tin từ người dùng và hiển thị kết quả.
Authentication Subsystem: Xử lý logic xác thực.
Database Subsystem: Lưu trữ và kiểm tra thông tin tài khoản.
### Sơ đồ tuần tự với phân hệ (Subsystems):
![](https://www.planttext.com/api/plantuml/png/T5513e8m4Bpt5HlkV823KOC7RaQ3zmMBDe52kbiJtkR19_a5so1QQZpkpipEJFPvVwo9qR3jMe4rzmPAaaOCRgLgDQ1cICe2ZhQYaLXs2I11MNpc9NDZ-Igrcv5LhoEL1__eScIia6IaoBTVll2v85s5vXdiDBjjsr-K1gMRNWIe9oyyCzWZKSXUm9uVE6PmaaOruyGN0GBfx-M3P6iqtBnahcyasPPZaxZ2MpcbShzWIyiMNk2wPv0h6beSvxjhgS_-RIy0003__mC0)

Giải thích:

- UI Subsystem: Nhận thông tin từ người dùng và hiển thị kết quả.
- Authentication Subsystem: Xử lý logic xác thực.
- Database Subsystem: Lưu trữ và kiểm tra thông tin tài khoản.

## 3 Mô tả hành vi liên quan đến lưu trữ

Mục tiêu: Mô tả hành vi liên quan đến lưu trữ và quản lý thông tin tài khoản người dùng.

Trong Use Case Login:

- Hệ thống cần lưu trữ thông tin tài khoản người dùng (email và mật khẩu) trong cơ sở dữ liệu.
- Khi người dùng đăng nhập, hệ thống xác thực cần truy vấn cơ sở dữ liệu để kiểm tra thông tin tài khoản.
![](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bToJc9niK9eSMgHGZMNWeAkGcQAWfL2S4bHPbuwc9-QcvYPWofK0DHIdb-4eb118Jsrn3D5GnD3q1La01Rn0AWfo5ArN507kIIM92Ob5gU27QMWK9nObgfH2dAa5TYj82rb-PafOCcqpBmKiAGdmaMQK8L04nrIyr90FWK0003__mC0)

Giải thích:

- Lớp User đại diện cho thông tin tài khoản người dùng, bao gồm id, email và mật khẩu.
- Lớp Database cung cấp các phương thức để lưu trữ (save) và truy xuất (find) thông tin tài khoản.

## 4 Cải tiến mô tả luồng sự kiện
Mục tiêu: Định nghĩa rõ luồng chính và luồng thay thế trong quá trình đăng nhập.

Luồng chính:
- Người dùng nhập thông tin đăng nhập.
- Hệ thống xác thực kiểm tra thông tin.
- Nếu thông tin hợp lệ, người dùng đăng nhập thành công.

Luồng thay thế:
- Người dùng nhập sai email hoặc mật khẩu.
- Hệ thống xác thực trả về thông báo lỗi (ví dụ: "Sai mật khẩu" hoặc "Tài khoản không tồn tại").
### Sơ đồ tuần tự với luồng thay thế:
![](https://www.planttext.com/api/plantuml/png/n94z3i8m34RtdC8Z7Ng13gWWO6AYWZsqJecKffATLEhP63WILo1fAtwwmCRYmVe-FJ_vVhtbx2GvtnWXZOF2boKoAs_0jBMs0k38I90kOUNTfUZPOPF1rhgmxAJHrPW3RLKRmgzGh6pMXJ_pr3aXQTL_njy2aCuO1tIUB7InfalfT6k1a7suSZ6GanalzEEj6Um713zL11f6s4bjiFf1Izl_YKtiBsfgL5aWKKlG14jPOoBGLY8F8pxp0G00__y30000)

Giải thích:

Luồng chính: Nếu thông tin hợp lệ, người dùng được đăng nhập.

Luồng thay thế: Nếu thông tin không hợp lệ, hệ thống trả về thông báo lỗi.

## 5 Hợp nhất các lớp và phân hệ
Mục tiêu: Tổ chức lại các lớp và phân hệ sao cho dễ quản lý và dễ hiểu.

UI Subsystem:

- Lớp LoginPage: Giao diện người dùng.
- Lớp LoginController: Quản lý sự kiện giao diện.
- 
Authentication Subsystem:

- Lớp AuthService: Xử lý logic xác thực.
- Lớp Validator: Kiểm tra tính hợp lệ của dữ liệu (email, mật khẩu, v.v.).

Database Subsystem:

- Lớp UserRepository: Kết nối với cơ sở dữ liệu, thực hiện lưu trữ và truy vấn dữ liệu.
- Lớp Database: Quản lý kết nối với cơ sở dữ liệu.
Sơ đồ lớp hợp nhất với phân hệ:
![](https://www.planttext.com/api/plantuml/png/R55BQiCm4Dtx528h6Ng2hD9F5eKiGaAwdqZJPAWi6StOnPISh8iUgLUebOyL5siXqBolcD_ldmKBH6agLzHWFk20QhPxLTjcpnqBLZFrLIXb732hLJYGNoTAcgLZYMi7dIxxzsdCUmvUOd0Euy0-WhSEp-XLSIfowcCZH_H21eI2dswGE5kCBPdS0R8EDLP0xa7LFVapH3lkzGQEB4Z8ZThB19T9TX6N_w3rrKgFFU-Rlu307XYdE-yOumRhmDGdTqFqEtcReATk8foXnGJgfh_K_Emn_ikGUVCpmNiqeikycljHQhn0RzEY_m000F__0m00)

Giải thích:

- UI Subsystem: Chịu trách nhiệm giao tiếp với người dùng, nhận thông tin và hiển thị kết quả.
- Authentication Subsystem: Xử lý logic xác thực thông tin người dùng.
- Database Subsystem: Quản lý và lưu trữ thông tin người dùng.
