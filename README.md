# Hướng dẫn Sử dụng Git trong Môi trường Làm việc Nhóm

**Tập trung:** Chiến lược phân nhánh và quy trình hợp tác (GitHub Flow)

**Phiên bản:** 1.0  
**Ngày lập:** Tháng 1/2026

## Mục lục
1. Giới thiệu  
2. Chiến lược phân nhánh  
3. Quy tắc đặt tên nhánh  
4. Quy trình làm việc nhóm  
5. Lệnh Git về nhánh  
6. Xử lý tình huống thường gặp  
7. Best Practices  
8. Kết luận

## 1. Giới thiệu
Git giúp nhiều lập trình viên làm việc cùng dự án mà không xung đột. Tài liệu này sử dụng GitHub Flow – mô hình đơn giản, phổ biến nhất hiện nay.

## 2. Chiến lược phân nhánh
main                    ← Nhánh chính, luôn ổn định ├── feature/            ← Tính năng mới ├── bugfix/             ← Sửa lỗi thông thường ├── hotfix/             ← Sửa lỗi khẩn cấp └── release/            ← (Tùy chọn) Phát hành phiên bản
Quy tắc quan trọng: Không push trực tiếp lên main. Mọi thay đổi phải qua Pull Request.

## 3. Quy tắc đặt tên nhánh
Định dạng: `<loại>/<mô-tả-ngắn>` (kebab-case)

Ví dụ:
- feature/user-login-google
- bugfix/fix-payment-error
- hotfix/security-patch
- release/v2.1.0

## 4. Quy trình làm việc nhóm (GitHub Flow)

1. Cập nhật main:
   git checkout main && git pull origin main

2. Tạo nhánh mới:
   git checkout -b feature/ten-tinh-nang

3. Làm việc & commit:
   git add .
   git commit -m "feat: thêm chức năng đăng nhập Google"

4. Đẩy nhánh lên:
   git push -u origin feature/ten-tinh-nang

5. Tạo Pull Request trên GitHub/GitLab

6. Review → Merge (khuyến nghị dùng Squash and merge)

7. Xóa nhánh sau merge:
   git branch -d feature/ten-tinh-nang
   git push origin --delete feature/ten-tinh-nang

## 5. Các lệnh Git về nhánh

git branch                  → Liệt kê nhánh local
git branch -a               → Liệt kê tất cả nhánh
git checkout -b <tên>       → Tạo + chuyển nhánh
git merge <tên-nhánh>       → Hợp nhất nhánh
git branch -d <tên>         → Xóa nhánh local
git push origin --delete <tên> → Xóa nhánh remote

## 6. Xử lý tình huống thường gặp

Cập nhật nhánh đang làm:
git checkout feature/xxx
git pull origin main
# hoặc git rebase main

Giải quyết conflict:
- Sửa file thủ công
- git add <file>
- git commit -m "resolve merge conflict"

## 7. Best Practices
- Nhánh chỉ làm 1 việc, ngắn (1-5 ngày)
- Commit nhỏ, message rõ ràng (feat:, fix:, chore:)
- Bắt buộc tạo Pull Request + Code Review
- Dùng Squash and merge
- Xóa nhánh sau khi merge
- Không commit file lớn, mật khẩu, file tạm

## 8. Kết luận
Tuân thủ quy trình này giúp giảm xung đột code, dễ quản lý phiên bản và nâng cao chất lượng dự án.

Lưu tài liệu này vào thư mục docs/ của repository để cả đội dễ tìm.
