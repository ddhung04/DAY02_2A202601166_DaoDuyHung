# Group Report — Day 02

## Thành viên nhóm

| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|-----|-----------|-------------|--------------------|
| 1   | Nguyễn Minh Đức| 2A202601946 | Phản biện chính; điều hướng scope; giải quyết khía cạnh rủi ro |
| 2   | Phạm Hoàng Nam | 2A202601442 | Đề xuất candidate chính (SQL Query & Visualization from Natural Language); xây dựng deck/script thuyết trình |
| 3   | Hoàng Văn Thành | 2A202601428 | Vẽ workflow trước/sau |
| 4   | Đào Duy Hưng (tôi)| 2A202601166 | Research giải pháp/tool đã có |
| 5   | Trần Văn Thắng | 2A202602003 | Tổng hợp Problem Statement + chuẩn bị pilot plan |

---

## Nhật ký hội tụ

| Cluster | Candidate | Pattern chung | Chọn? |
|---|---|---|---|
| SQL/Data analysis automation | SQL Query & Visualization from Natural Language | Tự động hóa truy vấn + trình bày dữ liệu cho stakeholder | ✅ Được chọn |
| Prioritization / ranking | Deadline ranking (xếp hạng/ưu tiên deadline từ nhiều nguồn) | Tổng hợp và sắp xếp thông tin theo mức độ ưu tiên | ❌ Không chọn |
| Tra cứu thông tin cũ | Problem Card #2 của tôi — tìm lại quyết định cũ trong chat nhóm học (Discord/Zalo) | Cùng pattern với candidate của một thành viên khác trong nhóm | ❌ Không chọn |
| Đời sống cá nhân | Mất thời gian lấy vé/gửi xe | Thao tác lặp lại, tốn thời gian chờ, phạm vi hẹp | ❌ Không chọn |

Nhóm chọn: **SQL Query & Visualization from Natural Language** (tự động hóa việc viết SQL + tạo visualization khi stakeholder hỏi data) — ý tưởng do Phạm Hoàng Nam đề xuất.

Vì sao chọn:

- Workflow rõ, dễ hiểu — dễ nêu bottleneck cụ thể (viết SQL, tạo visualization).
- Điểm mạnh của AI thể hiện rõ trong bài toán này: khả năng linh hoạt xử lý nhiều loại data trong thời gian ngắn, và có thể thiết kế logic truy vấn đảm bảo security (giới hạn schema, tránh lộ dữ liệu nhạy cảm).
- Các hướng khác từng được đề xuất nhắm vào nhiều pain point đa dạng hơn, nhưng đòi hỏi nhiều bước kiểm chứng hơn để xác nhận là pain thật — khó thực hiện trong thời gian lab.

Vì sao không chọn các candidate còn lại:

- **Deadline ranking:** workflow và metric mờ hơn — khó nêu bottleneck cụ thể bằng con số so với SQL/Visualization.
- **Problem Card #2 (tìm lại quyết định cũ trong chat nhóm học):** không còn là pain point thật vì đã có nhiều giải pháp có sẵn để xử lý thủ công (pin tin nhắn, note tổng hợp) — Rule đã đủ giải quyết phần lớn.
- **Mất thời gian lấy vé/gửi xe:** phạm vi hẹp, cá nhân, impact khó mở rộng ra nhiều actor.

---

## Quick validation

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Interview | 3 | 2/3 người xác nhận từng mất 20-40 phút để viết SQL + vẽ chart cho một request ad-hoc | 1 người nói team họ đã có dashboard nên ít gặp trường hợp này | Thu hẹp phạm vi: tập trung vào request không có sẵn trong dashboard, thay vì mọi loại request |
| Survey / poll | 6 | 4/6 từng phải tự viết SQL/tạo chart thủ công theo yêu cầu đột xuất | 2/6 dùng công cụ BI có sẵn nên không thấy đây là vấn đề lớn | Thêm điều kiện: giải pháp chỉ nhắm vào nhóm chưa có BI tool hoặc có nhưng không cover hết use case |
| Log / review / ticket | — | — | — | Chưa tiếp cận được log/ticket thật của một team data analyst cụ thể |

Insight sau validation:

```text
Tín hiệu phản bác (dashboard có sẵn đã đủ cho một phần người dùng) cho thấy phạm vi bài toán hẹp hơn "mọi request ad-hoc". Baseline "30-60 phút/request" và "2-3 requests/ngày" hiện vẫn là ước lượng, chưa có nguồn xác nhận độc lập (phỏng vấn analyst, log ticket, case study có trích dẫn) — cần validate thêm trước khi dùng làm số liệu chính thức.
```

---

