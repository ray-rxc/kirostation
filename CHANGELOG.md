## v1.0.0-69 (2026-04-18)

### 주요 변경
- launchAgent 통합: 에이전트 실행 로직을 SessionManager 한 곳으로 통합
- 딥링크 개선: project, cwd 파라미터 추가 (worktree 지원)
- 프로젝트 카드 UI 개선: 280×160 고정, 브랜치/커밋 분리, NSView 기반 tooltip
- 세션 히스토리: kiro-cli 2.0 .jsonl fallback 파싱, 빈 세션 필터, 시간순 정렬

### 수정
- GitHub PR 우클릭 에이전트 실행 안 되는 버그 수정
- resumeSession ACP 토글 상태 동기화 버그 수정
- SessionStarterView ZStack 제거, .infinity 전파 제거

---

## v1.0.0-68 (2026-04-17)

### 수정
- 터미널 스크롤 속도 조절 (mouse-scroll-multiplier)
- 사이드바 기본 너비 확대 (256 → 296)
- Shift+Enter: kiro-cli에서 줄바꿈, 일반 셸에서 정상 동작
- CLI 도구 실행 시 login shell 래핑으로 PATH 보장

---

## v1.0.0-67 (2026-04-17)

### 수정
- Shift+Enter: kiro-cli/claude에서 줄바꿈 동작 (Kitty keyboard protocol 지원)
- 한글 조합 중 엔터 시 조합 확정 후 즉시 전송
- CLI 도구 실행 시 PATH 누락 문제 수정 (login shell 래핑)

---

## v1.0.0-66 (2026-04-17)

### 수정
- 한글 IME 상태에서 Cmd+C/V 등 단축키 동작 안 되던 문제 수정 (keyCode→ASCII 매핑)
- 그리드 모드에서 Cmd+C/V가 항상 첫 번째 터미널로 가던 문제 수정 (focusedSurface 추적)
- 한글 조합 중 엔터 시 두 번 눌러야 하던 문제 수정
- 한글→영문 전환 시 preedit 잔상 수정
- 마우스 클릭 시 IME 조합 자동 확정
- 탭/세션 전환 시 IME 조합 자동 확정
- ghostty 기본 키바인딩 충돌 해제 (Cmd+T/N/W/Q)
- 그리드 모드에서 클릭한 터미널로 포커스 이동

---

## v1.0.0-66 (2026-04-17)

### 수정
- 한글 IME 상태에서 Cmd+C/V/T 등 단축키 동작 안 되던 문제 수정 (keyCode→ASCII 매핑)
- 그리드 모드에서 Cmd+C/V가 항상 첫 번째 터미널로 가던 문제 수정 (focusedSurface 추적)
- 한글 조합 중 엔터 시 두 번 눌러야 하던 문제 수정
- 한글→영문 전환 시 preedit 잔상 수정
- 탭/세션 전환 시 IME 조합 자동 확정
- ghostty 기본 키바인딩 충돌 해제 (Cmd+T/N/W/Q)
- 그리드 모드에서 클릭한 터미널로 포커스 이동

---

## v1.0.0-65 (2026-04-16)

### 주요 변경
- 터미널 엔진을 SwiftTerm → libghostty (Ghostty v1.3.1)로 교체
  - Metal GPU 가속 렌더링 — 깜빡임 해결
  - NSTextInputClient 기반 한글/일본어 IME 지원
  - ghostty 기본 키바인딩 (⌘+/⌘- 폰트 조절 등)

### 수정
- JIRA/GitHub 사이드바에서 에이전트 실행 시 URL이 전달되지 않던 버그 수정
- 그리드 모드에서 라벨 바가 터미널 영역과 겹치던 문제 수정

### 기타
- ghostty-defaults.conf 추가 (Menlo + Apple SD Gothic Neo, 다크 테마)
- GhosttyKit 빌드 가이드 README에 추가
- Git LFS로 xcframework 바이너리 관리

---

## v1.0.0-64 (2026-04-16)

### 수정
- 그리드 모드에서 ACP 셀 클릭 시 탭 활성화 안 되던 문제 수정 (NSEvent 로컬 모니터)
- DiffView 여러 줄 텍스트 선택 지원 (AttributedString 통합)
- ACP 세션 닫기 Alert에 세션명 표시
- kiro-cli 패닉(크래시) 시 Thinking... 무한 표시 문제 수정 (stderr 감지)
- JIRA 이슈 스프린트 그룹핑 시 active 스프린트 우선 선택

---

## v1.0.0-63 (2026-04-14)

