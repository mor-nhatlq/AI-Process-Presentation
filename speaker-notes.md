# Speaker Notes — Agentic Coding @ Mor

**Tổng thời lượng:** 30-35 phút trình bày + 5-10 phút Q&A = 40-45 phút
**Số slide:** 14
**Audience:** Toàn bộ developer Mor — đã biết Claude Code, mix junior↔senior

> Notes này standalone — presenter có thể đọc mà không cần mở deck. Ngắn gọn, mỗi slide ≤ 5 talking point + 1 analogy + 1 Q&A anticipated.

---

## Slide 1 — Agentic Coding @ Mor (Title hero)

**Time:** 1 phút
**Visual:** Hero gradient + corner logo + tagline

### Talking points
- Mở đầu: hôm nay nói về **Agentic Coding** — quy trình mới Mor áp dụng cho mọi dự án.
- Mục tiêu buổi này: hiểu high-level quy trình, biết khi nào dùng skill nào, biết workflow Requirement → Code.
- Demo chi tiết tách buổi sau, hôm nay tập trung concept.

### Analogy
> *"Trước đây: junior dev tự code, senior review sau. Giờ: pair với AI — AI là junior xịn cần spec rõ. Ta là senior, chỉ tay + duyệt. Output chất lượng hơn, ít rework."*

### Transition
→ "3 nguyên tắc cốt lõi để hiểu cả quy trình."

---

## Slide 2 — 3 nguyên tắc cốt lõi

**Time:** 2 phút
**Visual:** 3 principle cards (📋 🚦 🔄)

### Talking points
- **Spec-first** — không code khi chưa có tài liệu. Tránh AI tự sáng tạo, drift khỏi yêu cầu.
- **Human-gate** — mỗi step quan trọng có người duyệt. Không phải "AI làm hết", mà "AI làm, người duyệt".
- **TDD** — test trước, code sau. Test confirm behavior đúng, không confirm bug có sẵn.
- 3 nguyên tắc này áp dụng xuyên suốt 2 workflow phía sau.

### Anticipated Q&A
**Q:** "Có overhead không? Mất thêm thời gian write test, write spec?"
**A:** "Có overhead local nhưng giảm rework. Đo throughput end-to-end (từ ý tưởng → production), không đo local. Số liệu pilot sẽ public sau Q2."

### Transition
→ "Quy trình tổng quan trông thế nào?"

---

## Slide 3 — Quy trình chung

**Time:** 1.5 phút
**Visual:** Mermaid 2-box: Workflow Requirement → artifact → Workflow Code

### Talking points
- 2 workflow: **Workflow Requirement** (BrSE/BA + AI) và **Workflow Code** (Dev + AI).
- Bàn giao bằng tài liệu: `srs.md` (Software Requirements Spec) + `design.md` (HLD).
- Workflow Code không bắt đầu khi chưa có 2 file này.

### Anticipated Q&A
**Q:** "Ai own `srs.md`?"
**A:** "BrSE/BA author chính. AI agent draft. Tech Lead final review trước khi pass sang coding."

### Transition
→ "Vai trò cụ thể trong team?"

---

## Slide 4 — Vai trò trong team

**Time:** 2 phút
**Visual:** 4 persona card 2×2 grid

### Talking points
- **AI Champion** — người thúc đẩy AI cho dự án, train team, monitor performance khi dùng AI. 1 champion / dự án.
- **PM / BrSE / BA** — gather yêu cầu, break task, làm tài liệu. Review proposal + SRS.
- **Tech Lead** — dùng AI hỗ trợ review code + tài liệu. Gate cuối trước khi merge.
- **Developer** — code chính theo TDD cùng AI. Open PR, request review.

### Anticipated Q&A
**Q:** "Junior dev có review gì không?"
**A:** "Có — peer review `tasks.md` trước khi execute. Junior học nhanh nhất qua review code của người khác."

### Transition
→ "Đi sâu vào Workflow Requirement trước."

---

## Slide 5 — Workflow Requirement (diagram)

**Time:** 3-4 phút (slide sâu nhất)
**Visual:** PNG image — click zoom modal nếu cần

