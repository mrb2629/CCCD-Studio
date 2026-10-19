# Đóng gói và đưa CCCD Studio lên GitHub

## 1. Tạo bộ phát hành

Nhấp đúp `Dong_goi_EXE.bat`. Script dùng mã nguồn hiện tại, copy nguyên mẫu `templates/000 Danh sach CCCD.xlsm` và tạo:

- `release_ngày_giờ/CCCD_Studio/`: toàn bộ ứng dụng.
- `release_ngày_giờ/CCCD_Studio_Windows_x64_*.zip`: bộ tải về đã kiểm tra CRC.
- `.zip.sha256`: mã kiểm tra tệp ZIP.
- `release_ngày_giờ/GITHUB/`: README, mô tả bản phát hành và hướng dẫn để đưa vào kho GitHub.

Đường dẫn ZIP mới nhất lưu trong `last-release.txt`. Mẫu được giữ nguyên VBA; bản phát hành không copy settings.json, ảnh CCCD, dữ liệu Excel đã nhập hay Luutru từ máy cá nhân.

## 2. Tạo kho GitHub để phân phối

1. Đăng nhập GitHub, chọn New repository, đặt tên ví dụ `CCCD-Studio` và chọn Public hoặc Private theo nhu cầu.
2. Chỉ tải các tệp trong thư mục `GITHUB` lên phần Code của kho. Có thể chỉnh README trước khi đăng.
3. Không tải toàn bộ thư mục làm việc chứa dữ liệu lên kho. File ZIP đóng gói sẽ được đính kèm ở Releases.

## 3. Đăng bản phát hành

1. Trong kho, vào Releases → Draft a new release.
2. Tạo tag ví dụ `v1.0.0` (lần sau tăng thành `v1.0.1`...). Nhập tiêu đề bản phát hành.
3. Dán nội dung `RELEASE_NOTES.md` vào mô tả.
4. Kéo ZIP và `.zip.sha256` vào vùng đính kèm assets. Chờ tải xong.
5. Kiểm tra thông tin rồi bấm Publish release khi muốn phát hành. Có thể Save draft để kiểm tra trước.
6. Sau khi đăng, tải ZIP từ chính trang Release, giải nén vào một thư mục mới và thử chạy EXE/chọn file mẫu.

GitHub yêu cầu mỗi release asset nhỏ hơn 2 GiB; script sẽ báo lỗi nếu ZIP vượt giới hạn này.
Tài liệu chính thức: https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases

## 4. Kiểm tra SHA256

Mở PowerShell tại thư mục tải về và chạy (đổi tên ZIP cho đúng):

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\CCCD_Studio_Windows_x64_ngay_gio.zip'
```

So sánh Hash với dòng trong `.zip.sha256`. Đúng mã mới giải nén và dùng.

## 5. Nếu muốn đưa cả mã nguồn lên GitHub

`.gitignore` trong dự án đã loại thư mục build/release, môi trường Python, dữ liệu Excel, ảnh kiểm thử, settings và Luutru; chỉ cho phép mẫu ở `templates`.
Trước khi commit, xem kỹ danh sách tệp bằng `git status` và `git diff --cached --name-only`. Không dùng tải cả thư mục làm việc qua giao diện web.
Mã nguồn không bao gồm model OCR và Tesseract đã cài; người tải mã phải chuẩn bị các thành phần này. Kho phân phối bản đóng gói ở bước 2 phù hợp cho người chỉ cần chạy EXE.

Các bước trên do chủ kho thực hiện; công cụ đóng gói chỉ tạo tệp tại máy, không tự đăng hoặc gửi dữ liệu lên GitHub.
