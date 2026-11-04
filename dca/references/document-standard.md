# Quy ước tài liệu cố định của DCA

Đây là **quy ước cá nhân** được đưa vào DCA theo yêu cầu người dùng, lấy bảy nhóm đã chốt trong quy ước Snote làm profile `software-v1` cho các dự án phần mềm. Nó không phải chứng nhận tuân thủ ISO/IEEE. Cùng một profile phải cho cùng tên folder, file và ranh giới ở mọi dự án. Không dùng tên file thô hoặc cấu trúc cũ của dự án để tự đổi tên đích.

## Profile software-v1

| Nhóm cố định | Nội dung và ranh giới | Slot tên file cố định |
| --- | --- | --- |
| `product/` | Bài toán, mục tiêu, người dùng, phạm vi, thuật ngữ; không chứa màn hình hoặc task. | `overview.md`, `scope.md`, `glossary.md` |
| `requirements/` | Yêu cầu chức năng/phi chức năng, quy tắc, luồng, ngoại lệ, quyền và điều kiện chấp nhận nghiệp vụ; không chứa payload API/bố cục UI. | `srs.md`, `use-cases.md`, `business-workflows.md`, `permissions.md` |
| `ux/` | Điều hướng, màn hình, hành vi thành phần, trạng thái trống/tải/lỗi và wireframe; quyền gốc nằm ở requirements. | `navigation.md`, `screens.md`, `interaction-states.md` |
| `architecture/` | Ranh giới hệ thống/module, dữ liệu, bảo mật, triển khai ở mức thiết kế và quyết định kiến trúc. | `system.md`, `modules.md`, `data-model.md`, `security.md`, `decisions.md` |
| `contracts/` | Hợp đồng giao tiếp giữa thành phần, định dạng, trường, lỗi; quyền nghiệp vụ bắt nguồn ở requirements. | `api.md`, `data.md`, `events.md` |
| `verification/` | Truy vết, cách nghiệm thu, phương pháp kiểm thử và đo yêu cầu phi chức năng; không chứa log từng lần chạy. | `acceptance.md`, `test-strategy.md`, `traceability.md` |
| `operations/` | Quy trình môi trường, phát hành, theo dõi, sao lưu, phục hồi và sự cố; topology thiết kế ở architecture. | `environments.md`, `deployment.md`, `runbook.md` |

`docs/README.md` luôn là mục lục có mục tiêu bộ tài liệu, phạm vi nội dung và liên kết nội bộ. Chỉ tạo nhóm và file có thông tin đủ để viết thành nội dung hữu ích. Không tạo placeholder hoặc một file cho mỗi file nguồn. Một quy tắc có một nơi chính; các chỗ khác liên kết nội bộ tới đó.

Chọn slot theo **ý nghĩa**: ví dụ quy tắc ai được xem dữ liệu vào `requirements/permissions.md`, biểu diễn quyền qua endpoint vào `contracts/api.md`, thiết kế nơi kiểm tra quyền vào `architecture/security.md`. Nếu nội dung cần slot chưa có trong bảng, ghi một câu hỏi có ID `Q-...` để người dùng quyết định **bổ sung slot vào profile dùng chung**, không tự tạo tên riêng trong một dự án.

## Chức năng của từng slot

