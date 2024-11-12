
# Lab 2

## 1. Phân tích ca sử dụng:

### Maintain Timecard
- **Mô tả:** Ca sử dụng này cho phép nhân viên hoặc quản lý nhập thông tin chấm công (timecard) vào hệ thống. Các thông tin bao gồm mã nhân viên, ngày làm việc, và số giờ làm việc. Dữ liệu này sẽ được lưu vào cơ sở dữ liệu để tính toán lương sau này.
- **Actor:** Nhân viên, Quản lý
- **Tiền điều kiện**:
- Nhân viên hoặc quản lý đã đăng nhập thành công vào hệ thống.
- Người dùng phải có quyền truy cập vào chức năng "Maintain Timecard".
- **Hậu điều kiện**:
-   Thông tin chấm công được lưu vào cơ sở dữ liệu.
- Hệ thống phản hồi về trạng thái (thành công hoặc thất bại).
- **Các bước thực hiện:**
  1. Nhân viên đăng nhập vào hệ thống.
  2. Chọn tùy chọn "Maintain Timecard".
  3. Nhập thông tin chấm công bao gồm: ngày làm việc, số giờ làm việc, và mã nhân viên.
  4. Lưu thông tin chấm công vào cơ sở dữ liệu.
  5. Hệ thống hiển thị thông báo cập nhật thành công.
- **Ngoại lệ:**
  - Thông tin nhập không hợp lệ (ví dụ: số giờ làm vượt quá giới hạn).
  - Nhân viên không có quyền truy cập vào chức năng này.

### Calculate Payroll
- **Mô tả:** Ca sử dụng này tính toán bảng lương dựa trên thông tin chấm công đã được nhập và các thông tin bảng lương cơ bản như lương cơ bản theo giờ, bảo hiểm, và thuế.
- **Actor:** Hệ thống, Quản lý
- **Tiền điều kiện**:
- Thông tin chấm công của nhân viên đã được ghi nhận trong cơ sở dữ liệu.
- Bảng lương cơ bản được thiết lập đầy đủ trong hệ thống.
- **Hậu điều kiện**:
- Thông tin bảng lương được lưu vào cơ sở dữ liệu.
- Hệ thống hiển thị kết quả tính toán cho quản lý.
- **Các bước thực hiện:**
  1. Hệ thống truy xuất thông tin chấm công của nhân viên.
  2. Tính toán tổng thu nhập dựa trên giờ làm việc và lương cơ bản.
  3. Trừ các khoản khấu trừ (bảo hiểm, thuế).
  4. Cập nhật thông tin vào bảng lương và hiển thị cho quản lý.

### Select Payment Method
- **Mô tả:** Nhân viên chọn phương thức thanh toán lương (chuyển khoản ngân hàng, tiền mặt).
- **Actor:** Nhân viên
- **Tiền điều kiện**:
- Nhân viên đã đăng nhập thành công vào hệ thống.
- Các phương thức thanh toán đã được thiết lập trong hệ thống.
- **Hậu điều kiện**:
- Thông tin về phương thức thanh toán được lưu vào cơ sở dữ liệu.
- **Các bước thực hiện:**
  1. Nhân viên đăng nhập vào hệ thống.
  2. Chọn tùy chọn "Select Payment Method".
  3. Chọn phương thức thanh toán mong muốn.
  4. Hệ thống lưu lại thông tin lựa chọn.

### View Pay Statement
- **Mô tả:** Nhân viên có thể xem bảng lương của mình.
- **Actor:** Nhân viên
- **Tiền điều kiện**:
- Nhân viên đã đăng nhập thành công vào hệ thống.
- Dữ liệu bảng lương đã được tính toán và lưu vào cơ sở dữ liệu.
- **Hậu điều kiện**:
- Nhân viên có thể xem thông tin bảng lương chi tiết.
- **Các bước thực hiện:**
  1. Nhân viên đăng nhập vào hệ thống.
  2. Chọn tùy chọn "View Pay Statement".
  3. Hệ thống hiển thị bảng lương cho nhân viên.

