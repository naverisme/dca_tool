# Quy ước tài liệu chuẩn của DCA (Profile standard-v2)

DCA biên soạn dữ liệu thô thành bộ tài liệu kỹ thuật chuẩn theo **8 trụ cột kỹ nghệ hệ thống** cố định. Profile mặc định là `standard-v2` áp dụng đồng nhất cho các dự án phần mềm, hệ thống kỹ thuật và sản phẩm số. 

Cùng một profile phải cho cùng tên folder, file và ranh giới ở mọi dự án. Các thư mục được đánh số thứ tự từ `01-` đến `08-` để bảo đảm thứ tự tuần tự logic trong mọi môi trường (IDE, Git, File Explorer, Agent context). *(DCA cũng hỗ trợ bí danh không tiền tố số như `product/`, `scenarios/`... nếu dự án yêu cầu, nhưng khuyến nghị mặc định chuẩn số để giữ đúng luồng kỹ nghệ).*

---

## 8 Trụ cột tài liệu chuẩn

| STT | Nhóm cố định | Tên trụ cột | Câu hỏi cốt lõi | Đầu ra và ranh giới | Slot tên file cố định |
| --- | --- | --- | --- | --- | --- |
| 1 | `01-product/` | **Định nghĩa sản phẩm** | Xây cho ai, giải quyết vấn đề gì, kết quả mong muốn là gì, phạm vi bản đầu đến đâu? | Danh sách mục tiêu (`GOAL-xxx`) và giới hạn ranh giới để xét từng yêu cầu. | `overview.md`, `scope.md`, `glossary.md` |
| 2 | `02-scenarios/` | **Ngữ cảnh và kịch bản sử dụng** | Ai hoặc hệ thống nào tương tác? Họ thực hiện việc gì từ đầu đến cuối? Các tình huống lỗi là gì? | Các luồng tương tác và ca sử dụng (`UC-xxx`) để rút ra yêu cầu cụ thể. | `context.md`, `use-cases.md`, `workflows.md` |
| 3 | `03-requirements/` | **Đặc tả yêu cầu** | Sản phẩm phải làm gì, theo quy tắc nào, đạt chỉ tiêu nào? | Mỗi yêu cầu có mã riêng (`REQ-xxx`), nguồn gốc và điều kiện kiểm tra. Căn cứ để thiết kế. | `srs.md`, `business-rules.md`, `permissions.md` |
| 4 | `04-experience/` | **Thiết kế trải nghiệm hoặc vận hành** | Người dùng, thiết bị hoặc hệ thống khác tương tác qua những điểm nào? Mỗi thao tác gây ra kết quả gì? | Màn hình, lệnh CLI, tín hiệu hoặc giao diện ngoài cần triển khai tùy loại sản phẩm. | `screens.md`, `navigation.md`, `interaction-states.md` |
| 5 | `05-architecture/` | **Thiết kế kiến trúc và hợp đồng giữa các phần** | Có những thành phần nào, phần nào sở hữu dữ liệu, chúng trao đổi thế nào, lỗi được xử lý ở đâu? | Ranh giới module (`MOD-xxx`), mô hình dữ liệu (ERD), hợp đồng (`CTR-xxx`) và quyết định kỹ thuật (`ADR-xxx`) để chia việc. | `system.md`, `modules.md`, `data-model.md`, `contracts.md`, `decisions.md` |
| 6 | `06-verification/` | **Kế hoạch kiểm chứng** | Làm cách nào chứng minh từng yêu cầu đã đạt? Cần dữ liệu, thiết bị, phép đo hoặc ca thử nào? | Ca kiểm chứng nghiệm thu (`TC-xxx`) và tiêu chí hoàn thành (DoD) cụ thể cho từng gói việc. | `test-strategy.md`, `acceptance-tests.md`, `definition-of-done.md` |
| 7 | `07-traceability/` | **Bảng truy vết** | Mục tiêu nào sinh ra yêu cầu nào? Thiết kế và ca kiểm tra nào đáp ứng yêu cầu đó? | Ma trận truy vết 2 chiều khép kín, phát hiện yêu cầu chưa có thiết kế hoặc chưa có cách kiểm tra. | `matrix.md`, `gap-analysis.md` |
| 8 | `08-delivery/` | **Kế hoạch triển khai và phiếu giao việc** | Việc nào làm trước, việc nào phụ thuộc việc khác, ai được sửa phần nào và bàn giao bằng chứng gì? | Các nhiệm vụ (`TASK-xxx`) đủ rõ ràng, có ranh giới file cho phép sửa và bằng chứng bàn giao để giao cho người hoặc agent code. | `plan.md`, `task-packages.md`, `readiness.md` |

