# gstack

> "아마 12월 이후로는 사실상 한 줄의 코드도 직접 치지 않은 것 같아요. 엄청난 변화죠." - [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/), No Priors podcast, 2026년 3월

Karpathy가 이 말을 하는 걸 듣고, 저는 그 방법이 궁금해졌습니다. 어떻게 한 사람이 스무 명짜리 팀처럼 제품을 내놓을 수 있을까요? Peter Steinberger는 [OpenClaw](https://github.com/openclaw/openclaw)를 AI 에이전트와 함께 사실상 혼자서 만들어 [GitHub 스타 247K](https://github.com/openclaw/openclaw)를 얻었습니다. 혁명은 이미 시작됐습니다. 적절한 도구만 있으면, 한 명의 빌더가 전통적인 팀보다 더 빠르게 움직일 수 있습니다.

저는 [Y Combinator](https://www.ycombinator.com/)의 President & CEO인 [Garry Tan](https://x.com/garrytan)입니다. 저는 Coinbase, Instacart, Rippling을 비롯한 수천 개 스타트업과 함께 일해 왔고, 그들이 차고에서 1~2명으로 시작하던 시절을 봐 왔습니다. YC 이전에는 Palantir의 초기 엔지니어/PM/디자이너 중 한 명이었고, Posterous를 공동 창업해 Twitter에 매각했으며, YC 내부 소셜 네트워크인 Bookface를 만들었습니다.

**gstack은 제가 내놓은 답입니다.** 저는 20년 동안 제품을 만들어 왔고, 지금은 그 어느 때보다도 많은 코드를 출하하고 있습니다. 지난 60일 동안: **프로덕션 코드 600,000줄 이상**(그중 35%는 테스트), **하루 10,000~20,000줄**, YC를 풀타임으로 운영하면서도 파트타임으로 해냈습니다. 최근 3개 프로젝트에 대한 제 마지막 `/retro`는 이랬습니다: **한 주 동안 140,751줄 추가, 362 commits, 순증 LOC 약 115k**.

**2026년 - 현재까지 1,237 contributions:**

![GitHub contributions 2026 - 1,237 contributions, 1~3월에 폭발적 증가](docs/images/github-2026.png)

**2013년 - YC에서 Bookface를 만들던 시절 (772 contributions):**

![GitHub contributions 2013 - YC에서 Bookface를 만들던 시절 772 contributions](docs/images/github-2013.png)

같은 사람입니다. 시대가 달라졌습니다. 차이는 도구입니다.

**gstack이 바로 그 방법입니다.** gstack은 Claude Code를 가상 엔지니어링 팀으로 바꿉니다. 제품을 다시 생각하게 만드는 CEO, 아키텍처를 고정하는 엔지니어링 매니저, AI 냄새 나는 디자인을 걸러내는 디자이너, 프로덕션 버그를 잡는 리뷰어, 실제 브라우저를 여는 QA 리드, OWASP + STRIDE 감사를 수행하는 보안 책임자, PR을 출하하는 릴리스 엔지니어까지. 23명의 전문가와 8개의 파워 툴이 모두 슬래시 명령으로, 모두 Markdown으로, 모두 무료 MIT 라이선스로 제공됩니다.

이건 제 오픈소스 소프트웨어 공장입니다. 저는 매일 이걸 씁니다. 이런 도구는 모두가 사용할 수 있어야 한다고 생각해서 공개합니다.

포크하세요. 개선하세요. 당신만의 것으로 만드세요. 무료 오픈소스 소프트웨어를 싫어하고 싶다면 말리진 않겠지만, 그전에 한 번은 직접 써보셨으면 합니다.

**이런 분들께 적합합니다:**
- **창업자와 CEO** - 특히 직접 제품을 계속 내놓고 싶은 기술 창업자
- **Claude Code를 처음 쓰는 사람** - 빈 프롬프트 대신 구조화된 역할이 필요한 경우
- **Tech lead와 Staff engineer** - 모든 PR에 엄격한 리뷰, QA, 릴리스 자동화를 붙이고 싶은 경우

## 빠른 시작

1. gstack을 설치합니다. (30초 - 아래 참고)
2. `/office-hours`를 실행해 무엇을 만들고 있는지 설명합니다.
3. 어떤 기능 아이디어든 `/plan-ceo-review`를 실행합니다.
4. 변경이 있는 브랜치에서 `/review`를 실행합니다.
5. 스테이징 URL에 `/qa`를 실행합니다.
6. 여기까지만 해보세요. 이 도구가 자신에게 맞는지 바로 감이 올 겁니다.

## 설치 - 30초

**요구 사항:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (Windows만 해당)

### 1단계: 내 컴퓨터에 설치하기

Claude Code를 열고 아래 문장을 붙여 넣으세요. 나머지는 Claude가 처리합니다.

> gstack 설치: **`git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** 를 실행한 다음, `CLAUDE.md`에 "gstack" 섹션을 추가하고 모든 웹 브라우징에는 gstack의 `/browse` 스킬을 사용하며 `mcp__claude-in-chrome__*` 도구는 절대 사용하지 말라고 적어 주세요. 또한 사용 가능한 스킬 `/office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /design-shotgun, /design-html, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /connect-chrome, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /plan-devex-review, /devex-review, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, /learn` 를 나열해 주세요. 그런 다음 팀원도 쓰도록 현재 프로젝트에도 gstack을 추가할지 사용자에게 물어보세요.

### 2단계: 팀원도 받을 수 있게 저장소에 추가하기 (선택)

> 이 프로젝트에 gstack 추가: **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** 를 실행한 다음, 이 프로젝트의 `CLAUDE.md`에 "gstack" 섹션을 추가하고, 모든 웹 브라우징에는 gstack의 `/browse` 스킬을 사용하며 `mcp__claude-in-chrome__*` 도구는 절대 사용하지 말라고 적어 주세요. 사용 가능한 스킬 `/office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /design-shotgun, /design-html, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /connect-chrome, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /plan-devex-review, /devex-review, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, /learn` 를 나열하고, gstack 스킬이 동작하지 않으면 `cd .claude/skills/gstack && ./setup` 을 실행해 바이너리를 빌드하고 스킬을 등록하라고 Claude에게 알려 주세요.

실제 파일이 저장소에 커밋되므로(서브모듈 아님) `git clone`만으로 바로 동작합니다. 모든 것은 `.claude/` 내부에만 들어갑니다. PATH를 건드리거나 백그라운드 프로세스를 띄우지 않습니다.

> **기여 예정이거나 전체 히스토리가 필요한가요?** 위 명령은 빠른 설치를 위해 `--depth 1`을 사용합니다. 기여할 계획이 있거나 전체 git 히스토리가 필요하다면 전체 클론을 사용하세요.
> ```bash
> git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
> ```

### OpenClaw

OpenClaw는 ACP를 통해 Claude Code 세션을 생성하므로, Claude Code에 gstack이 설치되어 있으면 모든 gstack 스킬이 그대로 동작합니다. 아래 문장을 OpenClaw 에이전트에 붙여 넣으세요.

> gstack 설치: Claude Code용으로 gstack을 설치하려면 `git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup` 을 실행하세요. 그런 다음 `AGENTS.md`에 "Coding Tasks" 섹션을 추가하고 다음을 적으세요: 코딩 작업을 위해 Claude Code 세션을 생성할 때는 세션에 gstack 스킬을 사용하라고 지시한다. 다음 예시를 포함한다 - 보안 감사: "Load gstack. Run /cso", 코드 리뷰: "Load gstack. Run /review", URL QA 테스트: "Load gstack. Run /qa https://...", 기능을 끝까지 구현: "Load gstack. Run /autoplan, implement the plan, then run /ship", 구현 전에 계획 수립: "Load gstack. Run /office-hours then /autoplan. Save the plan, don't implement."

**설정이 끝나면 OpenClaw 에이전트와 자연스럽게 대화하면 됩니다:**

| 당신이 말하는 내용 | 실제 동작 |
|---------|-------------|
| "README의 오타를 고쳐줘" | 간단한 작업 - gstack 없이 Claude Code 세션으로 처리 |
| "이 저장소 보안 감사를 돌려줘" | Claude Code를 생성하며 `Run /cso` 실행 |
| "알림 기능 하나 만들어줘" | Claude Code를 생성하며 `/autoplan -> 구현 -> /ship` 실행 |
| "v2 API 재설계를 같이 계획해줘" | Claude Code를 생성하며 `/office-hours -> /autoplan` 실행 후 계획 저장 |

[docs/OPENCLAW.md](docs/OPENCLAW.md)에서 고급 디스패치 라우팅과 gstack-lite/gstack-full 프롬프트 템플릿을 확인할 수 있습니다.

### 다른 AI 에이전트

gstack은 Claude만이 아니라 8개의 AI 코딩 에이전트에서 동작합니다. 설치 스크립트가 어떤 에이전트가 설치되어 있는지 자동으로 감지합니다.

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup
```

특정 에이전트를 지정하려면 `./setup --host <name>`을 사용하세요.

| 에이전트 | 플래그 | 스킬 설치 위치 |
|-------|------|-------------------|
| OpenAI Codex CLI | `--host codex` | `~/.codex/skills/gstack-*/` |
| OpenCode | `--host opencode` | `~/.config/opencode/skills/gstack-*/` |
| Cursor | `--host cursor` | `~/.cursor/skills/gstack-*/` |
| Factory Droid | `--host factory` | `~/.factory/skills/gstack-*/` |
| Slate | `--host slate` | `~/.slate/skills/gstack-*/` |
| Kiro | `--host kiro` | `~/.kiro/skills/gstack-*/` |

**다른 에이전트도 지원하고 싶나요?** [docs/ADDING_A_HOST.md](docs/ADDING_A_HOST.md)를 보세요. TypeScript 설정 파일 하나면 되고, 코드 수정은 필요 없습니다.

## 실제 동작 예시

```text
당신:    내 캘린더용 데일리 브리핑 앱을 만들고 싶어.
당신:    /office-hours
Claude: [가설 말고 실제 사례를 중심으로 문제를 질문함]

당신:    Google 캘린더가 여러 개고, 이벤트 정보가 오래됐고, 장소도 자주 틀려.
          준비 시간이 너무 오래 걸리고 결과물도 만족스럽지 않아...

Claude: 너의 프레이밍부터 다시 보자. 너는 "데일리 브리핑 앱"이라고 했지만,
        실제로 설명한 건 개인 비서장(chief of staff) AI야.
        [네가 스스로 인지하지 못했던 5개의 핵심 역량을 추출]
        [4개의 전제를 문제 삼고, 네가 동의/반박/조정]
        [구현 방식 3가지를 공수 추정과 함께 제시]
        RECOMMENDATION: 가장 좁은 쐐기부터 내일 바로 출하하자.
        전체 비전은 3개월짜리 프로젝트지만, 먼저 정말 동작하는
        데일리 브리핑부터 시작하는 게 맞아.
        [디자인 문서를 작성하고 이후 스킬로 자동 연결]

당신:    /plan-ceo-review
          [디자인 문서를 읽고 범위를 다시 검토한 뒤 10개 섹션 리뷰 수행]

당신:    /plan-eng-review
          [데이터 흐름, 상태 머신, 오류 경로에 대한 ASCII 다이어그램]
          [테스트 매트릭스, 실패 모드, 보안 이슈]

당신:    계획 승인. 계획 모드 종료.
          [11개 파일에 2,400줄 작성. 약 8분.]

당신:    /review
          [AUTO-FIXED] 이슈 2개 자동 수정. [ASK] 경쟁 상태 문제 - 수정 여부를 물음.

당신:    /qa https://staging.myapp.com
          [실제 브라우저를 열고 플로우를 클릭해 보며 버그를 찾고 수정]

당신:    /ship
          Tests: 42 -> 51 (+9 new). PR: github.com/you/app/pull/42
```

당신은 "데일리 브리핑 앱"이라고 말했지만, 에이전트는 "당신은 개인 비서장 AI를 만들고 있다"고 말합니다. 기능 요청이 아니라 고통의 본질을 들었기 때문입니다. 여덟 개 명령으로 끝에서 끝까지 이어집니다. 이건 코파일럿이 아니라 팀입니다.

## 스프린트

gstack은 단순한 도구 모음이 아니라 프로세스입니다. 스킬은 실제 스프린트 순서대로 실행됩니다.

**Think -> Plan -> Build -> Review -> Test -> Ship -> Reflect**

각 스킬은 다음 스킬로 이어집니다. `/office-hours`는 디자인 문서를 작성하고, `/plan-ceo-review`는 그 문서를 읽습니다. `/plan-eng-review`는 테스트 계획을 쓰고, `/qa`는 그 내용을 이어받습니다. `/review`는 버그를 잡아내고, `/ship`은 그 수정이 반영됐는지 검증합니다. 모든 단계가 이전 단계를 알고 있기 때문에 중요한 것이 중간에 빠지지 않습니다.

| 스킬 | 당신의 전문가 | 하는 일 |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | 여기서 시작합니다. 코드를 쓰기 전에 제품을 다시 보게 만드는 6개의 강제 질문입니다. 현재 프레이밍에 반박하고, 전제를 흔들고, 구현 대안을 제시합니다. 작성된 디자인 문서는 이후 모든 스킬로 전달됩니다. |
| `/plan-ceo-review` | **CEO / Founder** | 문제를 다시 정의합니다. 요청 안에 숨어 있는 10점짜리 제품을 찾아냅니다. 네 가지 모드: Expansion, Selective Expansion, Hold Scope, Reduction. |
| `/plan-eng-review` | **Eng Manager** | 아키텍처, 데이터 흐름, 다이어그램, 엣지 케이스, 테스트를 고정합니다. 숨어 있던 가정을 밖으로 끌어냅니다. |
| `/plan-design-review` | **Senior Designer** | 각 디자인 차원을 0-10으로 평가하고, 10점이 무엇인지 설명한 뒤, 그 수준으로 가도록 계획을 수정합니다. AI Slop 감지 포함. 인터랙티브하며 디자인 선택마다 AskUserQuestion 한 번씩 사용합니다. |
| `/plan-devex-review` | **Developer Experience Lead** | 인터랙티브 DX 리뷰입니다. 개발자 페르소나를 탐색하고, 경쟁 제품의 TTHW와 비교하며, 마법 같은 첫 경험을 설계하고, 마찰 지점을 단계별로 추적합니다. 세 가지 모드: DX EXPANSION, DX POLISH, DX TRIAGE. 20-45개의 강제 질문을 던집니다. |
| `/design-consultation` | **Design Partner** | 완전한 디자인 시스템을 처음부터 구축합니다. 시장을 조사하고, 창의적인 리스크를 제안하며, 현실적인 제품 목업을 생성합니다. |
| `/review` | **Staff Engineer** | CI는 통과하지만 프로덕션에서 터지는 버그를 찾습니다. 명백한 문제는 자동 수정하고, 완성도 공백은 표시합니다. |
| `/investigate` | **Debugger** | 체계적인 근본 원인 디버깅입니다. 철칙: 조사 없이 수정하지 않는다. 데이터 흐름을 추적하고, 가설을 검증하며, 3번 수정에 실패하면 멈춥니다. |
| `/design-review` | **Designer Who Codes** | `/plan-design-review`와 동일한 감사를 실행한 뒤, 발견한 문제를 직접 고칩니다. 원자적 커밋과 before/after 스크린샷을 남깁니다. |
| `/devex-review` | **DX Tester** | 실제 개발자 경험을 감시합니다. 문서를 따라가고, getting started 플로우를 실행하고, TTHW를 측정하고, 오류를 스크린샷으로 남깁니다. `/plan-devex-review` 점수와 비교해 계획과 현실이 얼마나 맞는지 보여줍니다. |
| `/design-shotgun` | **Design Explorer** | 여러 AI 디자인 변형을 만들고, 브라우저 비교 보드를 열어 방향을 승인할 때까지 반복합니다. 선호도를 학습하는 taste memory가 포함됩니다. |
| `/design-html` | **Design Engineer** | 계산된 텍스트 레이아웃용 Pretext를 사용해 프로덕션 수준 HTML을 생성합니다. 승인된 목업, CEO 계획, 디자인 리뷰, 혹은 완전한 빈 상태에서 시작할 수 있습니다. 창 크기를 바꾸면 텍스트가 다시 흐르고, 높이도 콘텐츠에 맞게 조정됩니다. 디자인 유형에 따라 적절한 Pretext 패턴을 고르는 스마트 API 라우팅과 React/Svelte/Vue 프레임워크 감지도 포함됩니다. |
| `/qa` | **QA Lead** | 앱을 테스트하고, 버그를 찾고, 원자적 커밋으로 수정하고, 다시 검증합니다. 모든 수정에 대해 회귀 테스트를 자동 생성합니다. |
| `/qa-only` | **QA Reporter** | `/qa`와 같은 방법론을 쓰되 보고만 합니다. 코드 변경 없이 순수 버그 리포트만 제공합니다. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + STRIDE 위협 모델을 적용합니다. 노이즈를 최소화하기 위해 17개의 false positive 제외 규칙, 8/10 이상의 신뢰도 게이트, 독립적인 finding 검증을 사용합니다. 각 finding에는 구체적인 공격 시나리오가 들어갑니다. |
| `/ship` | **Release Engineer** | main을 동기화하고, 테스트를 실행하고, 커버리지를 점검하고, push한 뒤 PR을 엽니다. 테스트 프레임워크가 없으면 직접 부트스트랩합니다. |
| `/land-and-deploy` | **Release Engineer** | PR을 머지하고, CI와 배포를 기다리고, 프로덕션 상태를 검증합니다. "승인됨"에서 "프로덕션 검증 완료"까지 한 번에 갑니다. |
| `/canary` | **SRE** | 배포 후 모니터링 루프입니다. 콘솔 오류, 성능 회귀, 페이지 실패를 감시합니다. |
| `/benchmark` | **Performance Engineer** | 페이지 로드 시간, Core Web Vitals, 리소스 크기의 기준선을 측정합니다. 모든 PR에서 before/after를 비교합니다. |
| `/document-release` | **Technical Writer** | 방금 출하한 내용에 맞춰 프로젝트 문서를 모두 갱신합니다. 오래된 README도 자동으로 잡아냅니다. |
| `/retro` | **Eng Manager** | 팀 단위 주간 회고입니다. 사람별 분석, 출하 연속 기록, 테스트 건강도 추세, 성장 기회를 보여줍니다. `/retro global`은 여러 프로젝트와 AI 도구(Claude Code, Codex, Gemini)를 가로질러 실행됩니다. |
| `/browse` | **QA Engineer** | 에이전트에게 눈을 달아 줍니다. 실제 Chromium 브라우저, 실제 클릭, 실제 스크린샷. 명령당 약 100ms입니다. `/open-gstack-browser`는 사이드바, anti-bot stealth, 자동 모델 라우팅을 갖춘 GStack Browser를 실행합니다. |
| `/setup-browser-cookies` | **Session Manager** | 실제 브라우저(Chrome, Arc, Brave, Edge)의 쿠키를 헤드리스 세션으로 가져옵니다. 인증이 필요한 페이지를 테스트할 수 있습니다. |
| `/autoplan` | **Review Pipeline** | 한 번의 명령으로 검토가 완료된 계획을 만듭니다. CEO -> 디자인 -> 엔지니어링 리뷰를 코드화된 의사결정 원칙으로 자동 실행하고, 취향이 필요한 결정만 사용자 승인을 요청합니다. |
| `/learn` | **Memory** | gstack이 세션 간에 학습한 내용을 관리합니다. 프로젝트별 패턴, 함정, 선호도를 검토하고 검색하고 정리하고 내보낼 수 있습니다. 세션이 쌓일수록 코드베이스 이해도도 함께 쌓입니다. |

### 어떤 리뷰를 써야 할까요?

| 무엇을 만드는가 | 계획 단계 (코드 전) | 실서비스 감사 (출하 후) |
|-----------------|--------------------------|----------------------------|
| **최종 사용자용** (UI, 웹 앱, 모바일) | `/plan-design-review` | `/design-review` |
| **개발자용** (API, CLI, SDK, 문서) | `/plan-devex-review` | `/devex-review` |
| **아키텍처용** (데이터 흐름, 성능, 테스트) | `/plan-eng-review` | `/review` |
| **위 모든 것** | `/autoplan` (CEO -> 디자인 -> 엔지니어링 -> DX를 자동 감지해 실행) | - |

### 파워 툴

| 스킬 | 하는 일 |
|-------|-------------|
| `/codex` | **Second Opinion** - OpenAI Codex CLI가 독립적인 코드 리뷰를 수행합니다. 세 가지 모드: review (pass/fail gate), adversarial challenge, open consultation. `/review`와 `/codex`가 모두 실행되면 교차 모델 분석도 제공합니다. |
| `/careful` | **Safety Guardrails** - 파괴적인 명령(`rm -rf`, `DROP TABLE`, force-push`) 전에 경고합니다. "be careful"이라고 말하면 활성화됩니다. 어떤 경고든 무시할 수는 있습니다. |
| `/freeze` | **Edit Lock** - 파일 수정 범위를 한 디렉터리로 제한합니다. 디버깅 중 범위 밖 변경을 막아 줍니다. |
| `/guard` | **Full Safety** - `/careful` + `/freeze`를 한 번에 켭니다. 프로덕션 작업에서 가장 안전한 모드입니다. |
| `/unfreeze` | **Unlock** - `/freeze` 경계를 해제합니다. |
| `/open-gstack-browser` | **GStack Browser** - 사이드바, anti-bot stealth, 자동 모델 라우팅(Sonnet은 액션, Opus는 분석), 원클릭 쿠키 가져오기, Claude Code 연동이 포함된 GStack Browser를 실행합니다. 페이지를 정리하고, 스마트 스크린샷을 찍고, CSS를 수정하고, 정보를 터미널로 다시 넘길 수 있습니다. |
| `/setup-deploy` | **Deploy Configurator** - `/land-and-deploy`를 위한 1회성 설정입니다. 플랫폼, 프로덕션 URL, 배포 명령을 감지합니다. |
| `/gstack-upgrade` | **Self-Updater** - gstack을 최신 버전으로 업그레이드합니다. 전역 설치인지 vendored 설치인지 감지하고 둘 다 동기화하며 변경 사항을 보여줍니다. |

**[모든 스킬의 예시와 철학 자세히 보기](docs/skills.md)**

## 병렬 스프린트

gstack은 하나의 스프린트에서도 잘 동작합니다. 하지만 동시에 열 개를 돌리면 진가가 드러납니다.

**디자인이 중심에 있습니다.** `/design-consultation`은 디자인 시스템을 처음부터 구축하고, 시장을 조사하고, 창의적인 리스크를 제안하며, `DESIGN.md`를 작성합니다. `/design-shotgun`은 여러 시각적 변형을 만들고 비교 보드를 열어 방향을 고를 수 있게 합니다. `/design-html`은 승인된 목업을 받아, 창 크기를 바꿔도 텍스트가 자연스럽게 다시 흐르는 Pretext 기반의 프로덕션 수준 HTML을 생성합니다. 이후 `/design-review`와 `/plan-eng-review`가 그 결정을 이어받습니다. 디자인 결정이 시스템 전체를 관통합니다.

**`/qa`는 엄청난 해방감이었습니다.** 덕분에 병렬 워커 수를 6명에서 12명까지 늘릴 수 있었습니다. Claude Code가 "I SEE THE ISSUE"라고 말하고 실제로 버그를 고치고 회귀 테스트를 만들고 수정까지 검증하는 순간, 제 작업 방식이 바뀌었습니다. 이제 에이전트가 직접 봅니다.

**똑똑한 리뷰 라우팅.** 잘 운영되는 스타트업처럼, CEO가 인프라 버그까지 볼 필요는 없고, 백엔드 변경에 디자인 리뷰가 항상 필요한 것도 아닙니다. gstack은 어떤 리뷰가 이미 실행됐는지 추적하고, 지금 무엇이 적절한지 판단해, 적절한 일을 자동으로 수행합니다. Review Readiness Dashboard는 출하 전에 현재 상태를 알려줍니다.

**무조건 테스트합니다.** `/ship`은 프로젝트에 테스트 프레임워크가 없어도 처음부터 부트스트랩합니다. 모든 `/ship` 실행은 커버리지 감사를 남깁니다. 모든 `/qa` 버그 수정은 회귀 테스트를 생성합니다. 목표는 100% 테스트 커버리지입니다. 테스트가 있어야 vibe coding이 yolo coding이 아니라 안전한 방식이 됩니다.

**`/document-release`는 늘 아쉬웠던 그 엔지니어입니다.** 프로젝트의 모든 문서 파일을 읽고, diff와 교차 검토하고, 어긋난 모든 내용을 갱신합니다. README, ARCHITECTURE, CONTRIBUTING, CLAUDE.md, TODOS까지 모두 자동으로 최신 상태를 유지합니다. 이제는 `/ship`이 자동으로 이 스킬을 호출하므로, 별도 명령 없이도 문서가 계속 최신 상태를 유지합니다.

**실제 브라우저 모드.** `/open-gstack-browser`는 anti-bot stealth, 커스텀 브랜딩, 내장 사이드바 확장을 갖춘 AI 제어 Chromium인 GStack Browser를 실행합니다. Google이나 NYTimes 같은 사이트도 캡차 없이 동작합니다. 메뉴 바에는 "Chrome for Testing" 대신 "GStack Browser"가 표시됩니다. 기존 Chrome은 건드리지 않습니다. 모든 browse 명령은 그대로 동작합니다. `$B disconnect`를 실행하면 헤드리스 모드로 돌아갑니다. 창이 열려 있는 한 브라우저는 계속 살아 있으므로, 작업 중에 idle timeout으로 꺼지지 않습니다.

**사이드바 에이전트 - 브라우저 안의 AI 보조자.** Chrome 사이드 패널에 자연어를 입력하면, 하위 Claude 인스턴스가 그 작업을 실행합니다. "설정 페이지로 이동해서 스크린샷 찍어줘." "이 폼을 테스트 데이터로 채워줘." "이 목록의 각 항목을 돌며 가격을 추출해줘." 사이드바는 작업에 맞춰 모델을 자동 라우팅합니다. 빠른 액션(클릭, 이동, 스크린샷)은 Sonnet, 읽기와 분석은 Opus를 사용합니다. 각 작업에는 최대 5분이 주어집니다. 사이드바 에이전트는 격리된 세션에서 실행되므로, 메인 Claude Code 창과 서로 간섭하지 않습니다. 쿠키 가져오기도 사이드바 하단에서 한 번에 할 수 있습니다.

**개인 자동화.** 사이드바 에이전트는 개발 워크플로 전용이 아닙니다. 예를 들어 "아이 학교 학부모 포털을 둘러보고 다른 학부모들의 이름, 전화번호, 사진을 내 Google Contacts에 추가해줘" 같은 작업도 가능합니다. 인증은 두 가지 방식이 있습니다. 1) 헤디드 브라우저에서 한 번 로그인하면 세션이 유지됩니다. 2) 사이드바 하단의 "cookies" 버튼을 눌러 실제 Chrome의 쿠키를 가져올 수 있습니다. 인증이 끝나면 Claude가 디렉터리를 탐색하고 데이터를 추출해 연락처를 생성합니다.

**AI가 막혔을 때 브라우저 핸드오프.** CAPTCHA, 인증 벽, MFA 프롬프트에 걸렸나요? `$B handoff`를 실행하면 정확히 같은 페이지를 모든 쿠키와 탭 상태 그대로 가진 가시적 Chrome이 열립니다. 문제를 직접 해결하고 Claude에게 끝났다고 말하면, `$B resume`이 이어서 진행합니다. 심지어 3번 연속 실패하면 에이전트가 자동으로 이 방식을 제안합니다.

**멀티 AI 세컨드 오피니언.** `/codex`는 OpenAI Codex CLI로부터 독립적인 리뷰를 받습니다. 같은 diff를 완전히 다른 AI가 보는 셈입니다. 세 가지 모드가 있습니다. pass/fail 게이트가 있는 코드 리뷰, 실제로 코드를 깨뜨리려 시도하는 adversarial challenge, 세션 연속성을 가진 open consultation. `/review`(Claude)와 `/codex`(OpenAI)가 같은 브랜치를 모두 검토하면, 겹치는 finding과 각 모델만 발견한 finding을 보여주는 교차 분석도 받을 수 있습니다.

**필요할 때 켜는 안전 장치.** "be careful"이라고 말하면 `/careful`이 `rm -rf`, `DROP TABLE`, force-push, `git reset --hard` 같은 파괴적 명령 전에 경고합니다. `/freeze`는 디버깅 중 수정 범위를 하나의 디렉터리로 잠가, Claude가 관련 없는 파일을 "고쳐버리는" 일을 막아 줍니다. `/guard`는 두 기능을 모두 켭니다. `/investigate`는 조사 중인 모듈에 자동으로 freeze를 겁니다.

**선제적 스킬 제안.** gstack은 지금 사용자가 브레인스토밍 중인지, 리뷰 중인지, 디버깅 중인지, 테스트 중인지 감지하고 적절한 스킬을 제안합니다. 원치 않으면 "stop suggesting"이라고 말하면 되고, 그 선호는 세션을 넘어 기억됩니다.

## 10-15개의 병렬 스프린트

gstack은 하나의 스프린트에서도 강력합니다. 하지만 동시에 10개를 돌리면 업무 방식 자체가 바뀝니다.

[Conductor](https://conductor.build)는 여러 Claude Code 세션을 병렬로 실행합니다. 각 세션은 서로 격리된 워크스페이스를 가집니다. 하나는 새로운 아이디어에 `/office-hours`를 돌리고, 다른 하나는 PR에 `/review`를 돌리고, 세 번째는 기능을 구현하고, 네 번째는 스테이징에서 `/qa`를 실행하고, 나머지 여섯 개는 다른 브랜치에서 움직입니다. 전부 동시에 가능합니다. 저는 정기적으로 10-15개의 병렬 스프린트를 돌립니다. 지금 시점에서는 이것이 실질적인 최대치입니다.

병렬성이 제대로 작동하는 이유는 스프린트 구조 덕분입니다. 프로세스가 없으면 에이전트 10개는 혼돈 10개일 뿐입니다. 하지만 think, plan, build, review, test, ship이라는 구조가 있으면, 각 에이전트는 무엇을 해야 하고 언제 멈춰야 하는지 압니다. 관리 방식도 같습니다. CEO가 팀을 다루듯, 중요한 의사결정에만 체크인하고 나머지는 흘러가게 두면 됩니다.

### 음성 입력 (AquaVoice, Whisper 등)

gstack 스킬은 음성 친화적인 트리거 문구를 지원합니다. "보안 검사 돌려줘", "웹사이트 테스트해줘", "엔지니어링 리뷰 해줘"처럼 자연스럽게 말하면 알맞은 스킬이 활성화됩니다. 슬래시 명령 이름이나 약어를 외울 필요가 없습니다.

---

무료, MIT 라이선스, 오픈소스입니다. 프리미엄 요금제도, 대기열도 없습니다.

제가 소프트웨어를 만드는 방식을 오픈소스로 공개했습니다. 포크해서 당신만의 방식으로 바꿔 보세요.

> **채용 중입니다.** 하루 10K+ LOC를 출하하고 gstack을 더 단단하게 만들고 싶나요?
> YC에서 함께 일해요 - [ycombinator.com/software](https://ycombinator.com/software)
> 매우 경쟁력 있는 연봉과 지분. 샌프란시스코 Dogpatch District.

## 문서

| 문서 | 다루는 내용 |
|-----|---------------|
| [Skill Deep Dives](docs/skills.md) | 각 스킬의 철학, 예시, 워크플로 (Greptile 연동 포함) |
| [Builder Ethos](ETHOS.md) | 빌더 철학: Boil the Lake, Search Before Building, 세 가지 지식 계층 |
| [Architecture](ARCHITECTURE.md) | 설계 결정과 시스템 내부 구조 |
| [Browser Reference](BROWSER.md) | `/browse` 전체 명령 레퍼런스 |
| [Contributing](CONTRIBUTING.md) | 개발 환경 설정, 테스트, contributor mode, dev mode |
| [Changelog](CHANGELOG.md) | 모든 버전의 변경 사항 |

## 개인정보 및 텔레메트리

gstack에는 프로젝트 개선을 위한 **옵트인 방식**의 사용 텔레메트리가 포함되어 있습니다. 정확히 어떤 일이 일어나는지 설명하면 다음과 같습니다.

- **기본값은 꺼짐입니다.** 사용자가 명시적으로 동의하지 않으면 아무것도 전송되지 않습니다.
- **첫 실행 시** 익명 사용 데이터를 공유할지 물어봅니다. 거절할 수 있습니다.
- **동의 시 전송되는 정보:** 스킬 이름, 실행 시간, 성공/실패, gstack 버전, OS. 이것뿐입니다.
- **절대 전송되지 않는 정보:** 코드, 파일 경로, 저장소 이름, 브랜치 이름, 프롬프트, 또는 어떤 사용자 생성 콘텐츠도 포함되지 않습니다.
- **언제든 변경 가능:** `gstack-config set telemetry off` 를 실행하면 즉시 모두 비활성화됩니다.

데이터는 [Supabase](https://supabase.com)에 저장됩니다. Supabase는 오픈소스 Firebase 대안입니다. 스키마는 [`supabase/migrations/`](supabase/migrations/)에 있으므로, 정확히 무엇이 수집되는지 직접 검증할 수 있습니다. 저장소 안의 Supabase publishable key는 Firebase API key와 비슷한 공개 키이며, row-level security 정책이 모든 직접 접근을 차단합니다. 텔레메트리는 스키마 검증, 허용된 이벤트 타입, 필드 길이 제한을 강제하는 validated edge function을 통해서만 흐릅니다.

**로컬 분석은 항상 사용할 수 있습니다.** `gstack-analytics` 를 실행하면 원격 데이터 없이도 로컬 JSONL 파일 기반의 개인 사용 대시보드를 볼 수 있습니다.

## 문제 해결

**스킬이 보이지 않나요?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse`가 실패하나요?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**설치가 오래돼 보이나요?** `/gstack-upgrade` 를 실행하세요. 또는 `~/.gstack/config.yaml` 에 `auto_upgrade: true` 를 설정할 수 있습니다.

**명령을 더 짧게 쓰고 싶나요?** `cd ~/.claude/skills/gstack && ./setup --no-prefix` 를 실행하면 `/gstack-qa` 대신 `/qa` 를 사용합니다. 이 선택은 이후 업그레이드에도 유지됩니다.

**네임스페이스가 있는 명령을 원하나요?** `cd ~/.claude/skills/gstack && ./setup --prefix` 를 실행하면 `/qa` 대신 `/gstack-qa` 를 사용합니다. 다른 스킬 팩과 함께 쓸 때 유용합니다.

**Codex가 "Skipped loading skill(s) due to invalid SKILL.md" 라고 하나요?** Codex 쪽 스킬 설명이 오래된 상태입니다. 다음으로 해결할 수 있습니다: `cd ~/.codex/skills/gstack && git pull && ./setup --host codex` 또는 저장소 로컬 설치라면 `cd "$(readlink -f .agents/skills/gstack)" && git pull && ./setup --host codex`

**Windows 사용자:** gstack은 Windows 11에서 Git Bash 또는 WSL로 동작합니다. Windows에서는 Bun 외에 Node.js도 필요합니다. Bun에는 Playwright의 pipe transport와 관련된 알려진 버그가 있기 때문입니다. ([bun#4253](https://github.com/oven-sh/bun/issues/4253)) browse 서버는 자동으로 Node.js로 폴백합니다. `bun`과 `node` 둘 다 PATH에 들어 있는지 확인하세요.

**Claude가 스킬을 못 본다고 하나요?** 프로젝트의 `CLAUDE.md` 에 gstack 섹션이 있는지 확인하세요. 아래 내용을 추가하면 됩니다.

```md
## gstack
Use /browse from gstack for all web browsing. Never use mcp__claude-in-chrome__* tools.
Available skills: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /design-shotgun, /design-html, /review, /ship, /land-and-deploy,
/canary, /benchmark, /browse, /open-gstack-browser, /qa, /qa-only, /design-review,
/setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex,
/cso, /autoplan, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, /learn.
```

## 라이선스

MIT 라이선스입니다. 영원히 무료입니다. 이제 뭔가를 만들어 보세요.
