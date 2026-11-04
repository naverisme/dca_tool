# Bộ tài liệu kỹ thuật · <Tên sản phẩm / Dự án>

| Thuộc tính | Chi tiết |
| --- | --- |
| **Mục tiêu bộ tài liệu** | <Tài liệu hóa toàn diện hệ thống từ định nghĩa bài toán, yêu cầu, kiến trúc tới kế hoạch giao việc> |
| **Phạm vi phiên bản** | <Mô tả phiên bản / Milestone mục tiêu> |
| **Tiêu chuẩn áp dụng** | DCA 8 Trụ Cột Kỹ Nghệ (Profile standard-v2) |
| **Trạng thái** | Nháp / Chờ duyệt / Đã duyệt |
| **Ngày cập nhật** | YYYY-MM-DD |

---

## Danh mục 8 Trụ Cột Kỹ Nghệ

| STT | Trụ Cột | Nội dung tóm lược | Tài liệu chi tiết |
|:---:|---|---|---|
| **01** | **Định nghĩa sản phẩm** | Chân dung người dùng, bài toán cốt lõi, phạm vi phiên bản đầu và mục tiêu đo lường được (`GOAL-xxx`). | [01-product/](01-product/)<br>• [Tổng quan & Mục tiêu](01-product/overview.md)<br>• [Phạm vi & Giới hạn](01-product/scope.md)<br>• [Thuật ngữ](01-product/glossary.md) |
| **02** | **Ngữ cảnh & Kịch bản sử dụng** | Các tác nhân tương tác, sơ đồ ngữ cảnh, ca sử dụng đầu-cuối (`UC-xxx`) và luồng nghiệp vụ. | [02-scenarios/](02-scenarios/)<br>• [Ngữ cảnh hệ thống](02-scenarios/context.md)<br>• [Ca sử dụng & Ngoại lệ](02-scenarios/use-cases.md)<br>• [Luồng công việc nghiệp vụ](02-scenarios/workflows.md) |
| **03** | **Đặc tả yêu cầu** | Danh mục yêu cầu chức năng (`REQ-FR-xxx`), phi chức năng (`REQ-NFR-xxx`), quy tắc nghiệp vụ (`BR-xxx`) và ma trận phân quyền. | [03-requirements/](03-requirements/)<br>• [Đặc tả SRS](03-requirements/srs.md)<br>• [Quy tắc nghiệp vụ](03-requirements/business-rules.md)<br>• [Ma trận phân quyền](03-requirements/permissions.md) |
| **04** | **Thiết kế trải nghiệm / Vận hành** | Điểm chạm tương tác (UI màn hình, lệnh CLI hoặc tín hiệu phần cứng), luồng điều hướng và trạng thái phản hồi. | [04-experience/](04-experience/)<br>• [Giao diện tương tác](04-experience/screens.md)<br>• [Luồng điều hướng / Vận hành](04-experience/navigation.md)<br>• [Trạng thái tương tác](04-experience/interaction-states.md) |
| **05** | **Kiến trúc & Hợp đồng** | Ranh giới phân rã module (`MOD-xxx`), quyền sở hữu dữ liệu, mô hình ERD, hợp đồng API/giao thức (`CTR-xxx`) và quyết định kỹ thuật (`ADR-xxx`). | [05-architecture/](05-architecture/)<br>• [Kiến trúc tổng thể](05-architecture/system.md)<br>• [Phân rã module](05-architecture/modules.md)<br>• [Mô hình dữ liệu](05-architecture/data-model.md)<br>• [Hợp đồng giao tiếp](05-architecture/contracts.md)<br>• [Quyết định kỹ thuật ADR](05-architecture/decisions.md) |
| **06** | **Kế hoạch kiểm chứng** | Chiến lược đo kiểm, danh mục ca kiểm chứng nghiệm thu (`TC-xxx`) và tiêu chí hoàn thành nghiệm thu (DoD). | [06-verification/](06-verification/)<br>• [Chiến lược kiểm chứng](06-verification/test-strategy.md)<br>• [Ca thử nghiệm thu](06-verification/acceptance-tests.md)<br>• [Tiêu chí hoàn thành DoD](06-verification/definition-of-done.md) |
| **07** | **Bảng truy vết** | Ma trận đối soát 2 chiều giữa mục tiêu ↔ yêu cầu ↔ thiết kế ↔ kiểm thử; báo cáo phân tích lỗ hổng. | [07-traceability/](07-traceability/)<br>• [Ma trận truy vết 2 chiều](07-traceability/matrix.md)<br>• [Phân tích lỗ hổng](07-traceability/gap-analysis.md) |
| **08** | **Kế hoạch triển khai & Phiếu giao việc** | Kế hoạch triển khai DAG, danh mục phiếu giao việc (`TASK-xxx`) với whitelist file được sửa và tiêu chuẩn sẵn sàng code. | [08-delivery/](08-delivery/)<br>• [Lộ trình & Phụ thuộc DAG](08-delivery/plan.md)<br>• [Phiếu giao việc](08-delivery/task-packages.md)<br>• [Sẵn sàng lập trình](08-delivery/readiness.md) |

---
> *Lưu ý: Chỉ liệt kê các file thực sự đã được tạo và có nội dung. Nếu còn câu hỏi kỹ thuật chưa chốt, vui lòng kiểm tra file `docs-clarifications.md` ngang hàng với thư mục `docs/`.*
