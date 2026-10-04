# BÁO CÁO THỰC HÀNH: QUẢN LÝ TỆP TIN BỎ QUA (.GITIGNORE) VÀ SỬA LỊCH SỬ (AMEND)

- **Bài tập:** Bài 4 - Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)
- **Đường dẫn nộp bài:** `homework/session_04/ex4/`
- **Họ và tên:** Đỗ Đức Mạnh
- **Tài khoản GitHub:** domanh09012006
- **Email:** doducmanh09012006@gmail.com

---

## 1. Bối cảnh và Yêu cầu giải quyết

- **Sự cố:** Vô tình đưa tệp tin bảo mật nhạy cảm `credentials.txt` vào commit gần nhất trên Git.
- **Mục tiêu:**
  1. Gỡ tệp `credentials.txt` ra khỏi vùng theo dõi (Index/Cache) của Git mà **không xóa file vật lý** trên đĩa cứng.
  2. Khai báo vào `.gitignore` để Git vĩnh viễn bỏ qua tệp này trong các lần thay đổi tương lai.
  3. Dùng `git commit --amend` để ghi đè commit lỗi trước đó, cập nhật commit mới sạch sẽ cả về nội dung lẫn message.

---

## 2. Các bước thực hiện chi tiết

### Bước 1: Giả lập sự cố commit nhầm file nhạy cảm
```powershell
# Tạo các tệp tin làm việc
New-Item app.py -Value "print('App running...')"
New-Item credentials.txt -Value "API_KEY=secret_key_12345"

# Đưa tất cả vào stage và commit nhầm
git add .
git commit -m "feat: add app and config credentials"