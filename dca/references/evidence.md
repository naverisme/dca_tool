# Khảo sát và kiểm định bằng chứng

1. Xác định gốc dự án hoặc tập nguồn do người dùng nêu. Với Git, ghi commit, nhánh và thay đổi chưa commit nếu liên quan; với nguồn khác, ghi phiên bản/ngày/định danh khi có. Nêu phần chưa đọc. Không tự theo symlink, submodule, file bí mật hoặc nguồn ngoài phạm vi.
2. Đọc quy ước dự án, tài liệu đã duyệt và quyết định hiện hành trước khi gán thẩm quyền. Không áp dụng thứ bậc nguồn cứng: quyết định đã duyệt chỉ có hiệu lực đúng phiên bản và phạm vi.
3. Tách mệnh đề nguyên tử. Với mỗi mệnh đề ghi nội dung gốc, vị trí nguồn, chủ thể, hành động, đối tượng, điều kiện, thời điểm/phiên bản và trạng thái.
4. Đối chiếu các mệnh đề cùng điều kiện. Trước khi gọi mâu thuẫn, kiểm tra chúng có nói về nháp/bản duyệt, vai trò, môi trường hoặc thời điểm khác nhau không. Phân loại `CONFLICT`, `AMBIGUITY`, `GAP`, `DUPLICATE`, `STALE`, `UNVERIFIED`, `BROKEN_LINK`.
5. Phân biệt “file ghi X”, “X đã được duyệt”, “X đúng trong thực tế” và “phần mềm đang làm X”. Chúng cần bằng chứng khác nhau. Dữ kiện ngoài có thể thay đổi phải kiểm tra tại thời điểm trả lời và ghi ngày; hai bản sao cùng nguồn không là xác nhận độc lập.
6. Dùng `VERIFIED` khi bằng chứng trực tiếp chứng minh **đúng loại mệnh đề đang viết** trong đúng phạm vi, nguồn có thẩm quyền với mệnh đề đó, và không còn mâu thuẫn trọng yếu sau khi đối chiếu nguồn trong phạm vi. Một phát biểu của người dùng xác minh ý định đã nói; một quyết định được duyệt xác minh quy tắc đã chốt; bằng chứng thực nghiệm xác minh kết quả thực nghiệm trong điều kiện đo. Không dùng hai bản sao cùng nguồn để tăng độ chắc chắn. Dùng `INFERRED` khi suy luận có căn cứ; `UNKNOWN` khi thiếu; `CONFLICTING` khi chưa phân xử; `SUPERSEDED` khi có bằng chứng thay thế. Ghi căn cứ, giới hạn và người có quyền quyết định. Không tự nâng trạng thái.
7. Chỉ hỏi câu hỏi thực sự cần để phân xử ý nghĩa hoặc quyền. Nêu hai cách hiểu, nguồn và tác động; tiếp tục phần độc lập và giữ phần phụ thuộc ở trạng thái mở.

**Cổng đưa vào docs:** mệnh đề phải có phạm vi/điều kiện rõ, bằng chứng phù hợp, không bị nguồn có thẩm quyền cùng phạm vi bác bỏ, và đủ nội dung để viết thành đoạn tự hiểu được. Nếu một điểm trọng yếu chưa đạt, để ở khu vực rà soát chứ không viết thành quy tắc trong docs. Gắn nhãn `DCA-checked` cho kết quả đã kiểm theo phạm vi; chỉ dùng `approved` khi có bằng chứng người có quyền phê duyệt.

Ví dụ: Hai file khác nhau về việc giáo viên có xem checklist nhóm không. Kiểm tra cùng lớp, bài, thời điểm và trạng thái duyệt. Nếu còn mâu thuẫn, dẫn cả hai nguồn rồi hỏi người có quyền; không tự sửa ma trận quyền.
