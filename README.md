# TÊN BÀI TẬP: Viết Acceptance Criteria & Definition of Done cho User Story

## 1. Acceptance Criteria cho Story 1

**User Story 1:** "Là một độc giả, tôi muốn đặt mượn online một cuốn sách đang có sẵn để tôi không mất công đến thư viện rồi mới biết sách đã có người mượn."

| Story | AC# | Loại (Happy/Negative/Edge/Ràng buộc nghiệp vụ) | Given | When | Then |
|---|---|---|---|---|---|
| Story 1 | 1 | Happy Path | Độc giả đã đăng nhập vào hệ thống và tìm thấy cuốn sách "A" đang có sẵn. | Độc giả nhấn nút "Đặt mượn". | Hệ thống hiển thị thông báo "Bạn đã đặt mượn thành công cuốn sách A. Vui lòng đến nhận trong vòng 48 giờ."<br>And trạng thái của cuốn sách "A" chuyển sang "Đã đặt mượn". |
| Story 1 | 2 | Negative Case | Độc giả đã đăng nhập và tìm thấy cuốn sách "B" hiện không có sẵn (đã được mượn hết hoặc đã có người khác đặt giữ chỗ). | Độc giả nhấn nút "Đặt mượn". | Hệ thống hiển thị thông báo "Cuốn sách B hiện không có sẵn để đặt mượn. Vui lòng thử lại sau."<br>And trạng thái của cuốn sách "B" không thay đổi. |
| Story 1 | 3 | Edge Case | Độc giả đã đăng nhập và đang có một lượt đặt mượn thành công cho cuốn sách "C" đang trong thời gian giữ chỗ 48 giờ. | Độc giả tìm kiếm và nhấn nút "Đặt mượn" lại cuốn sách "C". | Hệ thống hiển thị thông báo "Bạn đã có một lượt đặt mượn cho cuốn sách này đang chờ xử lý."<br>And không tạo thêm lượt đặt mượn mới. |

**Câu hỏi làm rõ cho Product Owner (Story 1):**
*   Khi độc giả đặt mượn thành công, hệ thống có cung cấp mã đặt mượn/mã số sách để độc giả đến thư viện nhận không?

## 2. Acceptance Criteria cho Story 2

**User Story 2:** "Là một độc giả, tôi muốn nhận thông báo khi sách tôi đặt trước đã có sẵn để tôi kịp đến nhận sách trước khi hết thời gian giữ chỗ."

| Story | AC# | Loại (Happy/Negative/Edge/Ràng buộc nghiệp vụ) | Given | When | Then |
|---|---|---|---|---|---|
| Story 2 | 1 | Happy Path | Độc giả đã đặt mượn thành công cuốn sách "D" và còn trong thời gian giữ chỗ 48 giờ. | Hệ thống đã ghi nhận việc đặt mượn thành công. | Độc giả nhận được thông báo qua email (Giả định) với nội dung "Cuốn sách D của bạn đã sẵn sàng để nhận. Vui lòng đến thư viện trong vòng 48 giờ kể từ khi đặt mượn."<br>And thông báo này được gửi ngay lập tức sau khi đặt mượn thành công (Giả định). |
| Story 2 | 2 | Negative Case | Độc giả đã đặt mượn cuốn sách "E" nhưng không đến nhận và đã quá 48 giờ. | Hệ thống đã tự động hủy lượt đặt mượn cho cuốn sách "E". | Độc giả không nhận được thông báo nhắc nhở về việc nhận sách E nữa. |
| Story 2 | 3 | Edge Case | Độc giả đã đặt mượn cuốn sách "F" và chỉ còn 6 giờ (Giả định) trước khi hết thời gian giữ chỗ 48 giờ. | Hệ thống kiểm tra và phát hiện lượt đặt mượn của độc giả F sắp hết hạn. | Độc giả nhận được thông báo nhắc nhở qua email/ứng dụng: "Lượt đặt mượn sách F của bạn sẽ hết hạn sau 6 giờ nữa. Vui lòng đến nhận sách sớm."<br>And thông báo này chỉ được gửi một lần duy nhất cho lượt đặt mượn đó (Giả định). |