## Research giải pháp

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| ChatGPT / Claude | https://openai.com/chatgpt , https://claude.com | Generate SQL từ prompt | Hiểu ngôn ngữ tự nhiên tốt | Không có database access, không tự execute được | Chỉ giải quyết một phần (viết SQL), chưa giải toàn bộ workflow |
| Tableau | https://www.tableau.com/products/tableau-ai | Pre-built dashboard, có tính năng hỏi-đáp bằng ngôn ngữ tự nhiên | Tốt cho báo cáo lặp lại, đã biết trước câu hỏi | Cần analyst setup trước, không xử lý được ad-hoc request mới | Rule/dashboard đủ cho các câu hỏi lặp lại |
| Power BI Q&A | https://learn.microsoft.com/power-bi/natural-language/q-and-a-intro | Natural language → visual | Trải nghiệm hỏi-đáp tự nhiên | Giới hạn trong hệ sinh thái Power BI, chậm với câu hỏi mới | Không phải lựa chọn nếu data nằm ngoài Power BI |
| Manual process (hiện tại) | — | Kiểm soát hoàn toàn, độ chính xác cao | Đáng tin cậy | 30-60 phút/request, không scale được | Baseline để so sánh cải thiện |

Research takeaway:

```text
Các tool có sẵn (Tableau/Power BI) xử lý tốt các câu hỏi lặp lại và đã biết trước — đúng phạm vi của Rule/Workflow. Chúng chỉ thất bại ở phần ad-hoc, câu hỏi mới. Nếu tách được "câu hỏi lặp lại" (dùng Rule/dashboard có sẵn) ra khỏi "câu hỏi ad-hoc thật sự mới" (cần Agent), phạm vi cần Agent có thể nhỏ hơn nhiều so với đề xuất "Agent cho toàn bộ workflow" ban đầu.
```

---

## Workflow before/after

