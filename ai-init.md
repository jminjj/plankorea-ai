# AI 초기화 보고서 (ai_init.md)

## 1. 업무 진행 방법 정의 요약

본 프로젝트는 AI와의 효율적인 협업을 위해 다음과 같은 체계적인 업무 프로세스를 정의합니다.

### 1.1. 작업 지시 (Work Order)
- **트리거**: "지시 수행" 요청 또는 단축 명령어 `ex`
- **대상 파일**: `_project/work-order.md`
- **프로세스**:
    1. 지시 사항 정리 (원문 + 체계적 재정리)
    2. 계획 검토 및 수립
    3. 단계적 수행 및 상세 보고서 작성 (`_project/work-log/` 하위)
    4. `work-order.md` 리셋
    5. `_project/history.md`에 이력 추가

### 1.2. 질의 사항 (Question)
- **트리거**: "질문의 답", "답해줘" 요청 또는 단축 명령어 `aw`
- **대상 파일**: `_project/question.md`
- **프로세스**:
    1. 질의 내용 정리 (원문 + 체계적 재정리)
    2. 상세 답변 및 보고서 작성 (`_project/work-log/` 하위)
    3. 향후 업무 지시(work-order) 제안
    4. `question.md` 리셋
    5. `_project/history.md`에 이력 추가

### 1.3. 보고서 작성 규칙
- **경로**: `_project/work-log/`
- **파일명 형식**: `yymmdd-hh-seq-type-title.md`
    - `yymmdd`: 날짜
    - `hh`: 시간 (00-23)
    - `seq`: 일련번호 (000-999)
    - `type`: 업무 유형 (work/ques 등)
    - `title`: 핵심 제목

### 1.4. 예외 처리
- 프롬프트에 직접 지시/질의가 있는 경우 파일 확인 단계를 건너뛰고 즉시 수행 후 관련 파일 리셋

## 2. 환경 구성 계획

- gemini라면 **GEMINI.md**: 위 프로세스를 Gemini CLI의 핵심 지침으로 등록하여 자동 준수 유도
- claude라면 **CLAUDE.md**: 위 프로세스를 Claude CLI의 핵심 지침으로 등록하여 자동 준수 유도
- **파일 시스템**: `_project/` 하위에 `work-order.md`, `question.md`, `history.md`, `work-log/` 생성
- **자동화**: 명령어 인식 및 보고서 생성 로직을 GEMINI.md에 명시하여 일관성 유지
