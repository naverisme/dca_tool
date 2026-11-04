# Nháp và ghi tài liệu

`organize`, `normalize`, `diagram`, `sync` chỉ xem trước mặc định. Lưu nháp khi người dùng yêu cầu `--draft`; không ghi vào tệp đích.

1. Xác định tệp đích, phạm vi, mốc nguồn và nội dung hiện tại. Các thay đổi nghĩa chưa chốt ở sổ phát hiện, không lẫn vào văn bản đã duyệt.
2. Lưu bản nháp ở nơi rà riêng, kèm manifest ghi đường dẫn đích, hash nội dung đích lúc lập nháp hoặc `absent`, hash bản nháp, mốc nguồn và các phát hiện liên quan. Tính ID từ nội dung manifest đã cố định; không tự bịa ID hay hash.
3. Cho người dùng xem diff theo tệp, quyết định còn thiếu, ID và phạm vi `apply`. Không gọi nháp là tài liệu chính.
4. Với `apply <draft-id>`, kiểm tra lại ID, hash, mốc, đường dẫn và quyền ghi; nếu nguồn hoặc đích đổi, dừng và báo bản nháp đã cũ. Chỉ ghi các tệp đã chọn, giữ nội dung ngoài phạm vi.
5. Kiểm tra lại nội dung, liên kết, ID và bảng/sơ đồ bị ảnh hưởng. Báo tệp đã đổi và phát hiện mở. Không tự commit, đẩy Git, chỉnh mã nguồn.

Nếu người dùng yêu cầu sửa trực tiếp với đích và phạm vi rõ, kiểm tra trước/sau tương tự và vẫn không tự quyết định thay đổi nghĩa.