### 수정
- ACP 채팅 자동 스크롤 개선 — 콘텐츠 높이 변경 감지 방식으로 전환, 스트리밍 중 끊김 해결
- 사용자 스크롤 복귀 시 자동 스크롤 재개
- execute 도구 title이 서버에서 잘려오는 문제 수정 — rawInput.command에서 전체 명령어 표시
- ToolCallView 레이아웃 개선 — 긴 명령어 잘림 해결 (VStack 세로 배치)
- read 도구 파일 경로 미표시 수정 — operations 키 지원 추가

---

## v1.0.0-62 (2026-04-06)

### 수정
- DirectoryWatcher에 0.5초 debounce 추가 — 에이전트 파일 수정 시 사이드바 reload 폭풍 방지
- SwiftTerm scrollback 무제한 → 10,000줄 제한 — 터미널 메모리 누적 방지
- JIRA 이슈 컨텍스트 메뉴에서 에이전트 실행 시 동작하지 않는 버그 수정 (ACP 모드 지원 포함)

---

## v1.0.0-61 (2026-04-03)

### 수정
- 자동 업데이트: public repo 다운로드 (토큰 불필요), nohup 프로세스 분리, 윈도우 정리 후 종료
- 사이드바 헤더에 버전 표시 + 업데이트 버튼 이동

---

## v1.0.0-60 (2026-04-02)

### 수정
- Jira Data Center PAT 엔드포인트 수정 (Cloud: /search/jql, DC: /search)

---

## v1.0.0-59 (2026-04-02)

### 개선
- 자동 업데이트를 public repo(ray-rxc/kirostation)에서 체크 — GitHub 토큰 불필요
- 릴리즈 스크립트(release.sh) — private + public 양쪽 릴리즈 + CHANGELOG 동기화

---

## v1.0.0-58 (2026-04-02)

### 신규
- 앱 아이콘 추가
- Jira Data Center PAT 인증 지원 (Cloud/PAT 자동 분기)

### 개선
- DSAgentMenu 공통 컴포넌트 — 에이전트 메뉴 4곳 통합 (Jira/GitHub/Files/Specs)
- 메뉴 구조 개선: [글로벌 에이전트 | 프로젝트별(기본 에이전트 + 에이전트들)]
- 프롬프트를 CLI 인자로 전달 (onPromptReady 제거, claude/kiro-cli/codex 호환)
- Global 섹션에 루트 파일도 표시
- 앱 강제 다크모드 (라이트모드에서 텍스트 안 보이는 문제 해결)

### 수정
- pull 시 머지된 로컬 브랜치 자동 정리

---

## v1.0.0-57 (2026-04-02)

### 신규
- 자동 업데이트 — GitHub Releases에서 새 버전 감지 → DMG 다운로드 → 앱 교체
  - 앱 시작 / 비활성→활성 시 체크 (1시간 쿨다운)
  - 사이드바 하단 배지 → 릴리즈 노트 시트 → 즉시 또는 다음 실행 시 업데이트

### 수정
- auto-prune: pull 시 삭제된 리모트 브랜치의 로컬 브랜치 자동 정리

---

## v1.0.0-55 (2026-04-02)

### 신규
- .kiro GitHub Sync — 프로젝트별 `.kiro/` 디렉토리 동기화 기능
  - Pull / Commit & Push (feature 브랜치 -u 지원)
  - 브랜치 전환(main 포함) / 삭제 / merged 표시
  - 파일·커밋 클릭 → NSTextView 색상 diff 패널
  - PR 클릭 → 브라우저에서 GitHub 열기
  - Refresh 버튼 (fetch + 전체 상태 갱신)
  - 5분 주기 모니터링 + macOS 알림 (새 PR 감지)
  - 사이드바: ahead/behind/changed 상태 아이콘 + PR 뱃지
  - 충돌 해결 UI (side-by-side, Use Local/Remote/Edit)

### 개선
- KiroSyncStatus 확장 (3→8 case: synced/changed/behind/ahead/aheadBehind/conflict/newPR/syncing)
- 사이드바 프로젝트 우클릭 ".kiro Sync…" 메뉴 (기존 pull-only 대체)
- 기존 워닝 수정 (nonisolated KiroFiles.empty)

---

## v1.0.0-56 (2026-04-01)

### 수정
- File descriptor 누수 수정 — DirectoryWatcher를 DispatchSource → FSEventStream으로 교체 (DIR fd 4800+ → 1)
- SidebarView 파일 스캔 URL API → String API (resourceValues 캐싱 fd 누수 제거)
- setupWatcher ↔ reload 무한 루프 제거
- 장시간 사용 시 앱 느려지는 문제 해결
- 프로세스 종료 시 SIGKILL fallback 추가 (좀비 프로세스 방지)