```text
CURRENT STATE — 7 bước, 45 phút

[1 Stakeholder request: 2']
→ [2 Analyst clarify (năm nào, gross/net revenue...): 3']
→ [3 Viết SQL query: 15-20']  <-- bottleneck 1
→ [4 Execute & debug: 5-10']
→ [5 Export data: 2']
→ [6 Tạo visualization: 15-20']  <-- bottleneck 2
→ [7 Gửi cho stakeholder: 2']

FUTURE STATE — 8 bước, 5-7 phút (mục tiêu)

[1 Stakeholder request (natural language): 1']
→ [2 AI hiểu request (NLP): auto]
→ [3 AI query schema: auto]
→ [4 AI generate SQL: 1']
→ [5 AI execute query: 1']
→ [6 AI tạo visualization: 1']
→ [7 Analyst review (verify SQL + chart, có thể sửa/reject): 2-3']  <-- human boundary
→ [8 Gửi cho stakeholder (auto-send sau khi approve): 1']

Fallback: SQL sai → analyst sửa nhanh và chạy lại (vẫn nhanh hơn viết từ đầu).
```

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Tổng thời gian | 30-60 phút | Dưới 5 phút | 90% reduction — mục tiêu chính |
| Số bước | 7 | 8 | Tăng 1 bước nhưng phần lớn là auto |
| Số bước thủ công | 7/7 | 2/8 (clarify ban đầu + review cuối) | Analyst vẫn là gatekeeper |
| Bottleneck chính | Viết SQL (15-20') + Tạo viz (15-20') | Analyst review (2-3') | Bottleneck chuyển từ "làm" sang "kiểm tra" |
| Risk mới | Không có AI hallucination | SQL sai/join sai, lộ dữ liệu nhạy cảm, hiểu sai ý stakeholder | Cần review gate + giới hạn schema hiển thị cho AI |

---

## Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Data analyst xử lý các yêu cầu data ad-hoc từ stakeholder (PM, sales manager, CEO). |
| **Workflow** | Nhận request → clarify → viết SQL → execute/debug → export → tạo visualization → gửi stakeholder. |
| **Bottleneck** | Viết SQL (15-20 phút) và tạo visualization (15-20 phút) — hai bước lặp lại thủ công cho mỗi request. |
| **Impact** | 30-60 phút/request; ước lượng 2-3 request/ngày/analyst → 1-3 giờ/ngày (chưa được validate, xem mục Quick validation). |
| **Success Metric** | Giảm thời gian từ 30-60 phút xuống dưới 5 phút/request; giữ độ chính xác SQL 90-95% với human review. |
| **Boundary** | AI không tự gửi kết quả cho stakeholder; analyst luôn review SQL + visualization trước khi gửi; AI không được thấy các cột dữ liệu nhạy cảm (PII). |

---

## Rule / Workflow / Agent

| Mức | Phương án cho bài toán nhóm | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | Template SQL tham số hóa + dashboard có sẵn cho các loại request lặp lại (vd: "revenue theo category theo quý") | Đủ nếu phần lớn request rơi vào một số pattern cố định đã biết trước | Không xử lý được request thật sự mới/ad-hoc; cần biết trước danh sách pattern | Chưa được nhóm đánh giá — cần làm trước khi chốt Agent |
| **Workflow** | Pipeline cố định: nhận request đã chuẩn hóa → chạy SQL template → format chart cố định | Đủ nếu loại request có thể chuẩn hóa thành một số dạng câu hỏi giới hạn | Không adapt được khi schema đổi hoặc câu hỏi lệch khỏi template | Bị loại nhanh với lý do "database không predictable" — cần dẫn chứng cụ thể hơn (bao nhiêu % request là ad-hoc thật sự mới) |
| **Agent** | NLP hiểu request → tự khám phá schema → generate SQL → execute → tạo viz → analyst review | Cần nếu tỷ lệ request ad-hoc/mới cao, schema thay đổi thường xuyên, và có compliance cho phép AI truy cập DB | Sinh SQL sai, lộ dữ liệu nhạy cảm, hiểu sai ý định stakeholder, chi phí vận hành cao hơn Rule/Workflow | Chọn |

Mức chọn:

```text
Agent (cho phần ad-hoc mới; Rule/Workflow cho phần request lặp lại).
```

Vì sao:

- Schema khác nhau giữa các công ty/hệ thống, cần adapt động.
- Query có thể fail theo nhiều cách khác nhau (sai join, thiếu cột, lỗi permission), cần retry/tự sửa.
- Edge case (NULL, sai kiểu dữ liệu) cần AI suy luận theo ngữ cảnh.

Vì sao không chọn mức đơn giản hơn:

```text
Lý do ban đầu: SQL generation "không phải quy trình tuyến tính". Tuy nhiên lý do này chỉ đúng cho phần schema, chưa chứng minh phần lớn request stakeholder cũng không predictable. Nếu 70-80% request rơi vào một vài dạng câu hỏi quen thuộc, Rule/Workflow nên xử lý phần đó, Agent chỉ cho phần ad-hoc thật sự mới — cần số liệu thật (tỷ lệ request lặp vs mới) để quyết định đúng phạm vi trước khi mở rộng Agent ra toàn bộ workflow.
```

---

## Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Data analyst xử lý yêu cầu data ad-hoc từ stakeholder. |
| **Workflow** | Request → clarify → viết SQL → execute/debug → export → visualization → gửi stakeholder. |
| **Bottleneck** | Viết SQL và tạo visualization thủ công cho mỗi request, kể cả các request lặp lại dạng quen thuộc. |
| **Impact** | 30-60 phút/request (baseline cần validate); risk tồn đọng công việc, stakeholder chờ lâu, analyst không có thời gian cho phân tích chiến lược. |
| **Success Metric** | Giảm thời gian trung bình xuống dưới 5 phút/request; SQL accuracy 90-95% với human review; đo riêng tỷ lệ request được Rule/Workflow xử lý vs tỷ lệ cần Agent. |
| **Boundary** | AI không tự gửi cho stakeholder; không truy cập cột dữ liệu nhạy cảm (PII); analyst luôn là gatekeeper cuối cùng. |
| **AI intervention point** | Sau khi request đã được analyst clarify, trước bước viết SQL — chỉ cho các request được xác định là "ad-hoc mới" (không khớp pattern Rule có sẵn). |
| **Mức chọn** | Agent cho phần ad-hoc mới; Rule/Workflow cho phần request lặp lại theo pattern quen thuộc. |
| **Rủi ro & người thật kiểm tra** | Risk: SQL sai, lộ dữ liệu nhạy cảm, hiểu sai ý định, chi phí vận hành Agent nếu áp dụng cho cả phần lẽ ra Rule đã đủ. Người thật kiểm tra: analyst review toàn bộ output trước khi gửi (human gate, 2-3 phút/request). |

---

## Final decision

Decision:

```text
Go, với pilot phạm vi hẹp.
```

Pilot nhỏ nhất:

- 1 database duy nhất, không phải toàn bộ hệ thống công ty.
- Chỉ 3 loại visualization: bar chart, line chart, data table.
- Chỉ visualization tĩnh, chưa làm interactive filter (để Phase 2).
- Analyst bắt buộc review + approve trước khi stakeholder thấy kết quả.
- Test với 5-10 request thật.
- Thời gian pilot: 2-3 tuần.
- Không làm ở pilot này: interactive + storytelling visualization, personalize visualization theo từng người dùng, mở rộng ra ngoài 1 công ty/database.

Exit / rollback:

- SQL accuracy ≥ 80% sau 10 query là điều kiện tiếp tục; nếu tụt dưới 75% liên tục thì rollback.
- Thời gian thực thi ổn định dưới 30 giây/query; thời gian analyst xử lý mỗi request dưới 5 phút.
- Nếu stakeholder thích quy trình thủ công hơn (cần verify, không giả định) thì rollback.
- Trước khi chạy trên dữ liệu thật: xác nhận danh sách bảng/cột bị loại khỏi schema view của AI (PII).
- Đo tỷ lệ request lặp lại vs ad-hoc thật sự trong 5-10 request pilot, để biết Agent có thực sự cần cho toàn bộ workflow hay chỉ một phần.

Decision rationale:

- Problem có workflow rõ, bottleneck rõ (viết SQL + tạo visualization).
- Baseline thời gian (30-60 phút/request) chưa được validate bằng nguồn độc lập — cần phỏng vấn thật với ít nhất 2-3 analyst trước khi dùng làm số liệu chính thức.
- Agent chỉ nên áp dụng cho phần request ad-hoc thật sự mới; phần lặp lại nên dùng Rule/Workflow, cần số liệu thật để xác định đúng tỷ lệ.
- Boundary rõ: analyst luôn là gatekeeper, AI không tự gửi output, không truy cập cột dữ liệu nhạy cảm.
