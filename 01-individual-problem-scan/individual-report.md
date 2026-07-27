# 01 — Individual Problem Scan

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại | Viết báo cáo tuần theo cùng một mẫu | PM | 20 phút/tuần |
| 2 | Lặp lại | Cập nhật tiến độ từ Jira sang Notion | PM | Lặp mỗi sprint |
| 3 | Tốn thời gian | Đọc tài liệu dài trước khi review | Reviewer | 45 phút/tài liệu |
| 4 | Tốn thời gian | Tìm lại quyết định cũ trên Slack | Cả team | 10–15 phút/lần |
| 5 | AI có thể tốt hơn | Gợi ý ưu tiên công việc theo deadline | Team member | Priority chưa rõ |
| 6 | AI có thể tốt hơn | Phân công task tự động theo kỹ năng và workload | PM, Team Lead | Phân công mất 20–30 phút/sprint |
| 7 | Pain từ người khác | Nhân viên mới hỏi lại quy trình | Mentor, New hire | Câu hỏi lặp lại |
| 8 | Pain từ người khác | Khách hàng hỏi cùng một câu nhiều lần | Support | Ticket trùng lặp |


## Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
| ----- | ---------------------------------------- | -------------------------------------------------------- | ---------------------------------------------- |
| **1** | Gợi ý ưu tiên công việc theo deadline | Workflow phức tạp, AI có thể phân tích nhiều yếu tố để hỗ trợ ra quyết định | AI có hiểu đúng ngữ cảnh và mức độ ưu tiên của từng task không? |
| **2** | Đọc tài liệu dài trước khi review | Mất nhiều thời gian, workflow rõ, dễ đo hiệu quả | AI có tóm tắt đúng ý chính không? |
| **3** | Tìm lại quyết định cũ trên Slack | Pain xảy ra thường xuyên, AI search có giá trị cao | Dữ liệu có đầy đủ và dễ truy xuất không? |

## Problem Card #1 — Ưu tiên công việc theo deadline

**Problem 1 câu:**
Team member mất nhiều thời gian quyết định nên làm task nào trước khi có nhiều công việc cùng deadline và mức độ ưu tiên khác nhau.

**Actor:**
Team member hoặc PM quản lý nhiều task.

**Thời điểm / bối cảnh:**
Đầu mỗi ngày hoặc sau mỗi sprint planning.

**Current workflow:**

```text
1. Mở Jira/Notion
2. Xem deadline của từng task
3. Kiểm tra dependency với các task khác
4. Trao đổi với PM hoặc đồng đội nếu chưa rõ priority
5. Tự sắp xếp thứ tự công việc
6. Bắt đầu thực hiện
```

**Bottleneck:**
Bước 3–5 — phải cân nhắc nhiều yếu tố (deadline, dependency, mức độ quan trọng), mất khoảng 20–30 phút và dễ ưu tiên sai.

**Impact:**
Mất thời gian lập kế hoạch mỗi ngày, dễ trễ deadline hoặc làm những việc ít quan trọng trước.

**Success metric:**
Giảm thời gian sắp xếp công việc từ 30 phút xuống dưới 5 phút, giảm số task bị trễ deadline.

**Non-AI alternative:**
Đặt quy tắc ưu tiên cố định hoặc gắn Priority thủ công trong Jira.

**AI hypothesis:**
AI phân tích deadline, dependency, workload và lịch làm việc để đề xuất thứ tự ưu tiên phù hợp. Người dùng vẫn quyết định cuối cùng.

**Quick gut:**
Agent.

### Draft current workflow

```text
CURRENT STATE — 30 phút

[1 Mở Jira/Notion: 3']
→ [2 Kiểm tra deadline: 5']
→ [3 Xem dependency: 8']
→ [4 Trao đổi với PM: 7']  <-- bottleneck
→ [5 Sắp xếp priority: 7']
```

### Draft future workflow

```text
FUTURE STATE — 5 phút

[1 AI đọc toàn bộ task: 30s]
→ [2 AI phân tích deadline + dependency: 1']
→ [3 AI đề xuất thứ tự ưu tiên: 30s]
→ [4 Team member review/chỉnh sửa: 2']  <-- human boundary
→ [5 Bắt đầu làm việc: 1']

Fallback: Đề xuất AI không phù hợp → Người dùng tự sắp xếp lại.
```

## Problem Card #2 — Review tài liệu dài

