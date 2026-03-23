<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> "아마도 12 월 이후로 코드를 한 줄도 입력하지 않은 것 같습니다. 이는 매우 큰 변화입니다." — [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), No Priors 팟캐스트, 2026 년 3 월

Karpathy 가 이렇게 말하는 것을 듣고 저는 그것이 어떻게 가능한지 알고 싶었습니다. 한 사람이 어떻게 20 명 팀처럼 프로덕트를 출시할 수 있을까요? Peter Steinberger 는 [OpenClaw](https://github.com/openclaw/openclaw) 를 구축했습니다 — GitHub 에서 247K 스타 — 본질적으로 AI 에이전트 혼자서. 혁명은 여기에 있습니다. 올바른 도구를 가진 한 명의 빌더는 전통적인 팀보다 빠르게 움직일 수 있습니다.

저는 [Garry Tan](https://x.com/garrytan), [Y Combinator](https://www.ycombinator.com/) 의 사장 겸 CEO 입니다. 저는 수천 개의 스타트업 — Coinbase, Instacart, Rippling — 과 함께 일해왔습니다 — 그들이 차고에 한 두 명 있었을 때부터입니다. YC 이전에는 Palantir 에서 최초의 엔지니어/PM/디자이너 중 한 명이었고, Posterous 를 공동 설립했으며 (Twitter 에 매각), YC 의 내부 소셜 네트워크인 Bookface 를 구축했습니다.

**gstack 이 나의 답입니다.** 저는 20 년 동안 프로덕트를 구축해왔지만, 지금만큼 많은 코드를 출시한 적은 없습니다. 지난 60 일 동안:**600,000+ 행의 프로덕션 코드** (35% 는 테스트), **하루에 10,000-20,000 행**, 파트타임으로, YC 를 풀타임으로 운영하면서. 이것은 3 개 프로젝트에서의 마지막 `/retro` 입니다:**일주일 동안 140,751 행 추가, 362 커밋, 순 약 115k 행 LOC**.

**2026 년 — 1,237 회 기여, 그리고 계속 증가 중:**

![GitHub 기여 2026 — 1,237 회 기여, 1-3 월 대폭 가속](docs/images/github-2026.png)

**2013 년 — YC 에서 Bookface 를 구축했을 때 (772 회 기여):**

![GitHub 기여 2013 — YC 에서 Bookface 를 구축했던 772 회 기여](docs/images/github-2013.png)

같은 사람. 다른 시대. 차이는 도구입니다.

**gstack 이 나의 방식입니다.** 이것은 Claude Code 를 가상 엔지니어링 팀으로 바꿉니다 — 프로덕트를 재고하는 CEO, 아키텍처를 고정하는 엔지니어링 매니저, AI 조잡함을 찾는 디자이너, 프로덕션 버그를 찾는 리뷰어, 실제 브라우저를 여는 QA 리드, OWASP + STRIDE 감사를 실행하는 보안 책임자, 그리고 PR 을 출시하는 릴리스 엔지니어. 20 명의 전문가와 8 개의 강력한 도구, 모두 슬래시 명령, 모두 Markdown, 모두 무료, MIT 라이선스.

이것은 나의 오픈 소스 소프트웨어 공장입니다. 나는 매일 그것을 사용합니다. 내가 그것을 공유하는 이유는 이러한 도구가 모든 사람이 사용할 수 있어야 하기 때문입니다.

포크하세요. 개선하세요. 당신 것으로 만드세요. 그리고 무료 오픈 소스 소프트웨어를 비판하고 싶다면 — 환영합니다, 하지만 먼저 시도해보시길 바랍니다.

**누구를 위한 것인가:**
- **창업자와 CEO** — 특히 여전히 프로덕트를 출시하고 싶은 기술적 창업자
- **Claude Code 최초 사용자** — 빈 프롬프트 대신 구조화된 역할
- **테크 리드 및 스태프 엔지니어** — 모든 PR 에서 엄격한 검토, QA, 릴리스 자동화

## 빠른 시작

1. gstack 설치 (30 초 — 아래 참조)
2. `/office-hours` 실행 — 무엇을 구축하고 있는지 설명
3. 기능 아이디어에서 `/plan-ceo-review` 실행
4. 변경 사항이 있는 브랜치에서 `/review` 실행
5. 스테이징 URL 에서 `/qa` 실행
6. 거기서 멈추세요. 이것이 당신에게 맞는지 알 수 있을 것입니다.

## 설치 — 30 초

**요구 사항:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (Windows 만)

### 1 단계: 머신에 설치

Claude Code 를 열고 이것을 붙여넣으세요. Claude 가 나머지를 처리합니다.

> gstack 설치: **`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** 실행한 후 CLAUDE.md 에 "gstack" 섹션 추가. 모든 웹 브라우징에 gstack 의 /browse 스킬 사용, mcp__claude-in-chrome__* 도구 사용 금지, 사용 가능한 스킬 나열: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade. 그런 다음 사용자에게 팀원도 사용할 수 있도록 현재 프로젝트에 gstack 을 추가할지 확인.

### 2 단계: 팀원을 위해 저장소에 추가 (선택 사항)

> 이 프로젝트에 gstack 추가: **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** 실행한 후 프로젝트의 CLAUDE.md 에 "gstack" 섹션 추가. 모든 웹 브라우징에 gstack 의 /browse 스킬 사용, mcp__claude-in-chrome__* 도구 사용 금지, 사용 가능한 스킬 나열: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, 그리고 gstack 스킬이 작동하지 않으면 `cd .claude/skills/gstack && ./setup` 을 실행하여 바이너리를 빌드하고 스킬을 등록하도록 Claude 에 지시.

실제 파일은 저장소에 커밋됩니다 (서브모듈 아님). 따라서 `git clone` 이 작동합니다. 모든 것은 `.claude/` 안에 있습니다. PATH 를 건드리거나 백그라운드에서 실행되는 것은 없습니다.

### Codex, Gemini CLI 또는 Cursor

gstack 은 [SKILL.md 표준](https://github.com/anthropics/claude-code) 을 지원하는 모든 에이전트에서 작동합니다. 스킬은 `.agents/skills/` 에 있으며 자동으로 검색됩니다.

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

또는 setup 이 설치된 에이전트를 자동 감지하도록 합니다:

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

이것은 사용 가능한 것에 따라 `~/.claude/skills/gstack` 및/또는 `~/.codex/skills/gstack` 에 설치됩니다. 28 개 스킬 모두 지원되는 모든 에이전트에서 작동합니다. 후크 기반 보안 스킬 (careful, freeze, guard) 은 비 Claude 호스트에서 인라인 보안 권고문을 사용합니다.

## 작동 방식 보기

```
당신: 내 캘린더용 일일 브리핑 앱을 만들고 싶습니다.
당신: /office-hours
Claude: [고통에 대해 질문 — 구체적인 예시, 가정이 아님]

당신: 여러 Google 캘린더, 오래된 정보의 이벤트,
        잘못된 위치. 준비에 영원히 걸리고 결과는
        충분히 좋지 않아요...

Claude: 프레임링에 이의를 제기하겠습니다. "일일
        브리핑 앱"이라고 말했습니다. 하지만 실제로
        설명한 것은 개인 AI 참모입니다.
        [당신이 설명하고 있다는 것을 몰랐던 5 가지 능력 추출]
        [4 가지 전제에 도전 — 동의,不同意 또는 조정]
        [노력 추정치가 있는 3 가지 구현 접근 방식 생성]
        권장: 내일 가장 좁은 쐐기를 출시하고 실제 사용에서
        배우세요. 전체 비전은 3 개월 프로젝트 — 실제로
        작동하는 일일 브리핑부터 시작하세요.
        [디자인 문서 작성 → 하류 스킬에 자동 공급]

당신: /plan-ceo-review
        [디자인 문서 읽기, 범위 도전, 10 섹션 검토 실행]

당신: /plan-eng-review
        [데이터 흐름, 상태 머신, 오류 경로의 ASCII 다이어그램]
        [테스트 매트릭스, 실패 모드, 보안 우려]

당신: 계획 승인. 계획 모드 종료.
        [11 개 파일에 2,400 행 작성. 약 8 분.]

당신: /review
        [자동 수정] 2 문제. [질문] 경쟁 상태 → 수정 승인.

당신: /qa https://staging.myapp.com
        [실제 브라우저 열기, 플로우 클릭, 버그 발견 및 수정]

당신: /ship
        테스트: 42 → 51 (+9 새). PR: github.com/you/app/pull/42
```

당신은 "일일 브리핑 앱"이라고 말했습니다. 에이전트는 "당신은 AI 참모를 구축하고 있습니다"라고 말했습니다 — 그것은 당신의 기능 요청이 아니라 당신의 고통에 귀 기울였기 때문입니다. 8 개의 명령, 엔드 투 엔드. 이것은 코파일럿이 아닙니다. 이것은 팀입니다.

## 스프린트

gstack 은 프로세스이며 도구의 모음이 아닙니다. 스킬은 스프린트가 실행되는 순서대로 실행됩니다:

**생각 → 계획 → 구축 → 검토 → 테스트 → 출시 → 성찰**

각 스킬은 다음에 공급합니다. `/office-hours` 는 `/plan-ceo-review` 가 읽는 디자인 문서를 작성합니다. `/plan-eng-review` 는 `/qa` 가 받는 테스트 계획을 작성합니다. `/review` 는 `/ship` 이 수정되었는지 확인하는 버그를 잡습니다. 모든 단계가 이전 단계를 알기 때문에 아무 것도 빠지지 않습니다.

| 스킬 | 당신의 전문가 | 그들이 하는 일 |
|-------|----------------|--------------|
| `/office-hours` | **YC 오피스 아워** | 여기서 시작. 코드 작성 전 제품을 재구성하는 6 가지 필수 질문. 당신의 프레임링에 이의를 제기하고, 전제에 도전하며, 구현 대안을 생성합니다. 디자인 문서는 모든 하류 스킬에 공급됩니다. |
| `/plan-ceo-review` | **CEO / 창업자** | 문제를 재고합니다. 요청 안에 숨겨진 10 스타 제품을 찾습니다. 4 가지 모드: 확장, 선택적 확장, 범위 유지, 축소. |
| `/plan-eng-review` | **엔지니어링 매니저** | 아키텍처, 데이터 흐름, 다이어그램, 엣지 케이스, 테스트를 고정합니다. 숨겨진 가정을 표면으로 끌어올립니다. |
| `/plan-design-review` | **시니어 디자이너** | 각 디자인 차원을 0-10 으로 평가하고, 10 이 무엇인지 설명한 후,そこに도착하기 위해 계획을 편집합니다. AI 조잡함 감지. 인터랙티브 — 디자인 선택당 하나씩 AskUserQuestion. |
| `/design-consultation` | **디자인 파트너** | 처음부터 완전한 디자인 시스템을 구축합니다. 환경을 조사하고, 창의적 위험을 제안하며, 현실적인 제품 모업을 생성합니다. |
| `/review` | **스태프 엔지니어** | CI 를 통과하지만 프로덕션에서 폭발하는 버그를 찾습니다. 명확한 것을 자동 수정합니다. 완전성 격차를 플래그합니다. |
| `/investigate` | **디버거** | 체계적인 근본 원인 디버깅. 철칙: 조사 없이 수정 없음. 데이터 흐름을 추적하고, 가설을 테스트하며, 3 번의 실패한 수정 후 중지합니다. |
| `/design-review` | **코딩하는 디자이너** | /plan-design-review 와 동일한 감사 후 발견된 것을 수정합니다. 원자 커밋, 전후 스크린샷. |
| `/qa` | **QA 리드** | 앱을 테스트하고, 버그를 찾고, 원자 커밋으로 수정하고, 재검증합니다. 모든 수정에 대해 회귀 테스트를 자동 생성합니다. |
| `/qa-only` | **QA 리포터** | /qa 와 동일한 방법론이지만 보고서만. 코드 변경 없는 순수 버그 보고서. |
| `/cso` | **최고 보안 책임자** | OWASP Top 10 + STRIDE 위협 모델. 제로 노이즈: 17 개 위양성 제외, 8/10+ 신뢰도 게이트, 독립적 발견 검증. 각 발견은 구체적인 악용 시나리오를 포함합니다. |
| `/ship` | **릴리스 엔지니어** | main 을 동기화하고, 테스트를 실행하고, 커버리지를 감사하고, 푸시하고, PR 을 엽니다. 테스트 프레임워크가 없으면 부트스트랩합니다. |
| `/land-and-deploy` | **릴리스 엔지니어** | PR 을 병합하고, CI 와 배포를 기다리고, 프로덕션 건강을 검증합니다. "승인됨"에서 "프로덕션 검증됨"까지 하나의 명령. |
| `/canary` | **SRE** | 배포 후 모니터링 루프. 콘솔 오류, 성능 저하, 페이지 실패를 감시합니다. |
| `/benchmark` | **성능 엔지니어** | 페이지 로드 시간, Core Web Vitals, 리소스 크기의 기준선. 모든 PR 에서 전후를 비교합니다. |
| `/document-release` | **기술 작가** | 방금 출시한 것과 일치하도록 모든 프로젝트 문서를 업데이트합니다. 오래된 README 를 자동 감지합니다. |
| `/retro` | **엔지니어링 매니저** | 팀 인식 주간 회고. 개인별 내역, 출시 스트릭, 테스트 건강 트렌드, 성장 기회. `/retro global` 은 모든 프로젝트와 AI 도구 (Claude Code, Codex, Gemini) 에서 실행됩니다. |
| `/browse` | **QA 엔지니어** | 실제 Chromium 브라우저, 실제 클릭, 실제 스크린샷. 명령당 약 100ms. |
| `/setup-browser-cookies` | **세션 매니저** | 실제 브라우저 (Chrome, Arc, Brave, Edge) 에서 쿠키를 헤드리스 세션으로 가져옵니다. 인증된 페이지를 테스트합니다. |
| `/autoplan` | **검토 파이프라인** | 하나의 명령, 완전히 검토된 계획. CEO → 디자인 → 엔지니어링 검토를 자동 실행, 인코딩된 결정 원칙. 승인을 위한 취향 결정만 표면화합니다. |

### 파워 도구

| 스킬 | 그것이 하는 일 |
|-------|-------------|
| `/codex` | **두 번째 의견** — OpenAI Codex CLI 의 독립 코드 검토. 3 가지 모드: 검토 (통과/실패 게이트), 적대적 도전, 개방형 상담. `/review` 와 `/codex` 가 모두 실행될 때 교차 모델 분석. |
| `/careful` | **안전 가드레일** — 파괴적 명령 (rm -rf, DROP TABLE, 강제 푸시) 전에 경고. "be careful"라고 말하여 활성화. 모든 경고 재정의. |
| `/freeze` | **편집 잠금** — 파일 편집을 한 디렉토리로 제한. 디버깅 중 범위 밖의 우발적 변경 방지. |
| `/guard` | **완전 안전** — 하나의 명령으로 `/careful` + `/freeze`. 프로덕션 작업을 위한 최대 안전. |
| `/unfreeze` | **잠금 해제** — `/freeze` 경계 제거. |
| `/setup-deploy` | **배포 구성자** — `/land-and-deploy` 의 일회성 설정. 플랫폼, 프로덕션 URL, 배포 명령 감지. |
| `/gstack-upgrade` | **셀프 업데이터** — gstack 을 최신으로 업그레이드. 글로벌 대 벤더드 설치 감지, 둘 다 동기화, 변경 사항 표시. |

**[각 스킬에 대한 예시와 철학의 심층 분석 →](docs/skills.md)**

## 병렬 스프린트

gstack 은 하나의 스프린트에서 잘 작동합니다. 10 개가 동시에 실행되면 흥미로워집니다.

[Conductor](https://conductor.build) 는 여러 Claude Code 세션을 병렬로 실행합니다 — 각각 고유한 격리된 워크스페이스에서. `/office-hours` 에서 한 세션, `/review` 에서 다른 세션, 세 번째는 기능 구현, 네 번째는 `/qa` 실행. 모두 동시에. 스프린트 구조가 병렬 처리를 작동하게 합니다 — 프로세스가 없으면 10 개의 에이전트는 10 개의 혼돈 원천입니다. 프로세스가 있으면 각 에이전트는 정확히 무엇을 해야 하는지, 언제 멈춰야 하는지 압니다.

---

무료, MIT 라이선스, 오픈 소스. 프리미엄 티어 없음, 대기열 없음.

내가 소프트웨어를 구축하는 방식을 오픈 소스화했습니다. 포크하여 당신 것으로 만들 수 있습니다.

> **채용 중.** 하루 10K+ LOC 를 출시하고 gstack 강화를 도와주시겠습니까?
> YC 에서 일하기 — [ycombinator.com/software](https://ycombinator.com/software)
> 매우 경쟁력 있는 급여와 지분. 샌프란시스코, Dogpatch 지구.

## 문서

| 문서 | 다루는 내용 |
|-----|---------------|
| [스킬 심층 분석](docs/skills.md) | 각 스킬의 철학, 예시, 워크플로우 (Greptile 통합 포함) |
| [빌더 정신](ETHOS.md) | 빌더 철학: 호수 끓이기, 구축 전 검색, 3 층 지식 |
| [아키텍처](ARCHITECTURE.md) | 디자인 결정 및 시스템 내부 |
| [브라우저 참조](BROWSER.md) | `/browse` 의 전체 명령 참조 |
| [기여](CONTRIBUTING.md) | 개발 설정, 테스트, 기여자 모드 및 개발 모드 |
| [변경 로그](CHANGELOG.md) | 모든 버전의 새로운 기능 |

## 개인정보 및 원격 측정

gstack 에는 프로젝트 개선을 돕는 **옵트인** 사용 원격 측정이 포함되어 있습니다. 정확히 다음과 같습니다:

- **기본값은 꺼짐.** 명시적으로 "예"라고 말하지 않는 한 아무 것도 전송되지 않습니다.
- **첫 실행 시,** gstack 이 익명 사용 데이터를 공유할지 확인합니다. "아니오"라고 할 수 있습니다.
- **전송되는 내용 (옵트인한 경우):** 스킬 이름, 기간, 성공/실패, gstack 버전, OS. 그것뿐.
- **절대 전송되지 않는 내용:** 코드, 파일 경로, 저장소 이름, 브랜치 이름, 프롬프트 또는 사용자 생성 콘텐츠.
- **언제든지 변경:** `gstack-config set telemetry off` 는 모든 것을 즉시 비활성화합니다.

데이터는 [Supabase](https://supabase.com) (오픈 소스 Firebase 대안) 에 저장됩니다. 스키마는 [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) 에 있습니다 — 무엇이 수집되는지 정확히 확인할 수 있습니다. 저장소의 Supabase 게시 가능 키는 공개 키 (Firebase API 키와 같음) 입니다 — 행 수준 보안 정책은 삽입 전용 액세스로 제한합니다.

**로컬 분석은 항상 사용 가능합니다.** `gstack-analytics` 를 실행하여 로컬 JSONL 파일에서 개인 사용 대시보드를 확인하세요 — 원격 데이터 불필요.

## 문제 해결

**스킬이 표시되지 않음?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` 실패?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**설치가 오래됨?** `/gstack-upgrade` 실행 — 또는 `~/.gstack/config.yaml` 에서 `auto_upgrade: true` 설정.

**Windows 사용자:** gstack 은 Git Bash 또는 WSL 을 통해 Windows 11 에서 작동합니다.Bun 외에 Node.js 가 필요합니다 — Bun 은 Windows 에서 Playwright 의 파이프 전송에 알려진 버그가 있습니다 ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). 브라우즈 서버는 자동으로 Node.js 로 폴백합니다. `bun` 과 `node` 가 모두 PATH 에 있는지 확인하세요.

**Claude 가 스킬을 볼 수 없다고 함?** 프로젝트의 `CLAUDE.md` 에 gstack 섹션이 있는지 확인하세요. 이것을 추가:

```
## gstack
모든 웹 브라우징에 gstack 의 /browse 사용. mcp__claude-in-chrome__* 도구 사용 금지.
사용 가능한 스킬: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /careful, /freeze, /guard,
/unfreeze, /gstack-upgrade.
```

## 라이선스

MIT. 영원히 무료. 무언가를 구축하러 가세요.