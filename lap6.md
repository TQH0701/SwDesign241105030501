### Lap6
# THIẾT KẾ LỚP HỆ THỐNG PAYROLL SYSTEM
## Use case Login
1. Xác định các lớp và các operations liên quan đến use case "Login"
   Các lớp liên quan đến use case này có thể bao gồm:

- **User**
  - **Attributes**: 
    - userId: định danh người dùng
    - username: tên đăng nhập
    - password: mật khẩu đã mã hóa
  - **Operations**: 
    - login()
    - logout()
    - resetPassword()

- **AuthenticationService**
  - **Operations**: 
    - validateCredentials(String username, String password)
    - generateToken()
    - invalidateToken()

- **Session**
  - **Attributes**: 
    - sessionId: định danh phiên làm việc
    - userId: định danh người dùng
    - createdAt: thời điểm tạo phiên
    - expiresAt: thời điểm hết hạn
  - **Operations**: 
    - createSession()
    - endSession()
    - isValid()

- **UserInterface**
  - **Operations**: 
    - displayLoginError()
    - showDashboard(

![](https://www.planttext.com/api/plantuml/png/d5DBQiCm4Dth5CAh698BU54IkcsXO780LHuSKMKKPiO9eVHaNVH8lKBbZ-p4E9jwOPjvRzwRURP-lt-sB8QaENh57mur1GPblM7MBw5s-1nGA7WFf3-LRY_VbbSD0w4vGg5B8OVrMfzYpoLGbIfveTz3y61mx0kDT8s5tiTx99o3gzIN6WpROdAfGVQ3nIfFaYFqDdZD8GOfWTa5N77_Z7Z_aay-kqOEWEAiaGYKG6Td8HcR2OH_R0bewNgQ1bpW3mEFumm3lXeqzHI09OWJf6tkKXkAFS_XsNXNFUBU9ro2RSZ9TMTj92Uh9D1NR_hNce13GnOMresYypzaitbw46wXioZBsM9BzzqZuzWby80qIodI7GgGiSBwukIGgHbZKNaMm2qdfS3QT62cje1LUp3-0000__y30000)

2. Xác định các thuộc tính
   Các thuộc tính cần thiết cho các lớp đã xác định:

- **User**
  - userId: định danh người dùng
  - username: tên đăng nhập
  - password: mật khẩu đã mã hóa

- **AuthenticationService**
  - Không có thuộc tính cần thiết

- **Session**
  - sessionId: định danh phiên làm việc
  - userId: định danh người dùng
  - createdAt: thời điểm tạo phiên
  - expiresAt: thời điểm hết hạn
![](https://www.planttext.com/api/plantuml/png/Z591JiCm4Bpd5JvIYNuW1rHKLU80KgMA1opsAh6wyLQxJWf2l8m3J-8Bs2Hj6eWG9rkpCpkpQt--VwmqWiIseKBtFXXXnS8Ig9fxhdnOSuZ2H2ZcjJ36O8WeQq6NBXv8hrf52T1WQNPHVAYkpI69ZopkX2oohWFo3Y9UIXUbUM8cX90PbEqUKxUCT-nT1ftN0y7BHeJb0LMXmdFvhHY2Pj4EfVCM-v2sHhlFwERPQ_oTSMfSOSpSxH1xZjrVHiVRDjPv2WlHSvXumrZ2_ondZ7Bk_Ztj7GH7YJ1fhZKV9xje-lEYssarFrzlkRoPBAeqAPpEqkQd-qCm6tZWhp2u_Bk-0000__y30000)

3. Xác định các mối quan hệ và phụ thuộc
   - **User** và **Session**: Mỗi User có thể có nhiều Session, nhưng mỗi Session chỉ thuộc về một User.
- **AuthenticationService**: Phụ thuộc vào User để xác thực danh tính.
- **UserInterface**: Phụ thuộc vào AuthenticationService để phản hồi cho người dùng.

![](https://www.planttext.com/api/plantuml/png/Z591JiCm4Bpd5JvIYNuW1rHKLU80KgMA1opsAh6wyLQxJWf2l8m3J-8Bs2Hj6eWG9rkpCpkpQt--VwmqWiIseKBtFXXXnS8Ig9fxhdnOSuZ2H2ZcjJ36O8WeQq6NBXv8hrf52T1WQNPHVAYkpI69ZopkX2oohWFo3Y9UIXUbUM8cX90PbEqUKxUCT-nT1ftN0y7BHeJb0LMXmdFvhHY2Pj4EfVCM-v2sHhlFwERPQ_oTSMfSOSpSxH1xZjrVHiVRDjPv2WlHSvXumrZ2_ondZ7Bk_Ztj7GH7YJ1fhZKV9xje-lEYssarFrzlkRoPBAeqAPpEqkQd-qCm6tZWhp2u_Bk-0000__y30000)

4.Xác định các trạng thái chính
Các trạng thái chính của quá trình đăng nhập bao gồm:

- **Logged Out**: Người dùng chưa đăng nhập.
- **Logged In**: Người dùng đã đăng nhập thành công.
- **Login Failed**: Đăng nhập không thành công do thông tin không chính xác.
- **Session Expired**: Phiên làm việc đã hết hạn.

![](https://www.planttext.com/api/plantuml/png/P96nQiCm48RtUugR2ta13oLT0eMI5j9E9OChgvQeBHdh1DaxT6qUe4C8NGg5T2grXmmsUGyzGL-XKahi12z2_-dqVpztl_LsR2WkoUOPc2UfiDI6m_tP74UZSvngkj9fofDB1KVt2AVfRkFgDub9ywDIP6AtYR5TjizUAE6gpmAEF-pDWf0gzIh2cNt89OMIHqvqcKFt6c7x6dkRHRDYICBLNmpL2GxwvivuJudmmfBWYYIBIMhbCOnnOnvj1dts6o6R3tMQ5ZrdNM3cwXU0GMgUN5loxdU6bw6WlT8bphnreDpAdFiITAs3-RJBPdq0BgohtWc5TjKtm-8_Z0-nfN2k5FG-WnsCkKh2flu0003__mC0)


## Use case Run payroll
3. Xác định thuộc tính các lớp
   Các lớp liên quan đến use case này có thể bao gồm:

- **Payroll**
  - **Attributes**: 
    - payrollId: định danh bảng lương
    - date: thời gian thanh toán
    - totalAmount: tổng số tiền thanh toán
  - **Operations**: 
    - calculatePayroll()
    - processPayment()

- **Employee**
  - **Attributes**: 
    - employeeId: định danh nhân viên
    - name: tên nhân viên
    - salary: lương cơ bản
    - hoursWorked: số giờ làm việc
  - **Operations**: 
    - getSalary()
    - submitHours()

- **PayrollService**
  - **Operations**: 
    - generatePayroll(Employee[] employees)
    - validatePayroll(Payroll payroll)
![](https://www.planttext.com/api/plantuml/png/X5N1ZjCm4BttAqPxsOBK5RrMQBKikmWaG8Z01xZEa5frxCWULrI8B-F09_4BZ1CxzQQDzfQEt_EyUJFZ_llpzywJS1HQlV1xPS1PZujh-2AEpceDRwsX-84ELl1Uc5gZXrOmKDj6oONKmlkCBi2_5W3WWaadonSRE5XLzr4af_20ZssdxH7HlxEEOG-2CC8-Aa-lyzbj94YXPT1ypAWbffCDP0np8Xr9AEqZldDMelSSRD7GiXiFIs0XQDUNTI_ClZfwmlQx4GU6YAt6KdUD6cbKVLb8Z_szO0Dp42fq1oMHxRktmTJ27M4mZUne1UJBe1OaagdvXdn1Rsc3TCatfh6G-7dkO2ydcL6egSBMz-N23-i63vHfe4l0P2BwKujZ_8cOpYb3V21tAFVF-omTii3eypSdZ1UIb3NFq7hnaG93RrZuuqz2PuG6_wI293ZMi8ruEkN8DPnQdFNtb59DmTh0H2fhsbghKPZKOaEAKZTvAnns3Zrx52NG3eSrYGq5Jov82cvqSvoEg6ELk__XOGFiQ0mPqN93AnuFqyJVNcYUd0tKDl1OnaXgr2UadQrBQAp-ZPGyR5I66Lzne-gWJnTp6MDta_6pYXf-6U9EbHeCqYHISuB1yp4w9fdOEMGg32-IYNQGVxfO31Lz3kqMNLbNSK55We8lgxk6hyWlHzIpKvq7dd9eWoRLQIKLAMx8-TkrMjsUBTy6hjOtD-jnO_tL376o9vathjCShvZDp64lq75bp7b6PQAyBELDAvZYNqKyopge6kSp58EHSpHeM1QbKifYBnBM4FmCTZeGWwfrUYYOKvWoWv-QUuUcZlzb_m400F__0m00)

4. Xác định các thuộc tính
   Các thuộc tính cần thiết cho các lớp đã xác định:

- **Payroll**
  - payrollId: định danh bảng lương
  - date: thời gian thanh toán
  - totalAmount: tổng số tiền thanh toán

- **Employee**
  - employeeId: định danh nhân viên
  - name: tên nhân viên
  - salary: lương cơ bản
  - hoursWorked: số giờ làm việc

- **PayrollService**
  - Không có thuộc tính cần thiết
![](https://www.planttext.com/api/plantuml/png/V5DRRjj03FpNAVO2le1G66tY10ZG54QK2r1hrX6y3sF93I84ELa-SgHU8Lp9bbPIxHy988SpmyV--_pwIGo1epK57HgdWYSij04YjOKsU6DklUFqnw3U2wLMEeQ0ZZV0MAhqJK6qH-DRH7hsKbQgtmtnZxjJS9qGHsWtoD0OIhaJOZi4ryL7ST8zbrKONXkDlUfPG0IX1i9B4gEhWKz4h1YUq0bKlw0-tFjWGTnK71gtJvaQtE4vW2FGt7ZtX991AbNZEALvJDsZIEryh4qcTYFbLKkCjXTAT391Xrr9nS2HShaW_Es3Op47fbTP368wWOVDOCQ1nPoCm41e1rDzdwdtH-GNlvkt-Kjh7zsaUy5NCfXTD1FY6Xt-RPXoQeQtZG2xlcWvY76r5-tlvTYeEvUHrI7F8hkbI7BaNQHPf_zR_irqdRsNR8cP7R3zD4PEw0Vq9zeQGpwFZ62vqYmvVIINRsVvr5QhzU8Xb2eIqWNmxCglOhCZlOeR3h1Kn-0rqbNvyxfBjPTp2T9q1yvTdSNpZPHA1-p0ytvd5Ymus0li6m00__y30000)

5. Xác định các phụ thuộc và quan hệ
   
- **Payroll**: Phụ thuộc vào **Employee** để tính toán bảng lương.
- **PayrollService**: Phụ thuộc vào **Payroll** và **Employee** để thực hiện đầy đủ chức năng của hệ thống.

![](https://www.planttext.com/api/plantuml/png/X99DJiCm48NtEOMNPT4BHAYg-5knG2eSOEeyKIkE7NacaIB4oLXm9Aw07P8qD8Lk4illcpSpJ_xw-DooK92ciXcNngdW6PcsnAoUg0lUsbll9FqHr5kcb0gD6vJLLQvQRuh-5X8CMjnNjVKTm0y-HEoE10bxD2pNexP91PgiRcoK8xN2eEHgP69DAeUGiPpuEdWDvdXPmScgdiGvE1leGAwmk25NxZeML2-EseZGtc8-Tm4BcQO-FqZFlcT3BAEmGsYDnayehv1pcnVnawjqN6Om6Guh_VAhWt4I1Ns0BYylgmDYZxJiSo37fCLuTw5iwd_CQEpT9prtakCvLoTjej_UUmjooNBvQDRhpIApN3KC_WC-oUDVTZRxm6tXYlIQlm400F__0m00)

6. Xác định các trạng thái chính
   Các trạng thái chính của quá trình chạy bảng lương bao gồm:

- **Pending**: Bảng lương đang được tính toán.
- **Completed**: Bảng lương đã được tính toán thành công.
- **Failed**: Tính toán bảng lương không thành công do lỗi.
![](https://www.planttext.com/api/plantuml/png/T951JWCn34NtEONNIBq02rHH8S5kLDGLOk5c31eruupYf5BEng97wXMm9q0HJ7V9___Pidt-EAqbOyfb34uE0qEAGkxbvXLMgpjuwWF1BMm9-mevGYeC4zOKGt2pPw4jvJJGSU3tXt4AiHA9CizMzIUyb35sWy6NW5cD3gjY5pirX7ht9sHSbw8daQQCnDbQckc_ieejP6QqVJPHEv7c6cWIJ8rGJOgtrri9eLuhz8YiAxX7FkmOZpW4tC_RCWMaIgOHoiLno_chqzZAAWXnhphihMXEo88-3v7Tlp5-tQjhMmV_RRgrbh4JVm800F__0m00)