---

## Chi tiết chức năng của từng Slot

### 1. `01-product/` · Định nghĩa sản phẩm
- **`overview.md`**: Bài toán cần giải quyết, đối tượng thụ hưởng (Persona/Target Users), giá trị mang lại, kết quả mong muốn và danh mục mục tiêu cốt lõi với mã định danh ổn định (`GOAL-001`, `GOAL-002`, ...).
- **`scope.md`**: Phạm vi phiên bản đầu (MVP/v1), danh sách hạng mục thực hiện (In-Scope), danh sách loại trừ rõ ràng (Out-of-Scope) và các ràng buộc biên.
- **`glossary.md`**: Bảng thuật ngữ chuyên ngành và khái niệm chuẩn để dùng nhất quán xuyên suốt toàn bộ tài liệu.

### 2. `02-scenarios/` · Ngữ cảnh và kịch bản sử dụng
- **`context.md`**: Ranh giới hệ thống (System Boundary) và mô hình ngữ cảnh, xác định mọi tác nhân bên ngoài (con người, hệ thống ngoài, thiết bị ngoại vi, cron job/scheduler).
- **`use-cases.md`**: Danh mục ca sử dụng chi tiết (`UC-xxx`): tác nhân, tiền điều kiện, luồng thao tác chính (happy path), nhánh rẽ và kịch bản xử lý lỗi/ngoại lệ từ đầu đến cuối.
- **`workflows.md`**: Trình tự luồng công việc nghiệp vụ (Business/Operational Workflows), sự bàn giao giữa các vai trò và hệ thống.

### 3. `03-requirements/` · Đặc tả yêu cầu
- **`srs.md`**: Đặc tả yêu cầu chức năng (FR) và phi chức năng (NFR). Bắt buộc mỗi yêu cầu phải có:
  1. Mã định danh duy nhất: `REQ-FR-xxx`, `REQ-NFR-xxx`.
  2. Nguồn gốc sinh ra: bắt nguồn từ `GOAL-xxx` hoặc `UC-xxx` nào.
  3. Tiêu chí kiểm tra/nghiệm thu định lượng (rõ ràng, đo lường được, không dùng từ ngữ mơ hồ).
- **`business-rules.md`**: Bảng quy tắc nghiệp vụ, công thức tính toán, trạng thái dữ liệu hợp lệ và điều kiện ràng buộc logic (`BR-xxx`).
- **`permissions.md`**: Ma trận phân quyền chi tiết (Actor × Resource × Action × Condition).

### 4. `04-experience/` · Thiết kế trải nghiệm hoặc vận hành
*(Loại sản phẩm quyết định định dạng nội dung: UI cho web/app, CLI cho công cụ dòng lệnh, Tín hiệu/HMI cho phần cứng & IoT)*
- **`screens.md`** (hoặc `interfaces.md`): Điểm tiếp xúc tương tác cụ thể:
  - *Sản phẩm có UI*: Layout màn hình, wireframe, các thành phần trực quan.
  - *Sản phẩm CLI/Backend*: Cú pháp dòng lệnh, cờ tham số (flags), luồng stdin/stdout/stderr, mã thoát (exit codes).
  - *Sản phẩm IoT/Phần cứng*: Bảng điều khiển vật lý (HMI), nút bấm, đèn LED tín hiệu, cổng giao tiếp ngoại vi.
- **`navigation.md`**: Cấu trúc điều hướng, luồng di chuyển giữa các màn hình, menu hoặc các trạng thái vận hành.
- **`interaction-states.md`**: Đặc tả hành vi tại từng điểm chạm khi thao tác: phản hồi tức thì, trạng thái trống (empty), đang tải (loading), lỗi (error), mất mạng/mất tín hiệu, thiếu quyền thao tác.

### 5. `05-architecture/` · Thiết kế kiến trúc và hợp đồng giữa các phần
- **`system.md`**: Ranh giới hệ thống, kiến trúc tổng thể, nguyên tắc phân chia thành phần, quyền sở hữu dữ liệu (**Data Ownership** - module nào độc quyền sở hữu bảng/dữ liệu nào), cơ chế cô lập và xử lý lỗi (fault tolerance, fallback, retry).
- **`modules.md`**: Trách nhiệm từng module (`MOD-xxx`), đầu vào/ra, hướng phụ thuộc (dependency direction, cấm phụ thuộc vòng).
- **`data-model.md`**: Mô hình dữ liệu logic & vật lý (ERD, thực thể, trường dữ liệu, khóa chính/ngoại, quan hệ 1-1, 1-n, n-n, ràng buộc toàn vẹn).
- **`contracts.md`**: Hợp đồng giao tiếp chính thức giữa các phần (`CTR-xxx`): API endpoints (REST/GraphQL/gRPC), schema dữ liệu trao đổi (DTO/JSON schema), sự kiện/thông điệp bất đồng bộ (event topics, payloads, error payloads).
- **`decisions.md`**: Architecture Decision Records (`ADR-xxx`) ghi lại các quyết định kỹ thuật then chốt, bối cảnh, lý do lựa chọn và hệ quả đánh đổi.

