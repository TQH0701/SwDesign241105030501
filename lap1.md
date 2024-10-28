# 1 Phân tích kiến trúc hệ thống Payroll System

## 1.1 Phân tích kiến trúc

- **Kiến trúc phù hợp**: Kiến trúc Model – View – Controller (MVC) là lựa chọn phù hợp cho hệ thống Payroll System.
- 
  **Giải thích**: Khi áp dụng kiến trúc MVC vào hệ thống Payroll System sẽ giúp tổ chức code tốt hơn, quản lý dữ liệu nhân viên, tính lương, chấm công hiệu quả. Ngoài ra, hệ thống cũng dễ dàng thêm các chức năng mới (ví dụ: tính thuế, bảo hiểm) và bảo trì hệ thống.
Giải thích lý do lựa chọn.
 ### 1.2 Áp dụng MVC giúp phân tách rõ ràng các phần của hệ thống:

- **Model** quản lý dữ liệu và logic nghiệp vụ,
- **View** đảm nhiệm việc hiển thị dữ liệu và giao diện người dùng,
- **Controller** xử lý yêu cầu của người dùng và điều hướng dữ liệu.
### 1.3 Ý nghĩa của từng thành phần trong kiến trúc
- **Model**: Chứa các lớp quản lý dữ liệu và logic nghiệp vụ, bao gồm các lớp như Employee, Payroll, Timecard, Project. Những lớp này sẽ chứa các thuộc tính và phương thức để xử lý lương, quản lý thời gian, v.v.
- **View**: Hiển thị dữ liệu cho người dùng, bao gồm các giao diện nhập liệu, bảng biểu và báo cáo.
- **Controller**: Nhận yêu cầu từ người dùng, điều hướng đến Model để xử lý và chọn View phù hợp để trả kết quả cho người dùng.
- **Biểu đồ Package mô tả kiến trúc**
![Package diagram](https://www.planttext.com/api/plantuml/png/ZLDDRy8m3BttLqGzWL3_G0yJqzYa7IeX8UrkMWCP-QXY5uGc_lkIqD8WO5ekLVnilvTdTquCZZkjiXRgFMnHv9LjKENY9nF-r0g8nBjkbJqXzi5m2jcKGXeU0mOqbcB5JfhjDJhJiCSbd3GQdcoiqwNeRn_-CYt5mSecPfyJlYGbfMmluGfvPvixgWAqxGoNOgCiZBfcX0fhNgQravGu9da8tMjiS0zIjzPow31vAjhPRqzKWV4sXim5CAo1KjTc18Uh7Vrp5iWW5Jqr9jPjSU1VCN17G_7dPGhJ6pVEsJaRv_abyNWxphvJ059jZQHMmIcHyS2AdJts2YX-1k9RLrB-DslOMQNGFLGnmgcMrjaQYVwrER7W04esm7_ksjfQXM16ZN7LHL6yY555AVAEaF8i4HOoWbi1QmEBXwDx0OXDFDBRvw4vcYRyKhy0))

## 2. Cơ chế phân tích
#### Hệ thống Payroll System yêu cầu các cơ chế sau để đáp ứng yêu cầu nghiệp vụ:

- **Persistency**: Đảm bảo lưu trữ dữ liệu lâu dài và tin cậy cho các bản ghi nhân viên, bảng chấm công, hóa đơn, báo cáo và phương thức thanh toán.

- **Legacy Interface**: Đảm bảo tương tác với hệ thống cơ sở dữ liệu cũ (DB2 trên mainframe IBM) mà không gây ảnh hưởng tới dữ liệu hiện tại. Điều này cho phép Acme tận dụng hệ thống cũ, giúp tiết kiệm chi phí.

- **Security**: Bảo vệ dữ liệu cá nhân của nhân viên và lương khỏi truy cập trái phép. Chỉ người có quyền mới được truy cập hoặc chỉnh sửa dữ liệu.

# 3. Phân tích Ca sử dụng Select Payment
## 3.1. Các lớp phân tích cho Select Payment
- **Boundary**:

`PaymentForm`: Giao diện cho người dùng để nhập thông tin thanh toán.
`ProjectManagementDatabase`: Cơ sở dữ liệu chứa thông tin dự án và các phương thức thanh toán.
- **Control**:

`PaymentController`: Xử lý các yêu cầu thanh toán từ PaymentForm, xác thực và điều hướng dữ liệu.
- **Entity**:

`Employee`: Lưu trữ thông tin nhân viên bao gồm các thuộc tính cần thiết cho việc thanh toán.
 ## 3.2. Nhiệm vụ của từng lớp phân tích
- **PaymentForm**: Hiển thị giao diện người dùng để nhập và hiển thị các thông tin thanh toán.
- **ProjectManagementDatabase**: Truy xuất và lưu trữ thông tin thanh toán cho từng nhân viên.
- **PaymentController**: Nhận yêu cầu từ PaymentForm, kiểm tra và xác thực các thông tin cần thiết, tương tác với Model để lấy thông tin cần thiết.
- **Employee**: Chứa thông tin về nhân viên, bao gồm các phương thức liên quan đến việc thanh toán.
## 3.3. Biểu đồ Sequence
![Package diagram](https://www.planttext.com/api/plantuml/png/TL0x3i8m3DrpYemmz08TK2KA6n8I9t1JWuASE8hTeRSlvTU2slNzxKeKidQ133ZbR0yX4VU89ZrWxto2gFOCVS2eHyvX2TzprCn4c7_Pp7TqUe88DnnrDIWq86ZCfyKMktbuQQ-Ug4O5JxBPcXarKqvrfPMk2LudwSGz3MiBIfioEnHvsyQ0DQqjbglJ2xeeQ2VB2_wlQxqaWlvhCHN6Tlpz0000)

## 3.4. Biểu đồ lớp và giải thích
![Package diagram](https://www.planttext.com/api/plantuml/png/VLBBReD03Bpp5IjEZH0_mA5ArRHI3f4YvGiC6BhjFj3Q8A6g_zu5iZnQaJtQC_RCU8_4uBZLAYeK48ahz1eDlrkdnNSa_4kRgNH1_h1b9cxifAcd5cZR6iv4fIpmM4e85HPyNNEU3fdeh2mdW2-ZUnc9smQrkPQ1ERT-egsoLslOMQNGtVKbZRC54WLYvQLdQn-R9HqeMGBZ8tHkhK8mo-ettIZR8uP4f8z1cibmQa3Z9fL4mzV3-NzyEVlf4xk0WHe7r0aOSg2mBI7evd7tMvoGGIhQjrbZ2FB6m2q5udbIVfW5Und_WqtJv_NaJCGj8SNHdCCAiD0yJ0wtXO8zTcVgdjbXHpCSPg6EVt0WXRKUKqa_gXHv7qT7DENmRty1)

# 4. Phân tích Ca sử dụng Maintain Timecard
## 4.1. Các lớp phân tích cho Maintain Timecard
- **Boundary**:

`TimecardForm`: Giao diện cho người dùng để nhập và xem dữ liệu chấm công.
Control:

`TimecardController`: Xử lý yêu cầu từ TimecardForm, điều hướng tới Model để lấy và lưu dữ liệu chấm công.
- **Entity**:

`Timecard`: Chứa thông tin chấm công của nhân viên, bao gồm các thuộc tính như ngày, giờ vào, giờ ra.
`Employee`: Chứa thông tin của nhân viên và mối quan hệ với lớp Timecard.
## 4.2. Nhiệm vụ của từng lớp phân tích
- **TimecardForm**: Hiển thị giao diện người dùng để nhập và xem thông tin chấm công.
- **TimecardController**: Nhận yêu cầu từ TimecardForm, xác thực và điều hướng dữ liệu chấm công giữa TimecardForm và lớp Model liên quan.
- **Timecard**: Chứa dữ liệu chấm công của nhân viên, bao gồm các thuộc tính về thời gian làm việc.
- **Employee**: Kết nối với Timecard để lưu trữ và quản lý dữ liệu chấm công của nhân viên.
## 4.3. Biểu đồ Sequence
![Package diagram](https://www.planttext.com/api/plantuml/png/ZP913eCW44Ntd89bk_02BXetNNRLNc024qCZIAQZIMzVgMABYU0Ivir_uOVcnK0ys4w0ufxarVgkVoCknniuQ964do2ZZ0V7yc4iAY2TNCQzEz9e52Qp9IIEH6HbTTdkrL8H0kFfB3QJ04Vp7nMlPBKVfYSkBnsyFY1TgRnqnhxIvUKX9YsXbk0zzMD8IoUfyaSbpfsmafFmYOeBoXNA6cVgGBKjSgdN6ScNIiW3kM1hqEdmNyK7)
### Giải thích 
- **Nhân viên**:

Thực hiện thao tác tạo (create), cập nhật (update) và lấy thông tin (get) thẻ thời gian qua EmployeeService.
-**Quản lý**:

Thực hiện phê duyệt (approve) hoặc từ chối (reject) thẻ thời gian qua ManagerService.
- **Timecard**:

Các phương thức create(), update(), approve(), reject(), và get() được gọi từ dịch vụ tương ứng và trả về kết quả cho người dùng.

## 4.4. Biểu đồ lớp và giải thích
![Package diagram](https://www.planttext.com/api/plantuml/png/fP8zRy8m441t_meh4mK5mPe1CRH3Xqv5wdpANLDJV-boGK8L_nsdEA5GL5N2W-LxPzdlpbwt0YoTiwgsqBPwOnpLmAY_b4wZD5Xfu-KKa8isx8cUVyAFq77x5lYJ4dst0J974AhqOvg_urdDbDQJXqhlWi4JwoB-OaYMhbb3qeD1JXrKrdtAHZTrFRXay2fiV9ETAAPg7Ncvu3D0lBoGoONTFsIpsA1n5di13mtnlLunSkyXkV1p2wvijrJB7xkIrlYmPRaQVIjTB0irkFQPpNX6iPZFfuKQEtmpgzRaiVyzHm00)
### Giải thích 
- **Timecard**:

  Thuộc tính: id, employeeId, hoursWorked, date.
  Phương thức: create(), update(), delete(), get().
- **Employee**:

  Thuộc tính: id, name.
  Phương thức: add(), remove(), update(), get().
- **Manager**:

  Thuộc tính: id, name.
 Phương thức: approve(), reject().
- **Mối quan hệ**:
  
  Một Employee có nhiều Timecard (1-N).
Manager có thể phê duyệt hoặc từ chối nhiều Timecard (0-N).
Một Timecard chỉ thuộc về một Employee (1).

# 5. Hợp nhất kết quả phân tích
- Bằng cách kết hợp các lớp phân tích từ hai ca sử dụng trên, ta có một hệ thống thống nhất với các lớp Employee, Timecard, PaymentController, và TimecardController. Các lớp này giúp quản lý chặt chẽ quy trình chấm công và thanh toán cho nhân viên, đảm bảo tính toàn vẹn và bảo mật dữ liệu.