**Câu hỏi làm rõ cho Product Owner (Story 2):**
*   Thông báo sẽ được gửi qua những kênh nào (email, SMS, thông báo trong ứng dụng)?
*   Thời điểm gửi thông báo là khi nào? Ngay khi đặt mượn thành công, hay gần hết 48 giờ? Cần có mấy lần thông báo?

## 3. Acceptance Criteria cho Story 3

**User Story 3:** "Là một thủ thư, tôi muốn giới hạn số sách một độc giả được mượn cùng lúc để tránh tình trạng một người giữ hết sách."

| Story | AC# | Loại (Happy/Negative/Edge/Ràng buộc nghiệp vụ) | Given | When | Then |
|---|---|---|---|---|---|
| Story 3 | 1 | Happy Path (Ràng buộc nghiệp vụ) | Độc giả đang có 2 cuốn sách đang mượn và hệ thống quy định giới hạn tối đa là 5 cuốn/độc giả (Giả định). | Độc giả cố gắng đặt mượn cuốn sách thứ 3. | Hệ thống cho phép độc giả đặt mượn cuốn sách thứ 3 thành công.<br>And tổng số sách đang mượn và đặt mượn của độc giả là 3 (dưới giới hạn). |
| Story 3 | 2 | Negative Case (Ràng buộc nghiệp vụ) | Độc giả đang có 5 cuốn sách đang mượn/đặt mượn (đạt giới hạn tối đa là 5 cuốn/độc giả - Giả định). | Độc giả cố gắng đặt mượn thêm một cuốn sách khác. | Hệ thống hiển thị thông báo "Bạn đã đạt giới hạn số sách được mượn/đặt mượn. Vui lòng trả sách hoặc đợi lượt đặt mượn cũ hết hạn để có thể đặt thêm."<br>And hệ thống không cho phép đặt mượn cuốn sách mới. |
| Story 3 | 3 | Edge Case | Độc giả đang có 4 cuốn sách đang mượn/đặt mượn và hệ thống quy định giới hạn tối đa là 5 cuốn/độc giả (Giả định). | Độc giả cố gắng đặt mượn cuốn sách thứ 5. | Hệ thống cho phép độc giả đặt mượn cuốn sách thứ 5 thành công.<br>And tổng số sách đang mượn và đặt mượn của độc giả là 5 (đạt giới hạn). |

**Câu hỏi làm rõ cho Product Owner (Story 3):**
*   Giới hạn số lượng sách một độc giả được mượn/đặt mượn cùng lúc là bao nhiêu?
*   Giới hạn này áp dụng cho sách đang mượn, sách đang đặt mượn chờ nhận, hay tổng cả hai loại?

## 4. Definition of Done (DoD) của nhóm

Các tiêu chí sau đây áp dụng cho MỌI Product Backlog Item:
*   Tất cả Acceptance Criteria của User Story đã được đáp ứng và kiểm thử thành công.
*   Mã nguồn đã được review bởi ít nhất một thành viên khác trong nhóm phát triển.
*   Tất cả các bài kiểm thử tự động (Unit Test, Integration Test) liên quan đã được viết và chạy thành công (đạt tỉ lệ bao phủ mã tối thiểu 80% - Giả định).
*   Tính năng đã được triển khai lên môi trường kiểm thử (Staging/Test) và hoạt động ổn định.
*   Không có lỗi nghiêm trọng (Blocker/Critical) nào được phát hiện trong quá trình kiểm thử nội bộ.
*   Tài liệu hướng dẫn sử dụng/tài liệu kỹ thuật (nếu có) đã được cập nhật tương ứng với thay đổi.

## 5. Trả lời câu hỏi về Story 1

**Câu hỏi:** Story 1 đã đạt đủ các AC bạn viết, nhưng code chưa được review theo DoD của nhóm. Story 1 đã được coi là Done chưa? Vì sao?

**Trả lời:** Story 1 CHƯA được coi là "Done". Theo nguyên tắc Scrum, một User Story chỉ thực sự "Done" khi nó đáp ứng TẤT CẢ các tiêu chí trong Definition of Done của nhóm, không chỉ riêng Acceptance Criteria. Việc code chưa được review theo DoD có nghĩa là Story 1 chưa hoàn thành một bước quan trọng trong quy trình đảm bảo chất lượng của nhóm và chưa sẵn sàng để bàn giao hoặc phát hành.