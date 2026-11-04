# BÀI LÀM – HACKATHON 02

- **Mã đề:** 02
- **Họ tên:** Nguyễn Ngọc Tuấn Anh
- **Lớp:** CNTT04
- **Link repository:**
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
- pwd
- ls
- Move-Item .\huong_dan_van_hanh.txt .\docs
- mkdir backup
- Copy-Item .\data\luot_gui_xe_thang_2.xlsx .\backup
- Remove-Item .\temp_202.tmp
- cd .\logs
  Get-Content .\gate.log
  cd ..
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text

Path
----
C:\Users\ngoin\Downloads\starter-kit\starter-kit\bai_xe_website



    Directory:
    C:\Users\ngoin\Downloads\starter-kit\starter-kit\bai_xe_website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/4/2026   7:37 AM                data
d-----         11/4/2026   7:36 AM                docs
d-----         11/4/2026   7:36 AM                evidence
d-----         11/4/2026   7:38 AM                logs
d-----         11/4/2026   7:31 AM                web
------         11/3/2026   7:06 AM             73 .env
-a----         11/4/2026   7:34 AM           2454 bai_lam.md
-a----         11/3/2026   7:06 AM            155 huong_dan_van_hanh.txt
------         11/3/2026   7:06 AM             22 temp_202.tmp




    Directory:
    C:\Users\ngoin\Downloads\starter-kit\starter-kit\bai_xe_website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/4/2026   7:43 AM                backup


2026-02-28 08:03:17 GET /vi-tri-bai status=200
2026-02-28 08:05:28 GET /dang-ky-ve status=200
2026-02-28 08:08:39 POST /api/cho-trong status=500
2026-02-28 08:12:50 GET /tin-tuc status=404
2026-02-28 08:16:01 GET /js/app.js status=304
2026-02-28 08:20:12 GET /css/style.css status=304
2026-02-28 08:23:23 POST /api/cho-trong status=500
2026-02-28 08:26:34 POST /api/thanh-toan status=500
2026-02-28 08:29:45 GET /js/app.js status=200
2026-02-28 08:31:56 GET /images/so-do-bai.jpg status=404
2026-02-28 08:33:07 GET /dang-ky-ve status=200
2026-02-28 08:36:18 GET /images/so-do-bai.jpg status=404
2026-02-28 08:40:29 POST /api/cho-trong status=500
2026-02-28 08:42:40 POST /api/quet-the status=500
2026-02-28 08:44:51 GET /images/banner.jpg status=304
2026-02-28 08:47:02 GET /tin-tuc status=404
2026-02-28 08:50:13 GET /lien-he status=200
2026-02-28 08:53:24 GET /css/style.css status=200
2026-02-28 08:57:35 POST /api/thanh-toan status=500
2026-02-28 08:59:46 GET / status=200
```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
- Select-String "status=500" .\logs\gate.log > .\logs\loi_500.txt
- Get-Content .\logs\loi_500.txt -TotalCount 3

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text

logs\gate.log:3:2026-02-28 08:08:39 POST /api/cho-trong status=500
logs\gate.log:7:2026-02-28 08:23:23 POST /api/cho-trong status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\gate.log | Select-String "status=404").Count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
- mkdir script
  New-Item .\script\tong_hop.ps1
- "# Script: tong_hop.ps1","# Tac gia: Nguyen Ngoc Tuan Anh","# Ngay tao: 04/11/2026",'Write-Host "Dang tao bao cao..."','"=== BAO CAO SU CO WEBSITE ===" > .\logs\tong_hop.txt','Get-Content .\logs\gate.log | Select-String "status=404" >> .\logs\tong_hop.txt','Get-Content .\logs\gate.log | Select-String "status=500" | Measure-Object >> .\logs\tong_hop.txt','Write-Host "Hoan thanh"' > .\script\tong_hop.ps1
  .\script\tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
  Directory:
    C:\Users\ngoin\Downloads\starter-kit\starter-kit\bai_xe_website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/4/2026   7:57 AM                script



    Directory: C:\Users\ngoin\Downloads\starter-kit\starter-kit\bai_xe_website\script


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/4/2026   7:59 AM              0 tong_hop.ps1


Dang tao bao cao...
Hoan thanh
```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Lỗi NetWork | ReferenceError: hienThiGiaGui is not defined | Sửa lại tên |
| 2 |  |  |  |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** 
- **Expected:** 
- **Actual:** 
- **Log:** 

### Câu tìm kiếm Google

```text
site: stackoverflow.com "Uncaught ReferenceError: hienThiGiaGui is not defined"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/luot_gui_xe_thang_2.xlsx`, không cần ghi vào đây.
