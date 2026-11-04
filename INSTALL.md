# Cài DCA cho agent

Repo này phân phối một thư mục `dca/` hoàn chỉnh. Sao chép **nguyên thư mục** vào vị trí nạp skill của agent; `SKILL.md` phải nằm trực tiếp tại `<đích>/dca/SKILL.md`. Chỉ cài khi người dùng muốn cài. Nếu chưa nêu phạm vi, chọn cấp người dùng; dùng cấp dự án khi cần cả nhóm hoặc cả hai agent cùng dùng một bản.

| Môi trường | Cấp dự án | Cấp người dùng | Kiểm tra trong phiên agent |
| --- | --- | --- | --- |
| Codex | `<project-root>/.agents/skills/dca/` | `~/.agents/skills/dca/` | `$dca help` hoặc chọn `dca` trong danh sách skill |
| Antigravity | `<project-root>/.agents/skills/dca/` | `~/.gemini/config/skills/dca/` | `/dca help` |
| Agent khác | Đọc trực tiếp `<dca_tool>/dca/SKILL.md` | Tùy cơ chế nạp đã xác minh | Yêu cầu agent đọc `SKILL.md` và thực hiện `dca help` |

Ở cấp dự án, hai agent dùng chung `.agents/skills/dca/`. Ở cấp người dùng, mỗi agent có thư mục riêng. Windows, WSL và container có thể có home khác nhau; cài trong môi trường mà agent thực sự chạy. Tránh đặt nhiều bản cùng tên ở nhiều cấp trong cùng một phiên, vì agent có thể nhìn thấy cả hai.

## Cài bằng agent

Clone repo ở một nơi có thể đọc được:

```sh
git clone https://github.com/naverisme/dca_tool.git
```

Mở agent trong dự án muốn xử lý, rồi đưa yêu cầu (thay đường dẫn tuyệt đối):

```text
Đọc <đường-dẫn>/dca_tool/INSTALL.md. Cài DCA ở cấp người dùng
trong môi trường hiện tại, kiểm tra đủ file và thực hiện dca help.
```

Agent cần đọc `dca/VERSION` và `dca/SKILL.md`, xác định đích cài, so sánh nếu đích đã tồn tại, rồi sao chép nguyên thư mục. Không ghi đè bản đã sửa riêng hoặc đi qua symlink ngoài phạm vi. Nếu bản đích giống nguồn, chỉ xác minh. Nếu khác, xem diff và chỉ cập nhật khi yêu cầu bao gồm việc cập nhật. Sau khi cài, so sánh danh sách và nội dung file, kiểm tra việc nạp trong một phiên có thể thấy skill. Nếu chỉ kiểm chứng được file mà chưa kiểm tra được discovery, báo rõ giới hạn đó.

## Cài thủ công

Chạy từ gốc dự án, thay đường dẫn nguồn. Các ví dụ sau dừng nếu bản đích tồn tại. Muốn cài cấp người dùng, thay `parent` theo bảng trên.

**Bash (Linux, macOS, WSL)**

```bash
dca_source="/absolute/path/to/dca_tool/dca"
dca_parent="$PWD/.agents/skills"
dca_destination="$dca_parent/dca"
if [ -f "$dca_source/SKILL.md" ] && [ ! -e "$dca_destination" ] && [ ! -L "$dca_destination" ]; then
    mkdir -p "$dca_parent" && cp -R "$dca_source" "$dca_destination"
else
    printf '%s\n' "Kiem tra nguon DCA hoac ban dich da ton tai: $dca_destination" >&2
fi
```

**PowerShell**

```powershell
$source = 'D:\AI-Tools\dca_tool\dca'
$parent = Join-Path (Get-Location) '.agents/skills'
$destination = Join-Path $parent 'dca'
if (-not (Test-Path -LiteralPath (Join-Path $source 'SKILL.md') -PathType Leaf)) {
    throw "Khong tim thay SKILL.md tai $source"
}
if (Test-Path -LiteralPath $destination) { throw "DCA da ton tai tai $destination" }
New-Item -ItemType Directory -Path $parent -Force -ErrorAction Stop | Out-Null
Copy-Item -LiteralPath $source -Destination $destination -Recurse -ErrorAction Stop
```

## Cập nhật và gỡ

Lấy phiên bản mới bằng `git pull --ff-only` trong checkout của `dca_tool`. So sánh bản mới với thư mục cài, sao lưu bản cũ ngoài đường dẫn agent quét, rồi thay nguyên thư mục `dca/` và đối chiếu file. Nếu có sửa riêng, giữ bản đó để xử lý khác biệt trước khi thay. Quay lại bằng bản sao lưu và kiểm tra `help`. Gỡ bằng cách di chuyển đúng thư mục `dca` đã xác minh ra ngoài vùng agent quét; không xóa skill khác.

Việc cài DCA chỉ cung cấp quy trình. `build <folder-nguồn> --output <folder-docs>` tạo docs theo profile cố định và file `<tên-folder-docs>-clarifications.md` bên cạnh khi cần. `update` nhận câu trả lời để sửa lại docs; gói không sinh báo cáo provenance hay đường dẫn nguồn thô trong đầu ra.
