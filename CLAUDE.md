# 프로젝트 파악 (작업 전 필수)

새 세션 시작 시 아래 순서로 프로젝트를 먼저 파악한다:
1. `README.md` → 프로젝트 목적·스택 파악
2. `docker-compose.yml` → 서비스명 확인
3. `docs/` 존재 시 → 목록 확인 후 관련 파일만 읽기

# 실행 환경

> 모든 실행·테스트·빌드는 Docker 컨테이너 안에서. 로컬 직접 실행 금지.

```bash
make up / down / logs / build
docker compose exec [service] pytest
docker compose exec [service] npm test
docker compose exec [service] mypy .
docker compose run --rm [service] pytest    # 일회성
```

의존성 추가 → `make build`. 환경변수 → `.env`, `.env.example` 최신 유지.

# 행동 원칙

- 불확실하면 추측 말고 질문. 해석이 여럿이면 먼저 제시.
- 요청받은 것만 구현. 추측 기반 기능·추상화·유연성 추가 금지.
- 요청 외 코드·주석·포맷 수정 금지. 내 변경으로 생긴 orphan만 정리.
- dead code 발견 시 언급만, 삭제 금지.
- 다단계 작업은 계획 먼저: `1. [단계] → 검증: [방법]`
- "시니어 엔지니어가 과하다고 할까?" → Yes면 단순화.

# UI (KRDS)

- KRDS MCP(`@krds-mcp/krds-mcp`) 정보 최우선 참조.
- 색상·타이포·컴포넌트·패턴·디자인 토큰은 KRDS 정의된 것만 사용.
- KRDS에 없는 요구 → ① 가장 가까운 KRDS 대체안 제시 → ② 불가 시 승인 요청.
- 접근성: WCAG 2.1 AA 필수 (명암비 포함).

# 백엔드

- 제공된 내용만 따름. 추측 보완·결정 금지.
- 구조 지시 없으면 기존 구조 파악 후 feature/module 단위 추가.
- 새 디렉토리 필요 시 작업 전 질문: ① 경로안 ② 이유 ③ 대안+트레이드오프.

# 응답

- 설명 최소, 코드 중심. 파일 경로 먼저, 파일별 구분.
- 변경 사유·대안 비교는 요청 시에만.

# 주석

- 한국어. why/역할/입출력·부작용 중심. 코드만 봐도 뻔한 것 금지.
- 파일 상단: 이 파일의 책임 1~3줄.
- 함수·클래스 상단: 역할+입출력+예외·에러처리(있으면)+외부의존성(있으면).
- TODO/FIXME: 이유+조건+담당범위.
