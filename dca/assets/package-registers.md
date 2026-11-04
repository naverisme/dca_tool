# Mẫu hồ sơ kiểm định ngoài docs

## <folder-review>/provenance.md

| Mã nguồn | Tên, phiên bản và vị trí gốc | Độ phủ/loại thẩm quyền | Mệnh đề đã rút | Tài liệu biên soạn |
| --- | --- | --- | --- | --- |
| SRC-01 | <file/URL; commit/bản/ngày; mục/trang/dòng> | <đã đọc phần nào; người nói/duyệt nếu có> | FACT-01: <phát biểu có điều kiện> | docs/<danh-mục>/<chủ-đề>.md |

<Ghi ánh xạ khi gộp nhiều câu thành một quy tắc hoặc tách một file thô qua nhiều tài liệu. Giữ bản gốc ở nơi cũ; đây là dấu vết, không phải bản sao nội dung.>

## <folder-review>/unresolved.md

| Mã | Loại và trạng thái | Hai cách hiểu hoặc dữ kiện thiếu | Nguồn và vị trí | Chủ đề bị chặn | Quyết định cần có |
| --- | --- | --- | --- | --- | --- |
| DOC-01 | CONFLICT / CONFLICTING | <phát biểu A; phát biểu B> | <SRC-01 §...; SRC-02 §...> | <tài liệu hoặc phần chưa được đưa vào docs> | <câu hỏi cho người có quyền chốt> |

<Nếu không phát hiện vấn đề trong phạm vi đã khảo sát, ghi “Chưa phát hiện trong phạm vi X”, nêu phần chưa đọc. Không gọi đó là xác nhận toàn bộ dự án không có vấn đề.>

## <folder-review>/manifest.md

| Trường | Giá trị |
| --- | --- |
| Nguồn và mốc | <đường dẫn nguồn, commit/phiên bản/ngày và phần đã đọc> |
| Docs | <đường dẫn folder docs> |
| Review | <đường dẫn folder review> |
| File DCA sở hữu | <đường dẫn từng file và hash sau khi ghi> |
| Mục tiêu, lĩnh vực, người đọc | <mục tiêu bộ dữ liệu tài liệu và đối tượng sử dụng> |
| Quy ước phân loại | <chuẩn đã chỉ định, phiên bản hoặc lựa chọn trình bày đã thống nhất> |

<Không ghi nhận quyền sở hữu file có sẵn của người dùng chỉ vì DCA đã đọc file đó.>
