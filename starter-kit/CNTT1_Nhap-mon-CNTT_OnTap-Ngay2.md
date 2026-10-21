# BÀI LÀM – ÔN TẬP NGÀY 2

-   **Họ tên:lê trọng quang**

-   **Lớp:cntt1**

-   **Link repository:**

-   **Hệ điều hành (Windows/macOS):**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```
Get-Content error_report.txt -TotalCount 2
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```
[2026-10-21 08:15:22] ERROR: Failed to connect to database server.
[2026-10-21 08:16:05] ERROR: Timeout while waiting for API response.
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```
(Get-Content access.log | Select-String "WARNING").Count (Get-Content payment.log | Select-String "ERROR").Count
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```
WARNING trong access.log: 14
ERROR trong payment.log: 5
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```
Set-ExecutionPolicy Bypass -Scope Process -Force .\auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```
[REPORT DATE] 2026-10-21 Total warnings found in access.log: 14 Status: Completed successfully.
```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```
New-Item -ItemType Directory -Force logs Get-Content access.log | Select-String "ERROR" > logs/tong_hop_ngay2.txt Get-Content payment.log | Select-String "ERROR" >> logs/tong_hop_ngay2.txt Get-Content logs/tong_hop_ngay2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```
[2026-10-21 09:00:10] ERROR: NullReferenceException in module auth. [2026-10-21 09:12:45] ERROR: Transaction declined by gateway.
```

## Bài 5. Câu hỏi ngắn

-   **a) **-TotalCount trong lệnh Get-Content giúp giới hạn số lượng dòng đọc từ đầu file, giúp tiết kiệm tài nguyên bộ nhớ và tăng tốc độ xử lý khi đọc các tệp log có kích thước lớn.****

-   **b)Toán tử `>` tạo mới hoặc ghi đè nội dung vào file đích , nếu file đã tồn tại sẽ bị xóa nội dung cũ , trong khi toán tử `>>` thực hiện ghi nối tiếp vào cuối file mà không làm mất dữ liệu cũ.**

-   **c) Khi chạy script PowerShell mà gặp lỗi do chính sách bảo mật (Execution Policy), ta có thể tạm thời vượt qua bằng lệnh `Set-ExecutionPolicy Bypass -Scope Process -Force`**

## Tự chấm (điền sau khi có đáp án)

-   **Điểm tự chấm:** ..../100

-   **Lỗi mình đã mắc và cách sửa:**
