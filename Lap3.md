# Lab 3: Identify Design Elements

## 1. Subsystem Context Diagrams

### 1.1. BankSystem Subsystem Context Diagram

![](https://www.planttext.com/api/plantuml/png/l59BJiCm4Dtx52El0FK3swYAgbAGs22adi1nfX3LiIFFM10XJiQ28t459arQsW9Rl1ZRC-_DUnhxy_rZJcmYfzefsbGUOY1KrXaYU31j3CvT1y_TZX5cCxk_vFch0bdJQHE3HIA1r-XPlQc1VxSmVhDgYR4MPkKPuzfOt161e_6qndYRV4bdnjgGFD-dki2OmOfZvHz7OEekcy4ofCBXg2SPorNmIyCe1Odd6In2S6Zyj_gHEAM2-hEOVMdp7Fx5mqtTkD0Y3gCH8n8hxlK5zNF2ut5-DBSCT28ahGwJ7UWOinskE29uhlX9_z7ur4xNl2d5k_G_hNNueSk13C7ms5X2qUvr1eI-qbkUlfnCBlHlSZks2CxHbzsl-m800F__0m00)

**Mô tả:**
- `PayrollController`: Thực hiện xử lý thanh toán qua hàm `//processPayment`, sử dụng giao diện `IBankSystem`.
- `IBankSystem`: Giao diện định nghĩa phương thức `transferFunds` để chuyển khoản, được triển khai bởi `BankSystem (proxy subsystem)`.
- `EmployeePayment`: Thực thể lưu thông tin thanh toán, được cập nhật bởi `PayrollController`.
- `PayrollSystem`: Xử lý nhiều thực thể `EmployeePayment`.
### 1.2. PrintService Subsystem Context Diagram

![](https://www.planttext.com/api/plantuml/png/j59BJiCm4Dtx52El0FK3swYAAc3JNQMUm766Ok7OmJC6MOYJiU18N04dQQX8OLblHZFpFgCdVtryhebLuDXOGK_6GV24Gbj515kLWhVspZlkAWPOhVHFKvRm9Y2_vJBWSqJYZ2ThMl4k3WARRJ2ETnXUZCPCpWs61wMnB0Sgj1tWmBl0fhK-8Mxg0dQSD_iPaB8gf0BkVQmipg36Ecestj4ukopWrdkBoXsD9xuKAqh4s9pTTr3CbkZOSEepojlJ9EVpSX9F0J8IaXI_nnrmYkjpL9e9NWq_od_ansCoGGTKt6cFCtaZUuoyNYokvAa13GbX3LNwIt_AFrhjqUNRUhCrkhhxLzy0003__mC0)

**Mô tả:**
- `PayrollController`: Điều khiển quy trình `//requestPayslip`, tạo và sử dụng phiếu lương.
- `Payslip`: Thực thể chứa thông tin phiếu lương, được tạo bởi `PayrollController` và in bởi `PrintService`.
- `IPrintService`: Giao diện định nghĩa phương thức `printPayslip` để in phiếu lương, được triển khai bởi `PrintService`.
- `PrintService`: Subsystem đảm nhận in phiếu lương thông qua giao diện `IPrintService`.

### 1.3. ProjectManagementDatabase Subsystem Context Diagram
![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTgNabcIQL2G69bKNvEJd1bSKbgBbomA3yhDRd4Dp4lCJqr5oZeabYIc9HOdCh5XQ9UGLVN3hTY1Ik5u9ByebI5aCpSrEJ4eXGkt4h11g4ORQKGb5fIb9bQXj2l05BEvP2QbmBo00000F__0m00)


**Mô tả:**
- `PayrollSystem` gửi yêu cầu Store Timecard để lưu thông tin bảng chấm công vào ProjectManagementDatabase.
- `PayrollSystem` sau đó gửi yêu cầu Retrieve Timecard Data để lấy dữ liệu bảng chấm công từ ProjectManagementDatabase.

## 2. Analysis Class to Design Element Map

| Analysis Class         | Design Element            |
|------------------------|---------------------------|
| LoginForm              | LoginForm                 |                                    
| MaintainTimecardForm   | TimecardForm              |                                      
| EmployeeController     | MainEmployeeForm          |                             
| TimecardController     | TimecardController        | 
| SystemClockInterface   | SystemClockInterface      |   
| PayrollController      | PayrollController         | 
| Paycheck               | Paycheck                  | 

## 3. Design Element to Owning Package Map

| Design Element         | Owning Package            |
|------------------------|---------------------------|
| LoginForm              | UI                        | 
| TimecardForm           | UI                        | 
| MainEmployeeForm       | UI                        | 
| TimecardController     | Controller                |
| SystemClockInterface   | Interface                 | 
| PayrollController      | Controller                | 
| Paycheck               | Model                     | 

## 4. Architectural Layers and Dependencies

![Diagram](https://www.planttext.com/api/plantuml/png/dPFBQiCm44Nt1l_3u5LAcn_meWJI5W8D5DAiZP0dZh2iCIEvmPJyUoKx3zjzqMeZVETQP-uWBQmJx9fAnr4SrKAMea18jgi4tkC8_99QM0lFL2ZpH5mDnLTLeHIS1_ri3-iMZKFEtAaysrF3DZiGbvYde8oxWo3fDcFXC8MT9k5kKdWZbVUd78UOjL3ciQerjOYVK3MJH6ipF1coMhHCMiykWkgPq_EFey1BCYxyXZm9VivuDNo9_tFMRlyYx4lV_Y-u7q9k72jJV1DpJJdgIK9Fb7kKvGWaXPQDzXq7r3z3ZT6hS2TsGk84lscjmsgfIPONowYL0bqc6sP_gRenpppemMF7dEqAvlDx6CmjXQInQ9Cu6eZ1qmqXb5NW2Uai79JRUsDV2PvhAzwNOuqcjq0c2QY5_-WUp0S0)


**Giải thích:**
- `UI`: Chứa các form để người dùng nhập thông tin (LoginForm, TimecardForm, MainEmployeeForm).
- `Controller`: Xử lý logic ứng dụng (TimecardController, PayrollController).
- `Model`: Chứa dữ liệu và logic tính toán (Paycheck).
- `Interface`: Giao diện hệ thống để lấy thời gian (SystemClockInterface).
