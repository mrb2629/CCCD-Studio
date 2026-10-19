# CCCD Studio cho Windows

Ứng dụng đọc CCCD, CĂN CƯỚC và ảnh căn cước điện tử offline, chỉnh ảnh và ghi thông tin vào Excel.

## Tải và chạy

Mở **Releases** của kho này, tải file `CCCD_Studio_Windows_x64_*.zip`, giải nén toàn bộ rồi chạy `CCCD_Studio.exe`. Không chạy trực tiếp bên trong ZIP. Máy dùng bản đóng gói không cần cài Python.

Bộ phát hành gồm EXE, `_internal`, `models`, `tesseract`, hướng dẫn và mẫu `000 Danh sach CCCD.xlsm` có VBA. Giữ nguyên các thư mục đi kèm.

App hỗ trợ nơi làm việc, thư mục ảnh theo nơi làm việc, hạn dùng Không thời hạn và cập nhật liên kết ảnh theo cột J. Luôn đối chiếu OCR với ảnh trước khi lưu.

Xem `HUONG_DAN_SU_DUNG.txt` trong ZIP. Khi nâng cấp, giải nén vào thư mục mới và chọn lại Excel dữ liệu đang dùng.

## Kiểm tra tệp tải về

Tải thêm `.zip.sha256`, dùng PowerShell `Get-FileHash -Algorithm SHA256` trên ZIP và so sánh với nội dung tệp SHA256.

Đây là kho phân phối bản đóng gói. Các thành phần OCR và thư viện đi kèm giữ thông tin bản quyền/giấy phép của chúng trong bộ phát hành.
