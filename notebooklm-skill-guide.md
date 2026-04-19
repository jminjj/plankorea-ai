# Gemini CLI에서 NotebookLM Skill 사용 가이드

이 문서는 [notebooklm-py](https://github.com/teng-lin/notebooklm-py)를 Gemini CLI의 **Agent Skill**로 등록하여, AI 에이전트가 직접 NotebookLM의 기능을 호출하고 활용할 수 있도록 설정하는 방법을 설명합니다.

## 1. 개요
Gemini CLI의 **Skill**은 에이전트가 특정 도구나 지식을 필요할 때 동적으로 로드하여 사용할 수 있는 패키지입니다. `notebooklm-py`는 이미 `SKILL.md` 파일을 포함하고 있어 Gemini CLI와 쉽게 연동됩니다.

## 2. Skill 설치 방법

### 방법 1: 자동 설치 (권장)
터미널에서 다음 명령어를 실행하여 GitHub 저장소에서 직접 Skill을 설치할 수 있습니다.

```bash
gemini skills install https://github.com/teng-lin/notebooklm-py
```

### 방법 2: 수동 설치 (워크스페이스 전용)
특정 프로젝트 내에서만 사용하려면 다음 단계를 따릅니다.

1.  프로젝트 루트에 `.gemini/skills/notebooklm/` 디렉토리를 생성합니다.
2.  해당 디렉토리에 `notebooklm-py` 저장소의 `SKILL.md` 파일을 다운로드하여 저장합니다.
    - [SKILL.md 직접 링크](https://raw.githubusercontent.com/teng-lin/notebooklm-py/main/SKILL.md)

## 3. Skill 활성화 및 사용

### 3.1. Skill 활성화
Gemini CLI 세션 내에서 다음 명령어를 통해 Skill이 올바르게 로드되었는지 확인하고 활성화할 수 있습니다.

- **목록 확인**: `/skills list`
- **활성화**: `/skills enable notebooklm` (설치 시 이름이 다를 경우 해당 이름 사용)

### 3.2. 에이전트에게 지시하기
Skill이 활성화되면, AI 에이전트에게 다음과 같이 자연어로 지시를 내릴 수 있습니다. 에이전트는 `activate_skill` 도구를 사용하여 필요한 지침을 불러온 뒤, `run_shell_command`를 통해 `notebooklm` 명령어를 실행합니다.

> **예시 명령어:**
> - "NotebookLM에 'AI 연구'라는 이름의 노트북을 만들고, 이 프로젝트의 `README.md`를 소스로 추가해줘."
> - "내 NotebookLM 노트북들 중에서 '기계학습' 노트북을 사용해서 핵심 요약을 해줘."
> - "이 소스들로 팟캐스트 스타일의 오디오 오버뷰를 생성하고 저장해줘."

## 4. 작동 원리
1.  **Skill 활성화**: 사용자가 요청하면 에이전트가 `notebooklm` 스킬을 활성화합니다.
2.  **지침 준수**: 에이전트는 `SKILL.md`에 정의된 작업 절차와 명령어 형식을 학습합니다.
3.  **도구 실행**: 에이전트는 `notebooklm-py` CLI 도구를 사용하여 실제 작업을 수행합니다.

## 5. 주의 사항
- 이 스킬을 사용하려면 시스템에 `notebooklm-py`가 이미 설치되어 있고 로그인이 완료되어 있어야 합니다. (`notebooklm login` 실행 필수)
- `notebooklm-py` 가이드 문서를 참고하여 기본 환경 구성을 먼저 완료해 주세요. (`notebooklm-guide.md`)
