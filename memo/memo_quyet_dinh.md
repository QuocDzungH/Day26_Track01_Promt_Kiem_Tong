# MEMO QUYẾT ĐỊNH ÁP DỤNG AI

**Dự án:** Trợ lý AI tra cứu quy trình & chính sách nội bộ<br>
**Nhóm:** Promt Kiếm Tông (`Day26_Track01_Promt_Kiem_Tong`)<br>
**Thành viên:** Trần Đình Hinh (`2A202602399`), Hoàng Quốc Dũng (`2A202602523`), Đinh Xuân Quyền (`2A202602358`)<br>
**Ngày lập:** 14/10/2026 · **Phiên bản:** v2

## 1. Vấn đề và nguyên nhân gốc

Phạm vi phân tích là trợ lý AI phục vụ 25 chuyên viên Vận hành & Hỗ trợ khách hàng, với vấn đề người dùng vẫn tìm file hoặc hỏi đồng nghiệp. Cấp tài khoản là **deployment**; quay lại dùng là **usage**. **Adoption** đòi hỏi thay đổi workflow, trách nhiệm, kiểm soát, hành vi và đo lường.

| Phạm vi: ba quy trình liên kết | Đầu vào → đầu ra | Owner kết quả |
| :--- | :--- | :--- |
| Tra cứu và kiểm chứng chính sách | Câu hỏi → điều khoản còn hiệu lực đã kiểm chứng | Chuyên viên vận hành |
| Xử lý yêu cầu và ngoại lệ | Kết quả kiểm chứng/ca chưa đủ căn cứ → phản hồi được duyệt/ticket chuyên viên chính | Chủ quy trình Vận hành; chuyên viên chính nhận ngoại lệ |
| Báo lỗi và cập nhật tài liệu | Báo lỗi/văn bản mới → phiên bản được duyệt, kiểm tra lại, đóng phản hồi | Data Owner; QA xác nhận bản sửa |

Hai giả thuyết nguyên nhân gốc cần kiểm tra:

1. **Nguồn thiếu quản trị/kiểm chứng:** thiếu owner, hiệu lực, kiểm tra trích nguồn và vòng phản hồi (Gartner-Lite: Readiness, Absorption).
2. **Workflow chưa rõ trách nhiệm và bàn giao:** nhân viên ngại dùng vì chưa biết ai kiểm/nhận ca lỗi (Mollick; ADKAR: Desire).

## 2. Framework và bằng chứng

Gartner-Lite là **khung rút gọn của bài lab**, không phải mô hình chuẩn quốc tế độc lập. Ba cách nhìn cùng dẫn tới giải pháp: quản trị nguồn → người kiểm và bàn giao → giảm trở ngại sử dụng → phản hồi và đo kết quả.

| Framework | Nhận định cần kiểm tra | Kiểm tra / giải pháp |
| :--- | :--- | :--- |
| Gartner-Lite — Direction | Mục tiêu giảm công sức tra cứu, baseline chưa xác nhận | Chủ quy trình xác nhận tác vụ, nguồn đo và mục tiêu ở Gate 30. |
| Gartner-Lite — Readiness | Tài liệu phân mảnh, thiếu Data Owner | Kiểm kê phiên bản/hiệu lực, quyền truy cập, ngân sách và người hỗ trợ; chỉ nạp nguồn được duyệt. |
| Gartner-Lite — Absorption | Thiếu phản hồi và hỗ trợ | Bổ nhiệm owner vận hành, hàng đợi hỗ trợ và lịch rà soát lỗi hằng tuần. |
| Mollick | Người duyệt và điểm bàn giao chưa rõ | AI tìm/tóm tắt; người kiểm nguồn, duyệt kết quả/ngoại lệ. Chỉ tự động tạo/định tuyến ticket rủi ro thấp, có log, kiểm thử và đường xử lý lỗi. |
| ADKAR | Desire có thể nghẽn vì thiếu tin cậy; các yếu tố khác chưa đo | Phỏng vấn đủ 5 yếu tố; bổ sung hướng dẫn khi nên/không nên dùng, thực hành có hỗ trợ và phản hồi. Đào tạo riêng lẻ chưa đủ. |