## 3. Java mô phỏng ca sử dụng: Maintain Timecard

Dưới đây là mã nguồn Java mô phỏng chức năng **Maintain Timecard**:

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// Lớp User để lưu thông tin người dùng
class User {
    private String username;
    private String password;
    private String role; // "employee" hoặc "manager"

    public User(String username, String password, String role) {
        this.username = username;
        this.password = password;
        this.role = role;
    }

    public String getUsername() {
        return username;
    }

    public String getPassword() {
        return password;
    }

    public String getRole() {
        return role;
    }
}

// Lớp Timecard lưu thông tin chấm công
class Timecard {
    private String employeeId;
    private String workDate;
    private int hoursWorked;

    public Timecard(String employeeId, String workDate, int hoursWorked) {
        this.employeeId = employeeId;
        this.workDate = workDate;
        this.hoursWorked = hoursWorked;
    }

    public String getEmployeeId() {
        return employeeId;
    }

    public String getWorkDate() {
        return workDate;
    }

    public int getHoursWorked() {
        return hoursWorked;
    }

    @Override
    public String toString() {
        return "Employee ID: " + employeeId + ", Work Date: " + workDate + ", Hours Worked: " + hoursWorked;
    }
}

// Lớp AuthService xác thực người dùng
class AuthService {
    private List<User> users;

    public AuthService() {
        users = new ArrayList<>();
        users.add(new User("employee1", "1234", "employee"));
        users.add(new User("manager1", "admin", "manager"));
    }

    public User login(String username, String password) {
        for (User user : users) {
            if (user.getUsername().equals(username) && user.getPassword().equals(password)) {
                return user;
            }
        }
        return null;
    }
}

// Lớp TimecardService quản lý chấm công
class TimecardService {
    private List<Timecard> timecards = new ArrayList<>();

    public void addTimecard(Timecard timecard) {
        timecards.add(timecard);
        System.out.println("Timecard added successfully.");
    }

    public void displayTimecards() {
        if (timecards.isEmpty()) {
            System.out.println("No timecards found.");
            return;
        }

        System.out.println("Timecards List:");
        for (Timecard timecard : timecards) {
            System.out.println(timecard);
        }
    }
}

// Lớp chính MaintainTimecardApp
public class MaintainTimecardApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        AuthService authService = new AuthService();
        TimecardService timecardService = new TimecardService();

        System.out.print("Enter Username: ");
        String username = scanner.next();
        System.out.print("Enter Password: ");
        String password = scanner.next();

        User user = authService.login(username, password);

        if (user == null) {
            System.out.println("Login failed. Invalid credentials.");
            return;
        }

        System.out.println("Login successful. Welcome, " + user.getRole() + "!");
        
        if (!user.getRole().equals("manager")) {
            System.out.println("You do not have permission to maintain timecards.");
            return;
        }

        while (true) {
            System.out.println("\n=== Maintain Timecard ===");
            System.out.println("1. Add Timecard");
            System.out.println("2. View Timecards");
            System.out.println("3. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter Employee ID: ");
                    String employeeId = scanner.next();
                    System.out.print("Enter Work Date (YYYY-MM-DD): ");
                    String workDate = scanner.next();
                    System.out.print("Enter Hours Worked: ");
                    int hoursWorked = scanner.nextInt();

                    // Kiểm tra tính hợp lệ của giờ làm việc
                    if (hoursWorked < 0 || hoursWorked > 24) {
                        System.out.println("Invalid hours worked. Please enter a value between 0 and 24.");
                    } else {
                        Timecard timecard = new Timecard(employeeId, workDate, hoursWorked);
                        timecardService.addTimecard(timecard);
                    }
                    break;
                case 2:
                    timecardService.displayTimecards();
                    break;
                case 3:
                    System.out.println("Exiting the application.");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}

```