### 6. `06-verification/` · Kế hoạch kiểm chứng
- **`test-strategy.md`**: Chiến lược kiểm chứng tổng thể: các cấp độ kiểm thử (Unit, Integration, E2E, Performance, Security), môi trường thử nghiệm, công cụ đo kiểm, tập dữ liệu mẫu cần chuẩn bị, thiết bị đo (nếu có phần cứng).
- **`acceptance-tests.md`**: Danh mục ca kiểm chứng nghiệm thu chi tiết (`TC-xxx`):
  1. Ánh xạ trực tiếp tới mã yêu cầu `REQ-xxx`.
  2. Tiền điều kiện (Preconditions).
  3. Các bước thực hiện (Test steps).
  4. Kết quả mong đợi đo lường được (Expected measurable results).
- **`definition-of-done.md`**: Bộ tiêu chí hoàn thành nghiệm thu (DoD) định lượng cho từng gói việc trước khi coi là hoàn tất.

### 7. `07-traceability/` · Bảng truy vết
- **`matrix.md`**: Ma trận truy vết 2 chiều (Bidirectional Traceability Matrix):
  `Mục tiêu (GOAL-xxx)` $\longleftrightarrow$ `Yêu cầu (REQ-xxx)` $\longleftrightarrow$ `Thiết kế/Module/Hợp đồng (MOD/CTR-xxx)` $\longleftrightarrow$ `Ca kiểm chứng (TC-xxx)`.
- **`gap-analysis.md`**: Báo cáo phân tích lỗ hổng:
  - Yêu cầu mồ côi (yêu cầu chưa có module thiết kế nào đáp ứng).
  - Yêu cầu mù kiểm thử (yêu cầu chưa có ca kiểm chứng tương ứng).
  - Thiết kế thừa / không rõ nguồn gốc (thành phần kiến trúc không ánh xạ về bất kỳ mục tiêu/yêu cầu nào).

### 8. `08-delivery/` · Kế hoạch triển khai và phiếu giao việc
- **`plan.md`**: Lộ trình triển khai (Roadmap / Milestones), đồ thị phụ thuộc (DAG) giữa các gói việc: việc nào làm trước, việc nào phụ thuộc việc khác.
- **`task-packages.md`**: Danh mục phiếu giao việc chi tiết (`TASK-xxx`):
  1. Mã task & Mục tiêu thực hiện cụ thể.
  2. Yêu cầu & Hợp đồng liên quan (`REQ-xxx`, `CTR-xxx`).
  3. **Ranh giới file được phép chỉnh sửa**: Whitelist các file/thư mục cụ thể mà người hoặc AI agent được phép can thiệp (chống xung đột code chéo hoặc sửa ngoài phạm vi).
  4. Ràng buộc phụ thuộc (Task tiền đề cần xong trước).
  5. **Bằng chứng bàn giao bắt buộc**: Deliverables/Evidence kiểm chứng được (PR link, unit test pass 100%, commit hash, test execution log, benchmark report).
- **`readiness.md`**: Bảng kiểm tra sẵn sàng lập trình (Coding Readiness Checklist) chứng minh bộ tài liệu đã đạt chuẩn trước khi giao việc cho dev hoặc agent code.

---

## Nguyên tắc áp dụng

1. `docs/README.md` luôn là mục lục tổng quan có mục tiêu bộ tài liệu, phạm vi nội dung và bảng liên kết nội bộ tới 8 trụ cột.
2. Chỉ tạo nhóm và file có thông tin đủ để viết thành nội dung hữu ích. Không tạo placeholder rỗng.
3. Một quy tắc/yêu cầu chỉ có một nơi lưu chính; các chỗ khác trích dẫn bằng mã định danh (`REQ-xxx`, `GOAL-xxx`, `TASK-xxx`) và liên kết nội bộ.
4. **Không đưa dấu vết file thô ra đầu ra**: Tuyệt đối không trích dẫn đường dẫn file thô, metadata khảo sát vào `docs/`. Bảng truy vết tại `07-traceability/` là truy vết kỹ thuật nội bộ giữa Mục tiêu, Yêu cầu, Thiết kế và Kiểm chứng, không phải log quét file thô.