### Talking points
- Lane 1: **AI Champion** setup skill cho dự án (1 lần / dự án).
- Lane 2: **PM/BrSE/BA** gather yêu cầu, đưa cho AI.
- Lane 3: **AI Agent** brainstorm → decompose → gap analysis → gen SRS → HLD.
- Lane 4: **Tech Lead** gate cuối trước chuyển coding.
- 4 review gate: tại bước 5, 7, 10, 12. Mỗi gate có **NOT-OK loop** quay về AI re-iterate.
- Click ảnh để xem fullscreen — image size đầy đủ cho detail.

### Anticipated Q&A
**Q:** "Tại sao nhiều review gate vậy? Không chậm sao?"
**A:** "Mỗi gate sẽ catch issue sớm. Issue tại bước 5 fix nhanh hơn issue tại bước 12 nhiều. Cost of fix tăng exponential."

### Transition
→ "Skill nào dùng cho từng bước?"

---

## Slide 6 — Workflow Requirement · Skill map

**Time:** 2 phút (table — đọc qua, không từng row)
**Visual:** Table 5-col

### Talking points
- Table này là cheat sheet — không cần nhớ hết, để dev tham khảo lại.
- Cột "Mô tả" giải thích step làm gì.
- Cột "Skill / Command" có command thực thi.
- Highlight: `/spec:propose` (decompose), `/spec:review` (gate), `/docs-hero:init` (gen SRS).

### Anticipated Q&A
**Q:** "Có cần học hết tất cả command không?"
**A:** "Không. Champion / Tech Lead biết toàn bộ. Dev biết command thường dùng (slide 13 sẽ tổng hợp)."

### Transition
→ "Cơ chế Review hoạt động thế nào?"

---

## Slide 7 — Human Review Gate (merged)

**Time:** 4 phút (slide quan trọng nhất)
**Visual:** 2-col: NOT-OK loop + 2 cơ chế chặn + checklist

### Talking points
- AI sinh artifact → tạo file `review-checklist.md` tự động.
- Người review **mở file checklist, tick thủ công từng đầu mục**. Không AI tự tick — đây là chỗ con người judge.
- Tick xong, đặt `Overall Decision: OK`. Chưa OK → AI re-iterate theo feedback.
- Lặp đến khi người dùng hài lòng.
- Có **2 cơ chế chặn** ngăn skip review:
  - **PreToolUse hook** — Claude harness chặn skill invocation. Không thể bypass bằng prompt thường.
  - **Skill content gate** — skill tự refuse run nếu checklist còn PENDING.
- Defense-in-depth: nếu 1 layer bị disable, layer kia vẫn block.

### Analogy
> *"Như red light + speed bump cùng lúc. Bỏ red light xong vẫn còn bump — không thể tăng tốc bypass."*

### Anticipated Q&A
**Q:** "Loop bao nhiêu lần thường?"
**A:** "1-2 lần thường đủ. > 3 lần → escalate Tech Lead, có thể spec sai từ đầu hoặc reviewer + AI hiểu khác nhau."

**Q:** "Có cách bypass không?"
**A:** "Có — set `Overall Decision: OK` thủ công. Nhưng đó là quyết định người review, có audit trail rõ ai bypass + lý do."

### Transition
→ "Workflow Code sau khi có SRS + design."

---

## Slide 8 — Workflow Code (diagram)

**Time:** 3-4 phút
**Visual:** PNG image — click zoom modal

### Talking points
- Setup → nhận `srs.md` + `design.md` từ Workflow Requirement.
- Brainstorm hướng implementation → LLD → review LLD.
- Plan TDD step-by-step → review plan.
- **TDD inner loop** (highlighted): Write Test → FAIL → Code → PASS → Refactor → Regression. Lặp với mỗi task.
- Sau TDD: Deep Review (5 sub-agents) → Final Review → PR → Tech Lead duyệt PR → Deploy dev → QA.

### Anticipated Q&A
**Q:** "TDD inner loop khác outer task loop thế nào?"
**A:** "Inner = lặp test/code/refactor cho **1 task**. Outer = chuyển sang **task kế tiếp** trong tasks.md. Mỗi task ≈ 1 chức năng nhỏ."