**Problem 1 câu:**
Reviewer mất khoảng 45 phút để đọc tài liệu dài trước khi review, trong đó việc xác định các điểm quan trọng và thiếu sót tốn nhiều thời gian nhất.

**Actor:**
Reviewer hoặc Team Lead chịu trách nhiệm review PRD, proposal hoặc tài liệu thiết kế.

**Thời điểm / bối cảnh:**
Mỗi khi nhận tài liệu mới trước buổi review hoặc phê duyệt.

**Current workflow:**

```text
1. Mở tài liệu
2. Đọc toàn bộ nội dung
3. Đánh dấu các ý chính
4. Kiểm tra yêu cầu thiếu hoặc mâu thuẫn
5. Viết comment và feedback
6. Review lại nhận xét
7. Gửi phản hồi
```

**Bottleneck:**
Bước 2–4 — đọc và tổng hợp nội dung mất khoảng 35 phút, dễ bỏ sót thông tin.

**Impact:**
45 phút/tài liệu cho mỗi reviewer. Review chậm làm kéo dài thời gian phê duyệt và tăng nguy cơ bỏ sót lỗi.

**Success metric:**
Giảm thời gian review từ 45 phút xuống dưới 20 phút, vẫn giữ chất lượng phản hồi.

**Non-AI alternative:**
Chuẩn hóa template tài liệu và checklist review.

**AI hypothesis:**
AI tóm tắt tài liệu, highlight các điểm quan trọng và gợi ý các vấn đề cần review. Reviewer vẫn kiểm tra trước khi gửi.

**Quick gut:**
Workflow.

### Draft current workflow

```text
CURRENT STATE — 45 phút

[1 Mở tài liệu: 2']
→ [2 Đọc toàn bộ: 25']
→ [3 Đánh dấu ý chính: 8']
→ [4 Kiểm tra thiếu sót: 5']  <-- bottleneck
→ [5 Viết comment: 5']
```

### Draft future workflow

```text
FUTURE STATE — 18 phút

[1 Upload tài liệu: 1']
→ [2 AI tóm tắt nội dung: 1']
→ [3 AI highlight rủi ro: 1']
→ [4 Reviewer review + chỉnh sửa: 13']  <-- human boundary
→ [5 Gửi feedback: 2']

Fallback: AI tóm tắt chưa đúng → Reviewer đọc lại toàn bộ.
```

---

## Problem Card #3 — Tìm quyết định cũ trên Slack

**Problem 1 câu:**
Thành viên trong team mất khoảng 10–15 phút để tìm lại các quyết định cũ trên Slack khi cần xác nhận thông tin.

**Actor:**
Tất cả thành viên trong team.

**Thời điểm / bối cảnh:**
Khi cần tra cứu quyết định đã được thống nhất trong các cuộc thảo luận trước.

**Current workflow:**

```text
1. Mở Slack
2. Tìm kiếm bằng từ khóa
3. Mở nhiều cuộc hội thoại
4. Đọc lại các tin nhắn liên quan
5. Xác nhận quyết định
6. Chia sẻ lại cho team
```

**Bottleneck:**
Bước 2–4 — thông tin nằm rải rác ở nhiều kênh và nhiều thời điểm khác nhau.

**Impact:**
10–15 phút mỗi lần tìm kiếm. Team mất thời gian và dễ sử dụng thông tin không chính xác.

**Success metric:**
Giảm thời gian tìm kiếm xuống dưới 2 phút, không tăng số lần hỏi lại trong team.

**Non-AI alternative:**
Lưu toàn bộ decision vào Notion hoặc tạo kênh riêng để ghi quyết định.

**AI hypothesis:**
AI tìm kiếm theo ngữ cảnh, tóm tắt quyết định và dẫn nguồn tin nhắn liên quan.

**Quick gut:**
Agent.

### Draft current workflow

```text
CURRENT STATE — 15 phút

[1 Mở Slack: 1']
→ [2 Search từ khóa: 4']
→ [3 Mở nhiều thread: 5']  <-- bottleneck
→ [4 Đọc lại hội thoại: 3']
→ [5 Xác nhận decision: 2']
```

### Draft future workflow

```text
FUTURE STATE — 2 phút

[1 Hỏi AI: 10s]
→ [2 AI tìm theo ngữ cảnh: 30s]
→ [3 AI tóm tắt + dẫn nguồn: 20s]
→ [4 User kiểm tra kết quả: 1']  <-- human boundary

Fallback: Không tìm thấy → Search thủ công trên Slack.
```

