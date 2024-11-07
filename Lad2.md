#heading1
1.phân tích ca sử dụng:
Tác Nhân (Actors)
- Nhân Viên (Employee) - Tác nhân chung tương tác với hệ thống để thực hiện các nhiệm vụ như lựa chọn phương thức thanh toán, quản lý thẻ chấm công và quản lý đơn đặt hàng.
- Nhân Viên Hưởng Hoa Hồng (Commissioned Employee) - Là loại nhân viên đặc biệt có thêm quyền truy cập để quản lý đơn đặt hàng.
- Quản Trị Viên Tiền Lương (Payroll Administrator) - Có trách nhiệm tạo báo cáo hành chính, quản lý thông tin nhân viên, và xử lý bảng lương.
- Cơ Sở Dữ Liệu Dự Án (Project Database) - Hệ thống hoặc tác nhân bên ngoài được liên kết với việc quản lý thẻ chấm công.
- Đồng Hồ Hệ Thống (System Clock) - Đại diện cho chức năng theo dõi thời gian cần thiết cho xử lý bảng lương.
- Máy In (Printer) - Sử dụng để in các báo cáo hoặc tài liệu bảng lương.
- Hệ Thống Ngân Hàng (Bank System) - Sử dụng để xử lý các giao dịch cho bảng lương.
1.1 Các Trường Hợp Sử Dụng (Use Cases)
- Chọn Phương Thức Thanh Toán (Select Payment) - Cho phép nhân viên chọn phương thức thanh toán.
- Quản Lý Thẻ Chấm Công (Maintain Timecard) - Nhân viên, có liên kết với Cơ Sở Dữ Liệu Dự Án, quản lý thẻ chấm công của họ tại đây.
- Tạo Nhân Viên (Create Employee) - Thêm nhân viên mới vào hệ thống.
- Quản Lý Đơn Đặt Hàng (Maintain Purchase Order) - Chỉ dành cho Nhân Viên Hưởng Hoa Hồng để quản lý đơn đặt hàng.
- Đăng Nhập (Login) - Điểm truy cập chung cho người dùng có thẩm quyền.
- Tạo Báo Cáo Hành Chính (Create Administrative Report) - Quản Trị Viên Tiền Lương tạo báo cáo.
- Quản Lý Thông Tin Nhân Viên (Maintain Employee Info) - Quản Trị Viên Tiền Lương quản lý dữ liệu nhân viên.
- Chạy Bảng Lương (Run Payroll) - Tích hợp với Máy In và Hệ Thống Ngân Hàng để xử lý bảng lương.
  
```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;


// Lớp timecard đại diện cho mỗi bản ghi timecard
class Timecard {
    private String employeeId;
    private String date;
    private double hoursWorked;

    public Timecard(String employeeId, String date, double hoursWorked) {
        this.employeeId = employeeId;
        this.date = date;
        this.hoursWorked = hoursWorked;
    }

    public String getEmployeeId() {
        return employeeId;
    }

    public String getDate() {
        return date;
    }

    public double getHoursWorked() {
        return hoursWorked;
    }

    public void setHoursWorked(double hoursWorked) {
        this.hoursWorked = hoursWorked;
    }

    @Override
    public String toString() {
        return "Employee ID: " + employeeId + ", Date: " + date + ", Hours Worked: " + hoursWorked;
    }
}

// Lớp TimecardManager quản lý các thao tác trên timecard
class TimecardManager {
    private Map<String, Timecard> timecards = new HashMap<>(); // Key: employeeId + date

    // Add a new timecard
    public void createTimecard(String employeeId, String date, double hoursWorked) {
        String key = employeeId + "-" + date;
        if (timecards.containsKey(key)) {
            System.out.println("Timecard already exists for this employee on this date.");
        } else {
            Timecard timecard = new Timecard(employeeId, date, hoursWorked);
            timecards.put(key, timecard);
            System.out.println("Timecard created successfully.");
        }
    }

  // Cập nhật thẻ thời gian hiện có
    public void updateTimecard(String employeeId, String date, double hoursWorked) {
        String key = employeeId + "-" + date;
        Timecard timecard = timecards.get(key);
        if (timecard != null) {
            timecard.setHoursWorked(hoursWorked);
            System.out.println("Timecard updated successfully.");
        } else {
            System.out.println("Timecard not found.");
        }
    }

   // Xóa thẻ thời gian
    public void deleteTimecard(String employeeId, String date) {
        String key = employeeId + "-" + date;
        if (timecards.remove(key) != null) {
            System.out.println("Timecard deleted successfully.");
        } else {
            System.out.println("Timecard not found.");
        }
    }

 // Hiển thị tất cả các timecard
    public void displayTimecards() {
        if (timecards.isEmpty()) {
            System.out.println("No timecards found.");
        } else {
            System.out.println("Timecards:");
            for (Timecard timecard : timecards.values()) {
                System.out.println(timecard);
            }
        }
    }
}

public class MaintainTimecardApp {
    public static void main(String[] args) {
        TimecardManager manager = new TimecardManager();
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            System.out.println("\nChoose an option:");
            System.out.println("1. Create Timecard");
            System.out.println("2. Update Timecard");
            System.out.println("3. Delete Timecard");
            System.out.println("4. Display All Timecards");
            System.out.println("5. Exit");
            
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter Employee ID: ");
                    String empId = scanner.nextLine();
                    System.out.print("Enter Date (YYYY-MM-DD): ");
                    String date = scanner.nextLine();
                    System.out.print("Enter Hours Worked: ");
                    double hours = scanner.nextDouble();
                    manager.createTimecard(empId, date, hours);
                    break;
                case 2:
                    System.out.print("Enter Employee ID: ");
                    empId = scanner.nextLine();
                    System.out.print("Enter Date (YYYY-MM-DD): ");
                    date = scanner.nextLine();
                    System.out.print("Enter New Hours Worked: ");
                    hours = scanner.nextDouble();
                    manager.updateTimecard(empId, date, hours);
                    break;
                case 3:
                    System.out.print("Enter Employee ID: ");
                    empId = scanner.nextLine();
                    System.out.print("Enter Date (YYYY-MM-DD): ");
                    date = scanner.nextLine();
                    manager.deleteTimecard(empId, date);
                    break;
                case 4:
                    manager.displayTimecards();
                    break;
                case 5:
                    System.out.println("Exiting the application.");
                    scanner.close();
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please select again.");
            }
        }
    }
}



```