### Transition
→ "Skill cụ thể cho từng bước Workflow Code."

---

## Slide 9 — Workflow Code · Skill map

**Time:** 2 phút
**Visual:** Table 5-col, 17 row

### Talking points
- Tương tự slide 6 — cheat sheet.
- Highlight: `/superpowers:test-driven-development` (RED phase), `/spec:apply` (code), `/superpowers:execute-plan` (refactor), `/deep-review --diff` (auto review code).
- Tech Lead chú ý: `/deep-review <PR>` chạy 5 sub-agents song song trên PR.

### Anticipated Q&A
**Q:** "Phải chạy `/deep-review` thủ công sau mỗi PR?"
**A:** "Recommended yes. Hoặc cấu hình GitHub Action chạy auto trên mỗi PR mở (sẽ document sau pilot)."

### Transition
→ "Tôi đã nói TDD nhiều lần — TDD là gì cụ thể?"

---

## Slide 10 — TDD cycle

**Time:** 3 phút
**Visual:** Mermaid 6-node circular RED·GREEN·BLUE

### Talking points
- Bạn thấy tôi đang nói về TDD nhiều mà chưa giải thích nó là gì.
- Đi qua quy trình TDD dựa vào đồ thị:
  - **Viết test trước** — test sẽ fail vì chưa có code (**RED**).
  - **Viết minimum code** để test pass (**GREEN**). Không over-engineer.
  - **Refactor** — cải tiến code, **giữ nguyên behavior**. Tests vẫn pass.
  - **Chạy lại toàn bộ test** → đảm bảo không break test khác (**REGRESSION**).
  - Lặp lại cho test/feature tiếp theo.
- Tại sao quan trọng: test viết SAU code → test confirm bug có sẵn. Test viết TRƯỚC → test enforce behavior mong muốn.

### Anticipated Q&A
**Q:** "Refactor có cần test mới?"
**A:** "Không. Refactor = thay đổi structure, giữ behavior. Test mới = feature mới = TDD cycle mới."

**Q:** "Senior có thể skip TDD không?"
**A:** "Không. Senior code cũng có bug. TDD là safety net, không phải junior training wheel."

### Transition
→ "Toolkit để làm tất cả việc trên."

---

## Slide 12 — Toolkit · 4 plugin

**Time:** 1.5 phút
**Visual:** 4 plugin card 2×2

### Talking points
- **`spec`** — workflow dựa trên tài liệu, build trên OpenSpec. Tạo proposal/design/tasks/checklist.
- **`superpowers`** — TDD-focused skills. Note: bộ Mor **không dùng `/brainstorming` của superpowers** (override).
- **`deep-review`** — 5 sub-agents song song review risk bảo mật/testing/convention. Chạy trên PR hoặc git diff.
- **`docs-hero`** — generate SRS + API docs + DB design (BrSE standard).

### Anticipated Q&A
**Q:** "Cài bằng cách nào?"
**A:** "`/plugin add marketplace github:mor-duongmh/claude-plugins` rồi `/plugin install spec@mor-duongmh`. Chi tiết trong `claude-plugins/README.md`."

### Transition
→ "Tình huống cụ thể, dùng skill nào?"

---

## Slide 13 — Các use case phổ biến

**Time:** 2 phút
**Visual:** Mermaid decision tree 4-leaf

### Talking points
- Tuỳ tình huống → workflow nhỏ tương ứng. Đồ thị này là quick map.
- **Start new feature** → `/spec:propose` (full Workflow Requirement).
- **Continue plan đang dở** → `/superpowers:execute-plan`.
- **Debug bug/error** → `/superpowers:systematic-debugging` trước, không jump vào fix ngay.
- **Review PR** → `/deep-review <PR-num>`.
- AI Team sẽ gửi link tình huống cụ thể thường gặp sau buổi này.

### Anticipated Q&A
**Q:** "Bug critical, có cần đi qua spec không?"
**A:** "Bug fix nhỏ — skip spec, dùng `/superpowers:systematic-debugging` trực tiếp. Bug lớn (architectural) — vẫn cần spec để align hướng fix."

