# Getting Started — Viết user guide đầu tiên trong ~30 phút

> Hướng dẫn này dẫn bạn (PO/BA) đi qua **happy path**: từ lúc có SRS + staging URL
> đến lúc có folder markdown user guide hoàn chỉnh, sẵn sàng bàn giao publish.
>
> **Thời gian ước tính:** 30 phút thao tác + thời gian AI tự chạy (10–20 phút,
> tùy độ phức tạp của feature). Trong lúc AI chạy, bạn có thể làm việc khác.

---

## 0. Chuẩn bị trước khi bắt đầu

Checklist 5 mục — phải có đủ trước khi mở Claude Code:

- [ ] **Claude Code** đã cài và đăng nhập (nếu chưa, liên hệ IT)
- [ ] **Plugin Docsmith** đã install:
  ```
  /plugin marketplace add https://gitlab.fci.vn/bss/docsmith.git
  /plugin install docsmith@bss-docsmith
  ```
- [ ] **(Optional)** **PRD và/hoặc SRS của feature** để tham khảo khi điền
  audience profile và verify chi tiết kỹ thuật ở các bước sau. Không bắt buộc,
  nhưng càng có càng đỡ phải nghĩ persona/feature behavior từ đầu.
- [ ] **(Optional)** **Staging URL** của feature + **test account** (username/password)
  - Có → AI tự chụp screenshot ở bước `walkthrough`
  - Không có → bạn tự chụp tay rồi paste vào draft, hoặc skip `walkthrough`
- [ ] Đã **clone repo doc** của công ty về máy
- [ ] Repo doc đã có sẵn **company-wide standards** ở `<doc-repo>/standards/`:
  - `voice-chart.md`
  - `ux-text-patterns.md`
  - `content-scorecard.md`

  > Đây là 3 file UX content standards đã chốt cross-team. AI sẽ tự đọc khi
  > chạy bước `voice`, bạn không phải làm gì. Nếu repo doc chưa có, liên hệ
  > owner để được setup.

---

## 1. Mở Claude Code trong repo doc (2 phút)

1. Mở Terminal (macOS) hoặc Command Prompt (Windows)
2. `cd` vào repo doc đã clone, ví dụ:
   ```
   cd ~/work/doc-repo
   ```
3. Gõ `claude` để khởi động Claude Code
4. Khi Claude Code mở, bạn sẽ thấy prompt sẵn sàng nhận lệnh

---

## 2. Khởi động workflow (1 lệnh)

Gõ:

```
/docsmith start <TenFeature>
```

Ví dụ: `/docsmith start PaymentGateway`

> **Tên feature** nên ngắn, không dấu, không khoảng trắng. Đây sẽ là tên folder output.

AI sẽ giới thiệu workflow và bắt đầu **Step 1: Audience** — bước này do bạn (Human) làm.

---

## 3. Step 1 — Audience: Định nghĩa người đọc

Đây là bước **Human-owned** theo workflow chuẩn của Docsmith. AI sẽ:

1. Cung cấp cho bạn **template Audience Profile** (file `AUDIENCE_PROFILE_TEMPLATE.md`)
2. Hướng dẫn cách điền: gather existing knowledge, define user goals, identify
   target users, outline user needs, identify competitors, condense thành persona
   và user stories
3. Hỏi bạn: **(a)** cung cấp profile đã điền sẵn, hoặc **(b)** trả lời tương tác từng câu

Bạn chọn 1 trong 2:

- **Cách (a):** Mở template, điền tay theo hiểu biết về feature (có thể tham khảo
  PRD/SRS nếu có), lưu thành `docs/<TenFeature>/plan/audience-profile.md`, rồi báo AI
- **Cách (b):** Trả lời từng câu AI hỏi. AI sẽ tổng hợp và lưu file giúp bạn

> 💡 **Mẹo:** Nếu công ty bạn đã có PRD/SRS chi tiết cho feature, mở sẵn để
> tham khảo khi điền template hoặc trả lời câu hỏi của AI — tiết kiệm thời gian
> nghĩ persona từ đầu.

---

## 4. Step 2–6 — AI tự chạy: Plan → Sitemap → Voice → Draft → Edit (10–15 phút)

Sau khi audience được xác nhận, AI sẽ tự động chạy các bước:

