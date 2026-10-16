# BÁO CÁO ÁP DỤNG AI — DAY 26, TRACK 01

**Nhóm:** Promt Kiếm Tông · **Dự án:** Trợ lý AI tra cứu quy trình & chính sách nội bộ · **Ngày thực hiện:** 14/10/2026<br>
**Repo:** `Day26_Track01_Promt_Kiem_Tong` · **Quyết định:** SỬA, hoàn thiện kiểm soát trước khi mở rộng.

## 1. Thành viên và đóng góp

| Họ tên | MSSV | Phần phụ trách | Góp ý đã đưa cho nhóm bạn |
| :--- | :--- | :--- | :--- |
| Trần Đình Hinh (nhóm trưởng) | `2A202602399` | Gartner-Lite; Mollick; phối hợp quyết định cuối | Nhóm 05: số prompt chỉ phản ánh hoạt động; đề xuất đo tỷ lệ tra cứu thành công không cần hỏi lại đồng nghiệp. |
| Hoàng Quốc Dũng | `2A202602523` | AS-IS / TO-BE; kiến trúc tin cậy; gate 30–60–90 | Nhóm 05: bổ sung Data Owner duyệt và cập nhật tài liệu ngay trong giai đoạn 0–30 ngày. |
| Đinh Xuân Quyền | `2A202602358` | ADKAR; dashboard v1/v2; memo | Nhóm 05: thay “họp xem xét” bằng hành động có owner và thời hạn, ví dụ rà soát lỗi trích nguồn trong 48 giờ. |

## 2. Phạm vi

Một trợ lý RAG; nhóm người dùng chính gồm 25 chuyên viên Vận hành & Hỗ trợ khách hàng; ba quy trình liên kết: **tra cứu và kiểm chứng chính sách → xử lý yêu cầu/ngoại lệ → báo lỗi và cập nhật tài liệu**. Vấn đề cần giải quyết: người dùng vẫn quay lại tìm file hoặc hỏi đồng nghiệp thay vì tra cứu trong workflow AI.

## 3. Nguyên nhân gốc và bằng chứng

Hai giả thuyết: **nguồn thiếu quản trị/kiểm chứng** (Gartner-Lite: Readiness), và **trách nhiệm, bàn giao chưa rõ khiến người dùng ngại dùng** (Mollick; ADKAR: Desire). [Case Morgan Stanley](https://openai.com/index/morgan-stanley/) cung cấp bài học về đánh giá, QA và người kiểm tra. Phân tích và kế hoạch đo lường nằm ở [memo](memo/memo_quyet_dinh.md), phần 2.

## 4. Cách làm mới

AI tìm và tóm tắt kèm **link nguồn, điều khoản, ngày hiệu lực**; chuyên viên mở nguồn kiểm tra và duyệt. Thiếu nguồn, nguồn mâu thuẫn/hết hiệu lực, ngoài phạm vi hoặc người dùng nghi sai → chuyển chuyên viên chính kèm ngữ cảnh; Data Owner duyệt bản cập nhật, QA kiểm tra lại. Memo phần 5 ghi AS-IS / TO-BE, QA mẫu, quyền truy cập và owner từng gate.

## 5. Chỉ số ra quyết định

**Product:** trích nguồn đúng — baseline thu thập tại Gate 30, mục tiêu ≥95% ở Gate 30 và ≥98% ở Gate 60/90; nguồn QA + log RAG; owner AI Tech Lead. **Workflow:** thời gian một lượt tra cứu đã kiểm chứng — baseline thu thập tại Gate 30, mục tiêu ≤3,0 phút ở Gate 60/90; nguồn log riêng bước tra cứu; owner Chủ quy trình Vận hành.

[Dashboard v2](dashboard/dashboard_hanh_dong_v2.xlsx) có đủ **6 chỉ số ở 5 tầng**: mức dùng, hành vi, năng suất, trích nguồn, bàn giao và giờ tiết kiệm ròng; mỗi dòng đủ baseline, target, source, owner và hành động khi xấu. Các sheet kèm theo quy định công thức, mẫu đo, gate và kế hoạch thu thập dữ liệu.

## 6. Quyết định và thay đổi so với v1

**SỬA:** xác minh hiện trạng, nguồn và bàn giao trước khi mở rộng. So với [v1](v1/dashboard_hanh_dong_v1.xlsx): (1) thay số prompt/Like bằng kiểm tra trích nguồn và kết quả quy trình; (2) bổ sung chỉ số bàn giao; (3) thay năng suất tự khai bằng log tác vụ, bổ sung SLA và Data Owner. [Memo 5 phần](memo/memo_quyet_dinh.md) và nhật ký trong Excel ghi chi tiết các thay đổi.