### Transition
→ "5 điều tối kị, đừng làm."

---

## Slide 14 — Anti-pattern · Tối kị không được làm

**Time:** 2.5 phút
**Visual:** 5 đỏ list với border red

### Talking points
- **Skip review gate** — code drift khỏi spec đã thống nhất. Gây inconsistent quality giữa các phần dự án.
- **Skip TDD** — bắt buộc theo TDD trừ khi đặc thù dự án không khả thi (legacy code không test được, real-time system, ...). Báo trước nếu skip.
- **Bỏ qua `/deep-review`** — miss security/pattern issue. Issue type này không thấy bằng eyeball review.
- **Edit `tasks.md` giữa execution** — phá cấu trúc agent đang chạy. Nếu cần đổi plan → stop, edit, restart.
- **Dùng AI agent không có tài liệu** — đây là vibe coding, không nằm phạm trù agentic. Sai mục đích quy trình.

### Anticipated Q&A
**Q:** "Có ngoại lệ nào không?"
**A:** "Có — đặc thù dự án (mentioned). Nhưng phải report Champion/Tech Lead trước khi skip, không tự ý."

### Transition
→ "Bắt đầu áp dụng thế nào?"

---

## Slide 15 — Adoption · Bắt đầu thế nào?

**Time:** 2 phút + Q&A 5-10 phút
**Visual:** 4-stage roadmap + 3 actions + footer logo

### Talking points
- **Pilot** (đã chọn 3 dự án) — AI Team follow + triển khai chạy thử. Thu collected data.
- **Training & Adopting** — training use case theo dự án. AI Team chạy 1-2 task cùng dev cải thiện quy trình.
- **Adapting** — Pilot tự chủ. AI Team monitor performance, support khi cần.
- **Rollout** — áp dụng toàn bộ dự án công ty.
- 3 actions ngay hôm nay (theo flow):
  1. Pilot → nhận follow-up từ AI Team.
  2. Training → tham gia session + thực hành.
  3. Adapting → tự chủ áp dụng, báo blocker / feedback.
- Open Q&A 5-10 phút.

### Closing
- Cảm ơn cả team. Link slide deck + repo `claude-plugins` sẽ gửi sau.
- Champion nhận follow-up email với detail timeline.

### Anticipated Q&A
**Q:** "Dự án không thuộc Pilot làm gì lúc này?"
**A:** "Quan sát + chuẩn bị. Khi Pilot done, AI Team sẽ trigger Training cho team các bạn. Trước đó tự nghiên cứu repo `claude-plugins` được khuyến khích."

**Q:** "Performance metrics sẽ là gì?"
**A:** "Throughput end-to-end (ý tưởng → production), rework rate, bug escape rate, time-to-first-PR. Định nghĩa cụ thể đang finalize."

---

## Backup notes — Q&A buffer

### Câu hỏi technical hay gặp
- *"Plugin có conflict với plugin Mor cũ không?"* → Plugin Mor dùng namespace `mor-duongmh`, không conflict với plugin upstream cùng tên. Cài chỉ một bộ.
- *"AI có lưu code/data của Mor không?"* → Claude API không train trên user data. Data privacy giải quyết qua Anthropic Enterprise contract (Champion biết detail).
- *"GitHub Actions auto chạy `/deep-review` được không?"* → Có. Sample workflow trong `claude-plugins/docs/`. Pilot sẽ test rồi share.

### Câu hỏi quy trình hay gặp
- *"Champion là ai chọn?"* → AI Team đề xuất + dự án confirm. Mỗi dự án 1 champion (có thể là Tech Lead hoặc senior dev).
- *"Mất bao lâu để 1 dự án adopt full?"* → Pilot timeline 6-8 tuần. Từ adopting → adapting tốc độ tùy team. Average kỳ vọng 2-3 tháng.
- *"Có cost gì không?"* → Claude API cost (Anthropic) + thời gian training. Cost tracking qua AI Team. ROI đo qua metrics phía trên.