| Bước | AI làm gì |
|---|---|
| `plan` | Tạo documentation plan + traceability matrix |
| `sitemap` | Định nghĩa folder structure, navigation |
| `voice` | **Tự đọc** voice chart + UX text patterns + scorecard từ `<doc-repo>/standards/` (không sinh lại — đã chốt cross-team) |
| `draft` | Viết draft toàn bộ tài liệu theo content type templates |
| `edit` | Tự review qua 5 passes (technical accuracy, completeness, structure, clarity, voice) |

> ☕ **Đây là lúc bạn nghỉ.** AI sẽ ping khi cần input ở Gate 1.

### 🚦 Gate 1 — Review Plan (sau bước `plan`)

AI sẽ dừng và xin bạn approve documentation plan. Check:
- [ ] Plan có cover đủ user journey chính của feature không?
- [ ] Các content type (getting-started, how-to, reference) có hợp lý không?
- [ ] Có thiếu phần nào quan trọng từ SRS không?

**OK** → trả lời `approve` để AI tiếp tục.
**Cần sửa** → nói cụ thể, ví dụ: *"Thêm 1 how-to về cấu hình SSO, lấy thông tin từ SRS section 3.2"*.

---

## 5. Step 7 — Walkthrough: AI test trên staging và chụp screenshot (5–10 phút)

Khi đến bước walkthrough, AI cần thông tin staging:

```
/docsmith walkthrough <TenFeature>
```

Cung cấp khi AI hỏi:
- Staging URL
- Test account
- Lưu ý đặc biệt (feature flag cần bật, demo data cần seed...)

AI sẽ:
1. Tạo test cases từ docs
2. Mở browser tự động, chạy từng test case
3. Chụp screenshot tại các bước cần thiết
4. Thay thế tất cả `placehold.co` placeholder bằng ảnh thật
5. Nếu phát hiện doc sai (UI không khớp mô tả), tự sửa
6. Xuất báo cáo execution

> ☕ **Đây cũng là lúc bạn nghỉ.** Bước này có thể kéo dài, đặc biệt với feature nhiều màn hình.

---

## 6. 🚦 Gate 2 — Peer Review (5 phút)

```
/docsmith peer-review <TenFeature>
```

AI sẽ trình bày toàn bộ tài liệu để bạn review. Check:
- [ ] Đọc qua từng file, kiểm tra mô tả có đúng feature không
- [ ] Mỗi screenshot có khớp với UI staging không?
- [ ] Có còn placeholder `[TODO]`, `[TBD]`, `placehold.co` nào không?
- [ ] Voice/tone có nhất quán không?
- [ ] Các link nội bộ giữa các file có work không?

**OK** → tiến tới bước cuối.
**Có feedback** → nói cụ thể, AI sẽ chạy `incorporate` để sửa rồi quay lại review.

---

## 7. Hoàn tất và bàn giao (2 phút)

```
/docsmith publish <TenFeature>
```

AI sẽ show **publication checklist**:
1. Final sign-off chất lượng nội dung
2. Phối hợp với release của code/product
3. Publish lên documentation platform
4. Announce cho users

Tick xong là **DONE**. Output của bạn nằm tại:

```
<doc-repo>/
├── standards/                    # Company-wide, KHÔNG đụng — đã có sẵn
└── docs/<TenFeature>/
    ├── plan/                     # Audience profile, plan, sitemap, traceability
    ├── drafts/                   # ⭐ Các file user guide chính
    ├── walkthrough/              # Test cases, execution reports
    └── images/                   # Screenshot đã capture
```

**Bàn giao** folder `docs/drafts/<TenFeature>/` và `docs/images/<TenFeature>/`
cho _[bộ phận publish của công ty]_ để đẩy lên static site.

---

## Xong! Cần thêm gì?

- 📋 Tra cứu lệnh khác → [Reference](reference.md)
- 💬 Hỏi người thật → _#docsmith-support (điền sau)_

---

> ⚠️ **Lưu ý quan trọng:** Đây là **happy path**. Trong thực tế, có thể bạn
> cần quay lại các bước trước (ví dụ: AI hiểu sai feature, cần re-plan; hoặc
> screenshot không khớp, cần re-walkthrough). Đó là chuyện bình thường — cứ
> nói rõ với AI cái cần sửa, đừng ngại lặp lại các bước.