| File | Chứa thông tin gì |
| --- | --- |
| `product/overview.md` | Bài toán, người dùng, giá trị và mục tiêu sản phẩm. |
| `product/scope.md` | Phạm vi của phiên bản, phần bao gồm và phần loại trừ. |
| `product/glossary.md` | Định nghĩa và tên gọi chuẩn của khái niệm. |
| `requirements/srs.md` | Yêu cầu chức năng, phi chức năng, ràng buộc và mã yêu cầu; liên kết nội bộ đến quyền/luồng được đặc tả riêng. |
| `requirements/use-cases.md` | Tác nhân, mục tiêu, tiền điều kiện, luồng chính và ngoại lệ của ca sử dụng. |
| `requirements/business-workflows.md` | Trình tự công việc, vai trò, bàn giao và nhánh nghiệp vụ; không lặp nguyên văn ca sử dụng. |
| `requirements/permissions.md` | Ma trận ai được làm gì trên đối tượng nào và trong điều kiện nào. |
| `ux/navigation.md` | Điều hướng, cấu trúc thông tin, đường đi giữa các màn hình. |
| `ux/screens.md` | Nội dung và hành vi từng màn hình/thành phần; liên kết đến quy tắc quyền ở requirements. |
| `ux/interaction-states.md` | Trạng thái trống, tải, lỗi, thiếu quyền, lưu dở và phản hồi thao tác. |
| `architecture/system.md` | Ranh giới hệ thống, thành phần cấp cao và liên kết giữa chúng. |
| `architecture/modules.md` | Trách nhiệm module và hướng phụ thuộc; không ghi hợp đồng trường API. |
| `architecture/data-model.md` | Thực thể logic, quan hệ, bội số và vòng đời dữ liệu. |
| `architecture/security.md` | Thiết kế xác thực, kiểm tra quyền và bảo vệ dữ liệu; nguồn quy tắc quyền ở requirements. |
| `architecture/decisions.md` | Quyết định kiến trúc đã chốt hoặc đang chờ duyệt, bối cảnh và hệ quả. |
| `contracts/api.md` | Endpoint, yêu cầu/phản hồi, lỗi, quyền thực thi và ví dụ hợp đồng. |
| `contracts/data.md` | Schema và định dạng trao đổi dùng chung; không thay mô hình dữ liệu logic. |
| `contracts/events.md` | Sự kiện/thông điệp giữa thành phần, điều kiện phát và cách xử lý. |
| `verification/acceptance.md` | Ca nghiệm thu và kết quả mong đợi gắn với mã yêu cầu. |
| `verification/test-strategy.md` | Phương pháp, mức kiểm thử, môi trường và cách đo chỉ tiêu. |
| `verification/traceability.md` | Ánh xạ nội bộ yêu cầu → thiết kế/hợp đồng → ca nghiệm thu; không dẫn file thô. |
| `operations/environments.md` | Vai trò và yêu cầu của môi trường phát triển, thử nghiệm, vận hành. |
| `operations/deployment.md` | Quy trình phát hành, kiểm tra và quay lui. |
| `operations/runbook.md` | Theo dõi, sao lưu, phục hồi và ứng phó sự cố. |

Nếu nhiều slot cùng cần nhắc một quy tắc, chọn slot chính theo bảng và chỉ liên kết nội bộ ở slot khác. Không tạo file gộp/đổi tên chỉ vì file nguồn có tên khác.

## Trạng thái tài liệu

Đầu mỗi tài liệu ghi: `Trạng thái` (Nháp, Chờ duyệt, Đã duyệt, Thay thế), `Phạm vi áp dụng`, `Người chịu trách nhiệm` nếu biết, `Ngày cập nhật`. Thiếu xác nhận có quyền thì ghi `Nháp` hoặc `Chờ duyệt`. Không thêm đường dẫn hay trích dẫn nguồn thô. Nếu người dùng xác nhận một quyết định, có thể mô tả ngắn quyết định và ngày xác nhận bằng lời; không suy ra việc phê duyệt toàn bộ file.

## Lĩnh vực khác

Chỉ sử dụng một profile đã được người dùng chốt **cho cả lĩnh vực**, không tự thiết kế cây thư mục riêng cho mỗi dự án. Nếu chưa có profile phù hợp, tạo câu hỏi có ID `Q-...` về tên lĩnh vực, nhóm, slot, ranh giới và mẫu nội dung; chưa xuất tài liệu vào một cấu trúc tự phát. Sau khi người dùng chốt, việc bổ sung profile có phiên bản vào DCA là một thay đổi riêng; lệnh build không tự sửa gói DCA. Chỉ dùng profile đó cho các dự án cùng lĩnh vực sau khi nó đã được thêm vào quy ước. Không ép bảy nhóm phần mềm vào hồ sơ cơ khí, pháp lý hoặc lĩnh vực khác.