**Bằng chứng tham khảo:** [OpenAI — Morgan Stanley uses AI evals to shape the future of financial services](https://openai.com/index/morgan-stanley/) (truy cập 16/10/2026) mô tả đánh giá trước triển khai, chuyên gia chấm câu trả lời, QA hồi quy và người kiểm đầu ra. Suy luận áp dụng: cần kiểm thử nguồn và cơ chế người kiểm trước mở rộng.

**Kế hoạch đo baseline:** thu thập log tác vụ, kiểm tra mẫu câu trả lời và phỏng vấn ngắn theo ADKAR trong giai đoạn 0–30 ngày. Mỗi tập đo ghi rõ thời gian, mẫu số, định nghĩa chỉ số và người phụ trách; dữ liệu công khai được tổng hợp, ẩn danh.

## 3. Thay đổi sau phản biện: đối chiếu v1 → v2

Đối chiếu dashboard v1 với v2 sau phản biện chéo với Nhóm 05:

| Hạng mục | V1 | V2 | Góp ý phản biện |
| :--- | :--- | :--- | :--- |
| Chất lượng thay cho activity | Số prompt/ngày, tỷ lệ Like | Bỏ hai chỉ số này; thêm trích nguồn đúng và hoàn tất không hỏi lại/không phải sửa | Prompt cao không chứng minh chất lượng; Like là cảm nhận. |
| Rủi ro và bàn giao | Chưa có chỉ số handoff | Ca cần chuyển có ticket đủ ngữ cảnh, đúng người nhận, có SLA | Cần điểm bàn giao khi thiếu nguồn/câu hỏi phức tạp. |
| Nguồn đo năng suất | Thời gian tự khai, giờ tiết kiệm lý thuyết | Log riêng bước tra cứu; giờ tiết kiệm ròng sau QA/làm lại/hỗ trợ | Nguồn đo phải kiểm tra được. |
| Ownership và hành động | Nhắc dùng, hướng dẫn, họp xem xét | Data Owner, QA, SLA 24/48 giờ, điều kiện sửa/dừng | Hành động phải có owner và thời hạn. |

## 4. Quyết định

**SỬA — giữ phạm vi pilot, đo baseline và hoàn thiện nguồn/kiểm soát trước mở rộng.**

Quyết định mở rộng dựa trên baseline, chất lượng và giá trị đo được. Mục tiêu giá trị là **120 giờ tiết kiệm ròng/tháng**, được đánh giá cùng các điều kiện chất lượng và bàn giao.

- **Tiếp tục:** đồng thời đủ bằng chứng và đạt mọi điều kiện gate kế tiếp.
- **Sửa:** thiếu dữ liệu hoặc bất kỳ mục tiêu/nguồn lực nào; ghi owner và hạn xử lý, đo lại. Hết 30/60/90 ngày không tự qua gate.
- **Tạm dừng luồng bị ảnh hưởng ngay:** lộ dữ liệu/sai quyền hoặc sai chính sách nghiêm trọng; Chủ quy trình phối hợp Data Owner/AI Tech Lead xử lý, QA thử lại trước khi mở.
- **Đề xuất dừng pilot:** không thể khắc phục quyền/nguồn lực, hoặc giờ tiết kiệm ròng ≤0 trong 4 tuần đủ mẫu sau một vòng sửa; Chủ quy trình trình người có thẩm quyền quyết định. Không dùng login để bù cho chất lượng/giá trị không đạt.

## 5. Lý do, bước tiếp theo và owner

### AS-IS / TO-BE và kiến trúc tin cậy

| Bước | AS-IS | TO-BE đề xuất | Owner / bàn giao |
| :--- | :--- | :--- | :--- |
| Tra cứu | Tìm nhiều file/hỏi người có kinh nghiệm | Ghi mã tác vụ và thời gian; AI chỉ tìm nguồn được phép | Chuyên viên vận hành; AI hỗ trợ |
| Kiểm chứng | Khó biết bản còn hiệu lực | Link, điều khoản, hiệu lực/phiên bản; người mở nguồn đối chiếu | Chuyên viên giữ quyền duyệt; mâu thuẫn chuyển chuyên viên chính |
| Dùng / chuyển | Chưa rõ trách nhiệm và đường chuyển | Chỉ gửi nội dung đã duyệt; thiếu/mâu thuẫn/hết hiệu lực nguồn, ngoài phạm vi hoặc nghi sai → ticket có câu hỏi, nguồn và lý do | Chuyên viên chính nhận trong 4 giờ làm việc; quá hạn báo Chủ quy trình |
| Phản hồi | Thiếu vòng phản hồi rõ | Ghi lỗi → Data Owner duyệt bản sửa → AI Tech Lead cập nhật → QA kiểm lại → báo người gửi | Không tự nạp phản hồi thành tri thức khi chưa duyệt |

Chuỗi: **Nguồn → Trích nguồn → QA mẫu → Chuyển người → Phản hồi**. Người dùng kiểm 100% kết quả trước khi dùng. QA độc lập lấy ngẫu nhiên ≥50 câu trả lời/tuần (ít hơn thì kiểm toàn bộ), đồng thời kiểm riêng toàn bộ ca lỗi/chuyển giao. Không trộn ca rủi ro được chọn thêm vào mẫu ngẫu nhiên tính tỷ lệ trích nguồn. QA rà cả ca không chuyển để phát hiện bỏ sót.

Điều kiện dùng AI: tài liệu trong phạm vi, có quyền truy cập và còn hiệu lực; AI không tự gửi khách hàng. Chuyển người theo dấu hiệu kiểm tra được và phản ánh người dùng; không dựa vào điểm tự tin do mô hình tự khai.

Readiness: Data Owner duyệt trước nạp, kiểm hiệu lực thứ Sáu hằng tuần và khi có thay đổi; sửa khẩn trong 24 giờ làm việc hoặc khóa nguồn bị ảnh hưởng. Thử quyền theo vai trò và khả năng thu hồi quyền. Chủ quy trình chốt người hỗ trợ, hạn mức chi phí và nơi lưu log; chưa duyệt thì chưa qua Gate 30.

### Định nghĩa chỉ số và giá trị

[Dashboard v2](../dashboard/dashboard_hanh_dong_v2.xlsx) có 6 chỉ số ở 5 tầng; sheet “Định nghĩa đo” ghi công thức, mẫu, kỳ đo và xử lý thiếu dữ liệu. Baseline được thu thập và mục tiêu được Chủ quy trình phê duyệt tại Gate 30.

| Chỉ số | Công thức / nguồn | Mục tiêu |
| :--- | :--- | :--- |
| Mức dùng trong workflow | Người có ≥1 tác vụ AI gắn ticket / người có tác vụ đủ điều kiện trong tuần; log tác vụ + lịch phân công | ≥85% ở Gate 60/90; chỉ phản ánh usage |
| Hành vi | Tác vụ AI đã duyệt, không hỏi thêm/không phải sửa trong 2 ngày làm việc / toàn bộ tác vụ AI đủ thời gian theo dõi; log + khảo sát đối chiếu | ≥80% ở Gate 60/90 |
| Năng suất | Trung bình phút lao động chủ động của mọi người từ bắt đầu tra cứu đến kết quả được duyệt, cộng các lượt chuyển/làm lại trong 2 ngày; log từng đoạn | ≤3,0 phút ở Gate 60/90; không dùng thời gian toàn bộ ticket |
| Trích nguồn (product) | Câu trả lời đúng nội dung/điều khoản, link có quyền mở, nguồn còn hiệu lực / câu trả lời chính sách trong mẫu QA ngẫu nhiên | ≥95% Gate 30; ≥98% Gate 60/90 |
| Bàn giao (product) | Ca cần chuyển có ticket đủ ngữ cảnh, đúng người và được nhận trong 4 giờ làm việc / ca cần chuyển phát hiện qua log + QA | 100%; không có ca thì N/A, báo riêng bộ thử |
| Giờ tiết kiệm ròng | (Tổng phút baseline của tác vụ tương đương − phút thực tế kể cả chuyển/làm lại − phút QA/bảo trì/hỗ trợ tăng thêm) / 60 | ≥120 giờ/tháng ở Gate 60/90; không cộng trùng chi phí đã tính trong tác vụ |

Ví dụ tính khả thi với giả định thời gian giảm từ 8,5 xuống 3,0 phút: tiết kiệm gộp 5,5 phút/lượt; cần ít nhất **1.310 lượt/tháng** để đạt 120 giờ trước công sức bổ sung. Với 25 người và 20 ngày làm việc giả định, khoảng 2,62 lượt/người/ngày. Sau QA/bảo trì cần khối lượng lớn hơn; Gate 30 phải kiểm lưu lượng thật. Giờ tiết kiệm không đồng nghĩa tiền mặt/ROI; đánh giá tài chính cần chi phí và đơn giá được duyệt.

### Gate 30–60–90

| Gate | Owner chịu trách nhiệm | Bằng chứng và điều kiện chuyển | Khi không đạt |
| :--- | :--- | :--- | :--- |
| **0–30: chứng minh vấn đề/readiness** | Chủ quy trình Vận hành; Data Owner, QA, AI Tech Lead thực hiện | Case thực tế; phạm vi/nguồn; owner; quyền và hạn mức chi phí được duyệt; baseline ≥50 lượt thủ công tương đương; ≥100 câu thử gồm ≥20 ca cần chuyển; trích nguồn đúng ≥95%; bàn giao đúng 100% ca thử; không lỗi nghiêm trọng chưa xử lý | Sửa/đo tiếp, chưa mở pilot AI trong workflow. Thiếu mẫu phải kéo dài thu thập. |
| **31–60: chứng minh chất lượng/hành vi/giá trị** | Chủ quy trình Vận hành; QA độc lập xác nhận | ≥50 tác vụ đủ theo dõi/tuần trong 2 tuần liên tiếp; QA ngẫu nhiên ≥50 câu/tuần hoặc toàn bộ nếu ít hơn; đủ một tháng tính giờ ròng. Đồng thời dùng ≥85%, hành vi ≥80%, thời gian ≤3,0 phút, trích nguồn ≥98%, bàn giao 100%, giờ ròng ≥120/tháng; không lỗi nghiêm trọng chưa xử lý | Thiếu mục tiêu/mẫu → sửa, đo lại. Không có ca bàn giao thật: ghi N/A và bộ thử đạt, chưa tuyên bố tỷ lệ thực tế. |
| **61–90: quyết định mở rộng** | Chủ quy trình trình Ban Điều hành; Data Owner/QA/AI Tech Lead bàn giao | Duy trì mọi mục tiêu Gate 60 trong 4 tuần liên tiếp với cùng yêu cầu mẫu; đủ một tháng giờ ròng; chốt owner vận hành, hỗ trợ, quyền và ngân sách phạm vi mới | Đạt → đề xuất mở rộng từng đợt sau phê duyệt. Không đạt → giữ/sửa hoặc đề xuất dừng theo §4. |

Phân công nhóm: Trần Đình Hinh phụ trách chẩn đoán và quyết định; Hoàng Quốc Dũng phụ trách workflow, nguồn và gate; Đinh Xuân Quyền phụ trách cách đo, dashboard và memo. Owner vận hành được phân công tại Gate 30.

**Bước tiếp theo:** Chủ quy trình và Data Owner khóa danh mục nguồn, phân công QA và người nhận ngoại lệ; triển khai thu thập baseline theo kế hoạch 0–30 ngày.
