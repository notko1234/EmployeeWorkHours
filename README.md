# Employee Working Hours and Salary Management (Android, Java, Room)

## Demo accounts (seeded on first launch)
| Role | Username | Password |
|------|----------|----------|
| Admin | admin | admin123 |
| Employee | emp1 | emp123 |

## Features
- Login with Admin / Employee roles; session kept in SharedPreferences
- Room (SQLite) tables: Account, Employee, WorkLog, Salary
- Admin: add / update / delete / search / view employees (with hourly rate), calculate and manage monthly salaries (tap = toggle PAID, long-press = delete)
- Employee: daily check-in / check-out, attendance history, monthly hours / overtime / salary

## Business rules
- Hours per day = check-out - check-in; hours over 8 per day are overtime paid at 1.5x (`Utils.STANDARD_HOURS_PER_DAY`, `Utils.OVERTIME_RATE`)
- Salary = (total - overtime) x rate + overtime x rate x 1.5; PAID records are never recalculated
- Validation: one check-in per day, no check-out without check-in, check-out must be after check-in; a check-in with no check-out by the next day becomes INCOMPLETE and is excluded from salary

## Run
Open the folder in Android Studio, let Gradle sync, run on an emulator (API 24+).

## Git
```
git init
git add .
git commit -m "Initial project"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main
```
## 👥 Phân công công việc (Task Assignment)

### 1. Thành viên 1: Database & Business Logic
- [ ] Thiết kế các lớp Entity (`Account`, `Employee`, `WorkLog`, `Salary`)
- [ ] Cấu hình `AppDatabase` và triển khai các interface DAO (`AccountDao`, `EmployeeDao`, `WorkLogDao`, `SalaryDao`)
- [ ] Xây dựng logic tính toán giờ làm chuẩn, tăng ca và tiền lương trong `SalaryService` & `AttendanceService`

### 2. Thành viên 2: Phân hệ Quản trị (Admin Module)
- [ ] Phát triển `AdminMainActivity` (Danh sách nhân viên, tìm kiếm, tính lương)
- [ ] Phát triển `AdminSalaryActivity` (Quản lý và thống kê bảng lương)
- [ ] Triển khai `EmployeeEditActivity` (Thêm/Sửa/Xóa thông tin nhân viên)

### 3. Thành viên 3: Đăng nhập, Phân hệ Nhân viên & Tiện ích
- [ ] Xây dựng `LoginActivity` và quản lý phiên làm việc `SessionManager`
- [ ] Phát triển `EmployeeMainActivity` & `EmployeeSalaryActivity` cho nhân viên
- [ ] Thiết kế XML layout, các lớp `Utils` và viết tài liệu báo cáo / file README