---

## v1.0.0-54 (2026-04-01)

### 신규
- Deep Link prompt 파라미터 — `kirostation://new-tab?agent=xxx&prompt=yyy`
- 사이드바 파일/폴더 에이전트 메뉴 — Global/Projects에서 우클릭 → 에이전트 선택 (JIRA/GitHub 동일)
- Specs 파일 드래그&드롭 지원

### 개선
- Tool Call 표시 개선 — read: compact 뷰 (전체 경로 + 라인 범위), edit: compact 헤더 + diff, JSON 덤프 제거
- 권한 요청 큐 — 여러 permission request 순차 처리 (이전: 마지막 1개만 표시)
- SessionStarter 레이아웃 재배치 — Tool 카드 항상 노출, ACP 토글+시작 버튼 HStack
- 사이드바 새로고침 시 Specs 섹션도 갱신

### 수정
- Metal crash 수정 — CLI tools 미설치 시 홈 디렉토리 전체 스캔 차단
- CLI 도구 감지 개선 — ~/.zshrc PATH 로드 (-li)
- ACP 환경변수 — 하드코딩 PATH 제거, 사용자 shell 환경 전체 로드

---

## v1.0.0-49 (2026-03-31)

### 개선
- 폰트 크기 전체 +2pt — DS 토큰 체계 적용 (fontXXS~fontIconLG)
- 제목/헤더 bold, 하위 그룹 semibold 적용
- 에이전트 탭 Global/Project 간격 축소

---

## v1.0.0-48 (2026-03-31)

### 신규
- 도구 호출 시 request input(JSON) 표시 — MCP 도구 등 요청 본문 확인 가능
- 도구 호출 시 __tool_use_purpose 표시 — title 옆에 목적 텍스트

### 수정
- ⌘C 후 포커스 복원 — 터미널/에디터에서 복사 시 해당 뷰 포커스 유지
- ProgressView 스피너 색상 수정

---

## v1.0.0-47 (2026-03-30)

### 신규
- Specs 사이드바 섹션 — ~/.kiro/specs/{프로젝트}/{에픽}/ 구조 파싱, JIRA 스타일 3단 트리
- 스펙 상태 뱃지 (완료/진행중/미시작) — md 파일 내 테이블 자동 파싱
- 스펙 우클릭 → 프로젝트 에이전트 선택 → ACP/Terminal 세션 시작 (스펙 context 자동 전달)
- 에픽 아카이브 기능 (전체 완료 시 archive/ 폴더로 이동)
- New Session 탭 분리: 히스토리 / 스펙 / 에이전트
- 스펙 탭: 에픽 카드 (진행률 바, 완료 카운트), 스펙 → 에이전트 메뉴
- 에이전트 탭: Global | Project 나란히 배치
- 탭 선택 저장/복원

### 수정
- ⌘W 포커스 판단 — NSView hitTest 기반으로 변경 (에디터/터미널 정확한 구분)

---

## v1.0.0-46 (2026-03-30)

### 개선
- Jira/GitHub 우클릭 에이전트 메뉴에 모든 프로젝트별 에이전트 표시 (서브메뉴 그룹핑)

---

## v1.0.0-45 (2026-03-30)

### 버그 수정
- ACP Transport 크래시 수정 — session/cancel 후 프로세스 종료 시 NSFileHandleOperationException 방지

### 새 기능
- 에디터 비디오 프리뷰 (mp4, mov, avi, mkv, webm, m4v) — 커스텀 Playback 컨트롤
- 이미지 뷰어 확대/축소 — 트랙패드 핀치(커서 기준), Fit/1:1 버튼, 중앙 정렬
- 브랜치명 실시간 갱신 — .git/HEAD 파일 감시
- open-web deep link — `kirostation://open-web?url={URL}` 내부 웹뷰로 열기

---

## v1.0.0-44 (2026-03-30)

첫 릴리즈.

### 주요 기능
- PTY 터미널 (다중 탭, 폰트 조절, 드래그&드롭)
- ACP 에이전트 채팅 (kiro-cli acp, 세션 복원, diff 표시)
- 사이드바 (파일 트리, MCP 상태, 프로젝트 관리)
- 에디터 (구문 강조, WebView, 이미지 프리뷰)
- JIRA/GitHub 연동
- 텔레그램 봇 (원격 제어, 백그라운드 세션)
- Deep Link (kirostation://)
- 글로벌 프롬프트 히스토리
