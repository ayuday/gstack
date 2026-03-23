<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> "Tôi không nghĩ mình đã gõ một dòng code nào kể từ tháng 12, về cơ bản, đó là một thay đổi cực kỳ lớn." — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), podcast No Priors, tháng 3 năm 2026

Khi tôi nghe Karpathy nói điều này, tôi muốn tìm hiểu làm thế nào. Làm sao một người có thể giao hàng như một đội hai mươi người? Peter Steinberger đã xây dựng [OpenClaw](https://github.com/openclaw/openclaw) — 247K sao trên GitHub — về cơ bản một mình với các agent AI. Cuộc cách mạng ở đây. Một người xây dựng duy nhất với công cụ phù hợp có thể di chuyển nhanh hơn một đội truyền thống.

Tôi là [Garry Tan](https://x.com/garrytan), Chủ tịch & CEO của [Y Combinator](https://www.ycombinator.com/). Tôi đã làm việc với hàng nghìn startup — Coinbase, Instacart, Rippling — khi họ chỉ là một hoặc hai người trong gara. Trước YC, tôi là một trong những kỹ sư/PM/designer đầu tiên tại Palantir, đồng sáng lập Posterous (bán cho Twitter), và xây dựng Bookface, mạng xã hội nội bộ của YC.

**gstack là câu trả lời của tôi.** Tôi đã xây dựng sản phẩm trong hai mươi năm, và giờ tôi đang giao nhiều code hơn bao giờ hết. Trong 60 ngày qua: **hơn 600.000 dòng code production** (35% tests), **10.000-20.000 dòng mỗi ngày**, bán thời gian, trong khi điều hành YC toàn thời gian. Đây là `/retro` mới nhất của tôi trên 3 dự án: **140.751 dòng được thêm, 362 commits, ~115k LOC ròng** trong một tuần.

**2026 — 1.237 đóng góp và tiếp tục:**

![Đóng góp GitHub 2026 — 1.237 đóng góp, tăng tốc mạnh vào tháng 1-3](docs/images/github-2026.png)

**2013 — khi tôi xây dựng Bookface tại YC (772 đóng góp):**

![Đóng góp GitHub 2013 — 772 đóng góp xây dựng Bookface tại YC](docs/images/github-2013.png)

Cùng một người. Thời đại khác. Sự khác biệt là công cụ.

**gstack là cách tôi làm.** Nó biến Claude Code thành một đội kỹ thuật ảo — một CEO suy nghĩ lại sản phẩm, một quản lý kỹ thuật khóa kiến trúc, một designer phát hiện rác AI, một reviewer tìm bug production, một trưởng QA mở trình duyệt thật, một nhân viên an ninh chạy kiểm toán OWASP + STRIDE, và một kỹ sư phát hành đẩy PR. Hai mươi chuyên gia và tám công cụ mạnh, tất cả lệnh slash, tất cả Markdown, tất cả miễn phí, giấy phép MIT.

Đây là nhà máy phần mềm nguồn mở của tôi. Tôi dùng nó mỗi ngày. Tôi chia sẻ nó vì những công cụ này nên có sẵn cho mọi người.

Fork nó. Cải thiện nó. Làm nó thành của bạn. Và nếu bạn muốn chê bai phần mềm nguồn mở miễn phí — bạn được chào đón, nhưng tôi thà bạn thử nó trước.

**Dành cho ai:**
- **Nhà sáng lập và CEO** — đặc biệt những người kỹ thuật vẫn muốn giao hàng
- **Người dùng Claude Code lần đầu** — vai trò có cấu trúc thay vì prompt trống
- **Tech leads và kỹ sư staff** — kiểm tra nghiêm ngặt, QA, và tự động hóa phát hành trên mọi PR

## Bắt đầu nhanh

1. Cài đặt gstack (30 giây — xem bên dưới)
2. Chạy `/office-hours` — mô tả những gì bạn đang xây dựng
3. Chạy `/plan-ceo-review` trên bất kỳ ý tưởng tính năng nào
4. Chạy `/review` trên bất kỳ branch nào có thay đổi
5. Chạy `/qa` trên URL staging của bạn
6. Dừng ở đó. Bạn sẽ biết liệu đây có dành cho bạn không.

## Cài đặt — 30 giây

**Yêu cầu:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (chỉ Windows)

### Bước 1: Cài đặt trên máy của bạn

Mở Claude Code và dán điều này. Claude làm phần còn lại.

> Cài đặt gstack: chạy **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** sau đó thêm phần "gstack" vào CLAUDE.md nói sử dụng kỹ năng /browse từ gstack cho tất cả duyệt web, không bao giờ dùng công cụ mcp__claude-in-chrome__*, và liệt kê các kỹ năng có sẵn: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. Sau đó hỏi người dùng liệu họ cũng muốn thêm gstack vào dự án hiện tại để đồng đội nhận được nó.

### Bước 2: Thêm vào repo của bạn để đồng đội nhận được (tùy chọn)

> Thêm gstack vào dự án này: chạy **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** sau đó thêm phần "gstack" vào CLAUDE.md của dự án này nói sử dụng kỹ năng /browse từ gstack cho tất cả duyệt web, không bao giờ dùng công cụ mcp__claude-in-chrome__*, liệt kê các kỹ năng có sẵn: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, và nói với Claude rằng nếu kỹ năng gstack không hoạt động, chạy `cd .claude/skills/gstack && ./setup` để build binary và đăng ký kỹ năng.

Các file thực tế được commit vào repo của bạn (không phải submodule), nên `git clone` chỉ cần hoạt động. Mọi thứ sống trong `.claude/`. Không gì chạm vào PATH của bạn hoặc chạy nền.

### Codex, Gemini CLI hoặc Cursor

gstack hoạt động trên bất kỳ agent nào hỗ trợ [chuẩn SKILL.md](https://github.com/anthropics/claude-code). Các kỹ năng sống trong `.agents/skills/` và được phát hiện tự động.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

Hoặc để setup tự động phát hiện những agent nào bạn đã cài:

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

Điều này cài đặt vào `~/.claude/skills/gstack` và/hoặc `~/.codex/skills/gstack` tùy thuộc vào những gì có sẵn. Tất cả 28 kỹ năng hoạt động trên tất cả các agent được hỗ trợ. Các kỹ năng an toàn dựa trên hook (careful, freeze, guard) sử dụng văn bản tư vấn an toàn inline trên các host không phải Claude.

## Xem nó hoạt động

```
Bạn:   Tôi muốn xây dựng một ứng dụng briefing hàng ngày cho lịch của tôi.
Bạn:   /office-hours
Claude: [hỏi về nỗi đau — ví dụ cụ thể, không giả thuyết]

Bạn:   Nhiều lịch Google, sự kiện với thông tin cũ,
       địa điểm sai. Chuẩn bị mất mãi mãi và kết quả
       không đủ tốt...

Claude: Tôi sẽ phản đối cách khung. Bạn nói "ứng dụng briefing
       hàng ngày". Nhưng những gì bạn thực sự mô tả là một
       trưởng phòng nhân sự AI cá nhân.
       [trích xuất 5 khả năng bạn không nhận ra mình đang mô tả]
       [thách thức 4 tiền đề — bạn đồng ý, không đồng ý, hoặc điều chỉnh]
       [tạo 3 cách tiếp cận triển khai với ước tính nỗ lực]
       KHUYẾN NGHỊ: Giao hàng hẹp nhất ngày mai, học từ
       sử dụng thực tế. Tầm nhìn đầy đủ là dự án 3 tháng —
       bắt đầu với briefing hàng ngày thực sự hoạt động.
       [viết tài liệu thiết kế → tự động nuôi các kỹ năng downstream]

Bạn:   /plan-ceo-review
       [đọc tài liệu thiết kế, thách thức phạm vi, chạy kiểm tra 10 phần]

Bạn:   /plan-eng-review
       [sơ đồ ASCII cho luồng dữ liệu, máy trạng thái, đường dẫn lỗi]
       [ma trận test, chế độ lỗi, lo ngại bảo mật]

Bạn:   Phê duyệt kế hoạch. Thoát chế độ kế hoạch.
       [viết 2.400 dòng trên 11 file. ~8 phút.]

Bạn:   /review
       [AUTO-FIXED] 2 vấn đề. [ASK] Race condition → bạn phê duyệt fix.

Bạn:   /qa https://staging.myapp.com
       [mở trình duyệt thật, click qua các flow, tìm và sửa bug]

Bạn:   /ship
       Tests: 42 → 51 (+9 mới). PR: github.com/you/app/pull/42
```

Bạn nói "ứng dụng briefing hàng ngày". Agent nói "bạn đang xây dựng một trưởng phòng nhân sự AI" — vì nó lắng nghe nỗi đau của bạn, không phải yêu cầu tính năng của bạn. Tám lệnh, từ đầu đến cuối. Đây không phải copilot. Đây là một đội.

## Sprint

gstack là một quy trình, không phải bộ sưu tập công cụ. Các kỹ năng chạy theo thứ tự sprint chạy:

**Suy nghĩ → Lập kế hoạch → Xây dựng → Kiểm tra → Test → Giao hàng → Suy ngẫm**

Mỗi kỹ năng nuôi kỹ năng tiếp theo. `/office-hours` viết tài liệu thiết kế mà `/plan-ceo-review` đọc. `/plan-eng-review` viết kế hoạch test mà `/qa` nhận. `/review` bắt bug mà `/ship` xác nhận đã sửa. Không gì rơi qua kẽ hở vì mỗi bước biết những gì đến trước.

| Kỹ năng | Chuyên gia của bạn | Những gì họ làm |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Bắt đầu ở đây. Sáu câu hỏi bắt buộc đóng khung lại sản phẩm của bạn trước khi viết code. Phản đối cách khung của bạn, thách thức tiền đề, tạo các lựa chọn triển khai. Tài liệu thiết kế nuôi mọi kỹ năng downstream. |
| `/plan-ceo-review` | **CEO / Nhà sáng lập** | Suy nghĩ lại vấn đề. Tìm sản phẩm 10 sao ẩn trong yêu cầu. Bốn chế độ: Mở rộng, Mở rộng chọn lọc, Giữ phạm vi, Giảm. |
| `/plan-eng-review` | **Quản lý Kỹ thuật** | Khóa kiến trúc, luồng dữ liệu, sơ đồ, trường hợp biên, và tests. Buộc các giả định ẩn ra ánh sáng. |
| `/plan-design-review` | **Designer cao cấp** | Đánh giá mỗi chiều thiết kế 0-10, giải thích 10 trông như thế nào, sau đó chỉnh sửa kế hoạch để đạt đến đó. Phát hiện rác AI. Tương tác — một AskUserQuestion cho mỗi lựa chọn thiết kế. |
| `/design-consultation` | **Đối tác thiết kế** | Xây dựng hệ thống thiết kế hoàn chỉnh từ đầu. Nghiên cứu cảnh quan, đề xuất rủi ro sáng tạo, tạo mockup sản phẩm thực tế. |
| `/review` | **Kỹ sư staff** | Tìm bug vượt qua CI nhưng nổ trong production. Tự động sửa những cái rõ ràng. Đánh dấu khoảng trống hoàn thiện. |
| `/investigate` | **Debugger** | Gỡ lỗi nguyên nhân gốc có hệ thống. Luật sắt: không sửa không điều tra. Theo dõi luồng dữ liệu, test giả thuyết, dừng sau 3 fix thất bại. |
| `/design-review` | **Designer biết code** | Cùng kiểm tra như /plan-design-review, sau đó sửa những gì tìm thấy. Commits nguyên tử, ảnh chụp trước/sau. |
| `/qa` | **Trưởng QA** | Test ứng dụng của bạn, tìm bug, sửa với commits nguyên tử, xác minh lại. Tự động tạo tests hồi quy cho mỗi fix. |
| `/qa-only` | **Phóng viên QA** | Cùng phương pháp như /qa nhưng chỉ báo cáo. Báo cáo bug thuần túy không thay đổi code. |
| `/cso` | **Giám đốc Bảo mật** | OWASP Top 10 + mô hình đe dọa STRIDE. Không nhiễu: 17 loại trừ dương tính giả, cổng tin cậy 8/10+, xác minh phát hiện độc lập. Mỗi phát hiện gồm kịch bản khai thác cụ thể. |
| `/ship` | **Kỹ sư phát hành** | Đồng bộ main, chạy tests, kiểm tra coverage, push, mở PR. Bootstrap frameworks test nếu bạn không có. |
| `/land-and-deploy` | **Kỹ sư phát hành** | Merge PR, đợi CI và deploy, xác minh sức khỏe production. Một lệnh từ "phê duyệt" đến "xác minh trong production". |
| `/canary` | **SRE** | Vòng lặp giám sát sau deploy. Theo dõi lỗi console, suy giảm hiệu suất, và lỗi trang. |
| `/benchmark` | **Kỹ sư hiệu suất** | Đường cơ bản thời gian tải trang, Core Web Vitals, và kích thước tài nguyên. So sánh trước/sau trên mỗi PR. |
| `/document-release` | **Nhà văn kỹ thuật** | Cập nhật tất cả tài liệu dự án phù hợp với những gì bạn vừa giao. Bắt README lỗi thời tự động. |
| `/retro` | **Quản lý Kỹ thuật** | Retro hàng tuần nhận thức đội. Phân tích theo người, chuỗi giao hàng, xu hướng sức khỏe test, cơ hội tăng trưởng. `/retro global` chạy trên tất cả dự án và công cụ AI của bạn (Claude Code, Codex, Gemini). |
| `/browse` | **Kỹ sư QA** | Trình duyệt Chromium thật, click thật, ảnh chụp thật. ~100ms mỗi lệnh. |
| `/setup-browser-cookies` | **Quản lý phiên** | Nhập cookie từ trình duyệt thật của bạn (Chrome, Arc, Brave, Edge) vào phiên headless. Test các trang xác thực. |
| `/autoplan` | **Pipeline kiểm tra** | Một lệnh, kế hoạch được kiểm tra đầy đủ. Tự động chạy kiểm tra CEO → thiết kế → kỹ thuật với nguyên tắc quyết định được mã hóa. Chỉ nổi lên quyết định thị hiếu để bạn phê duyệt. |

### Công cụ mạnh

| Kỹ năng | Những gì nó làm |
|-------|-------------|
| `/codex` | **Ý kiến thứ hai** — kiểm tra code độc lập từ OpenAI Codex CLI. Ba chế độ: kiểm tra (cổng qua/hỏng), thách thức đối nghịch, và tư vấn mở. Phân tích chéo mô hình khi cả `/review` và `/codex` đã chạy. |
| `/careful` | **Lan can an toàn** — cảnh báo trước lệnh phá hủy (rm -rf, DROP TABLE, force-push). Nói "be careful" để kích hoạt. Ghi đè bất kỳ cảnh báo nào. |
| `/freeze` | **Khóa chỉnh sửa** — giới hạn chỉnh sửa file vào một thư mục. Ngăn thay đổi ngoài phạm vi khi gỡ lỗi. |
| `/guard` | **An toàn đầy đủ** — `/careful` + `/freeze` trong một lệnh. An toàn tối đa cho work production. |
| `/unfreeze` | **Mở khóa** — xóa ranh giới `/freeze`. |
| `/setup-deploy` | **Cấu hình deploy** — setup một lần cho `/land-and-deploy`. Phát hiện nền tảng, URL production, và lệnh deploy của bạn. |
| `/gstack-upgrade` | **Tự cập nhật** — nâng cấp gstack lên phiên bản mới nhất. Phát hiện cài đặt global vs vendored, đồng bộ cả hai, hiển thị những gì thay đổi. |

**[Đi sâu với ví dụ và triết lý cho mỗi kỹ năng →](docs/skills.md)**

## Sprints song song

gstack hoạt động tốt với một sprint. Nó trở nên thú vị với mười chạy cùng lúc.

[Conductor](https://conductor.build) chạy nhiều phiên Claude Code song song — mỗi phiên trong không gian làm việc cô lập riêng. Một phiên trên `/office-hours`, một phiên khác trên `/review`, phiên thứ ba triển khai tính năng, phiên thứ tư chạy `/qa`. Tất cả cùng lúc. Cấu trúc sprint là điều làm cho song song hoạt động — không có quy trình, mười agent là mười nguồn hỗn loạn. Với quy trình, mỗi agent biết chính xác phải làm gì và khi nào dừng.

---

Miễn phí, giấy phép MIT, nguồn mở. Không có hạng cao cấp, không danh sách chờ.

Tôi đã nguồn mở cách tôi xây dựng phần mềm. Bạn có thể fork và làm nó thành của bạn.

> **Chúng tôi đang tuyển dụng.** Muốn giao 10K+ LOC/ngày và giúp củng cố gstack?
> Đến làm việc tại YC — [ycombinator.com/software](https://ycombinator.com/software)
> Lương và cổ phần cực kỳ cạnh tranh. San Francisco, khu Dogpatch.

## Tài liệu

| Tài liệu | Những gì bao gồm |
|-----|---------------|
| [Đi sâu kỹ năng](docs/skills.md) | Triết lý, ví dụ, và quy trình cho mỗi kỹ năng (bao gồm tích hợp Greptile) |
| [Đạo đức người xây dựng](ETHOS.md) | Triết lý người xây dựng: Đun sôi hồ, Tìm kiếm trước khi xây, ba lớp kiến thức |
| [Kiến trúc](ARCHITECTURE.md) | Quyết định thiết kế và nội thất hệ thống |
| [Tham khảo trình duyệt](BROWSER.md) | Tham khảo lệnh đầy đủ cho `/browse` |
| [Đóng góp](CONTRIBUTING.md) | Setup dev, testing, chế độ cộng tác viên, và chế độ dev |
| [Changelog](CHANGELOG.md) | Những gì mới trong mọi phiên bản |

## Quyền riêng tư & Telemetry

gstack bao gồm telemetry sử dụng **opt-in** để giúp cải thiện dự án. Đây chính xác những gì xảy ra:

- **Tắt mặc định.** Không gì được gửi đi bất cứ đâu trừ khi bạn nói có rõ ràng.
- **Khi chạy lần đầu,** gstack hỏi liệu bạn muốn chia sẻ dữ liệu sử dụng ẩn danh. Bạn có thể nói không.
- **Những gì được gửi (nếu bạn chọn tham gia):** tên kỹ năng, thời lượng, thành công/thất bại, phiên bản gstack, OS. Chỉ vậy.
- **Những gì không bao giờ gửi:** code, đường dẫn file, tên repo, tên branch, prompts, hoặc bất kỳ nội dung do người dùng tạo nào.
- **Thay đổi bất cứ lúc nào:** `gstack-config set telemetry off` tắt mọi thứ ngay lập tức.

Dữ liệu được lưu trữ trong [Supabase](https://supabase.com) (alternative nguồn mở cho Firebase). Schema trong [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — bạn có thể xác minh chính xác những gì được thu thập. Khóa có thể công khai Supabase trong repo là khóa công khai (như khóa API Firebase) — chính sách bảo mật cấp hàng giới hạn nó chỉ truy cập chèn.

**Phân tích cục bộ luôn có sẵn.** Chạy `gstack-analytics` để xem bảng điều khiển sử dụng cá nhân của bạn từ file JSONL cục bộ — không cần dữ liệu từ xa.

## Khắc phục sự cố

**Kỹ năng không hiển thị?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` thất bại?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**Cài đặt lỗi thời?** Chạy `/gstack-upgrade` — hoặc đặt `auto_upgrade: true` trong `~/.gstack/config.yaml`

**Người dùng Windows:** gstack hoạt động trên Windows 11 qua Git Bash hoặc WSL. Cần Node.js ngoài Bun — Bun có lỗi đã biết với vận chuyển pipe của Playwright trên Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). Máy chủ browse tự động fallback về Node.js. Đảm bảo cả `bun` và `node` có trong PATH của bạn.

**Claude nói không thể thấy kỹ năng?** Đảm bảo `CLAUDE.md` của dự án bạn có phần gstack. Thêm cái này:

```
## gstack
Sử dụng /browse từ gstack cho tất cả duyệt web. Không bao giờ dùng công cụ mcp__claude-in-chrome__*.
Kỹ năng có sẵn: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## Giấy phép

MIT. Miễn phí mãi mãi. Đi xây dựng điều gì đó.