# app-guide-plugin: Claude 앱 사용법 튜터 플러그인

[English](README.md) | **한국어**

> **응답 언어**: 모든 튜터는 학습자가 쓰는 언어(한국어, 영어, 일본어 등)로 답합니다. All tutors reply in the learner's language.


Claude **웹(claude.ai)·데스크톱 앱**을 처음 쓰는 분부터 기능을 더 깊이 쓰고 싶은 분까지, Claude 사용법을 한 단계씩 배우는 튜터 플러그인입니다. 코딩 지식은 필요 없습니다.

## 과정 구성 (3단계, 12개 레슨)

- **기초**: 첫 대화와 화면 둘러보기, 좋은 질문 쓰기, 파일·이미지 올리기, 웹 검색·Research·생각 설정
- **활용**: 프로젝트, 지침·메모리·이전 채팅 검색·시크릿 채팅, 아티팩트와 파일 만들기, 음성 모드와 모바일
- **고급**: 커넥터로 앱 연결하기, 스킬, 여러 기능 조합하기, 안전하고 믿을 수 있게 쓰기

레슨마다 설명, 새 채팅에서 해 보는 실습, 퀴즈가 있습니다. 메뉴 경로와 기능 정보는 공식 도움말(https://support.claude.com)로 확인한 내용입니다(2026-11 기준).

## 설치 방법

### 방법 1. 플러그인으로 추가 (유료 플랜: Pro, Max, Ultra, Team, Enterprise)

1. Claude 웹 또는 데스크톱 앱 왼쪽 메뉴에서 **사용자 정의(Customize)** → **플러그인(Plugins)** 탭으로 갑니다.
2. **추가(Add)** → **마켓플레이스 추가(Add marketplace)** → **저장소에서 추가(Add from a repository)**를 고르고 `sanh09/app-guide-plugin`을 입력합니다.
3. 추가된 마켓플레이스에서 `appguide-tutor`(스킬 `ai-chat-guide`)를 찾아 **추가(Add)**합니다.

웹·데스크톱에서 추가한 플러그인은 계정에 저장되어, 같은 계정으로 로그인한 Claude Code에도 이어집니다. 조직이 마켓플레이스를 제한하는 경우에는 관리자에게 문의하세요.

### 방법 2. 스킬로 추가 (무료 플랜 포함)

1. [`dist/ai-chat-guide-skill.zip`](dist/ai-chat-guide-skill.zip)을 내려받습니다(파일을 연 뒤 "Download raw file"). 압축은 풀지 않습니다.
2. **사용자 정의(Customize)** → **스킬(Skills)** → **"+"** → **"+ 스킬 만들기"** → **"스킬 업로드"**에서 파일을 올립니다.
3. 목록에 나타난 스킬이 켜져 있는지 확인합니다.

스킬을 쓰려면 설정에서 코드 실행(파일 생성) 기능이 켜져 있어야 합니다. 플러그인과 스킬 중 **하나만** 추가하세요. 둘 다 추가하면 같은 튜터가 두 번 보입니다.

### 플러그인 파일을 직접 올릴 때

직접 업로드가 필요한 환경을 위해 플러그인 압축 파일 [`dist/ai-chat-guide-plugin.zip`](dist/ai-chat-guide-plugin.zip)도 함께 둡니다.

## 사용법

새 채팅에서 이렇게 말하면 시작됩니다.

- "Claude 처음 써 봐요. 사용법 알려 주세요"
- "프로젝트 기능이 뭐예요?"
- "메모리 끄는 법 알려 주세요"
- "커넥터 연결하는 법 알려 주세요"
- "Claude 사용법 퀴즈 내 주세요"

플러그인으로 추가했다면 `/appguide-tutor:ai-chat-guide`로 직접 부를 수도 있습니다.

## 플러그인이 하는 일

- 스킬 하나(지침과 참고 파일)만 추가합니다. 훅, MCP 서버, 스크립트는 없고, 데이터를 어디로도 보내지 않습니다.
- 학습 기록을 저장하지 않습니다. 새 채팅에서는 어디부터 시작할지 다시 묻습니다.

## 구조

```
.claude-plugin/marketplace.json            마켓플레이스 정의 (sanh09-app-guide)
plugins/ai-chat-guide/
  .claude-plugin/plugin.json               플러그인 정의
  README.md, README.ko.md
  LICENSE, LICENSE-CC-BY-4.0.txt, NOTICE.txt      라이선스 (코드 MIT, 내용 CC BY 4.0)
  skills/ai-chat-guide/
    SKILL.md                               튜터 규칙
    references/curriculum.md               레슨 1~12, 실습, 퀴즈 문제 은행
    references/quiz-answers.md             퀴즈 정답표 (채점할 때만 읽음)
    references/facts.md                    도움말 문서로 확인한 메뉴 경로·기능 정리
dist/
  ai-chat-guide-skill.zip               스킬 업로드용
  ai-chat-guide-plugin.zip              플러그인 업로드용
```

내용을 고친 뒤에는 `plugin.json`의 `version`을 올리고, `dist/`의 압축 파일도 다시 만들어 주세요.

## 관련 저장소

- Claude 앱에서 배우는 Claude Code 과정: https://github.com/sanh09/guide-protocol
- Claude Code 안에서 배우는 Claude Code 과정: https://github.com/sanh09/code-guide-protocol

## 업데이트 내역

### 2026-11-26: 디렉터리에 맞춰 라이선스 파일 이름 변경 (0.4.3)
- 라이선스 파일 이름이 `LICENSE-CC-BY-4.0.txt`, `NOTICE.txt`로 바뀌었습니다(전에는 `LICENSE-CC-BY-4.0`, `NOTICE`). Anthropic 디렉터리는 Verified가 아닌 게시자에게서 Markdown·텍스트·JSON·YAML·이미지 파일만 받기 때문에 `.txt`를 붙였습니다. 라이선스 내용과 튜터는 그대로입니다.

### 2026-11-26: 이중 라이선스 (코드 MIT, 내용 CC BY 4.0)
- 코드는 계속 MIT이고, 튜터 내용은 이제 CC BY 4.0입니다. 아래 [라이선스](#라이선스)와 [`NOTICE.txt`](NOTICE.txt)를 보세요.
- 플러그인 폴더와 `dist/`의 두 `.zip`에 `LICENSE`, `LICENSE-CC-BY-4.0.txt`, `NOTICE.txt`가 들어갑니다(0.4.2). 가르치는 내용은 바뀌지 않습니다.

### 2026-11-25: 이름에서 `-ko` 제거 (0.4.0, 다시 추가 필요)
- 플러그인과 스킬 이름을 `ai-chat-guide-ko`에서 `ai-chat-guide`로 바꿨습니다. 학습자가 쓰는 언어로 답하는 것은 그대로입니다.
- 플러그인 이름은 `appguide-tutor`이고, 스킬 `ai-chat-guide`를 담습니다(0.4.1). 짧은 이름이 디렉터리의 기존 항목과 너무 비슷해서 바꿨습니다.

**예전 이름으로 추가했다면 다시 추가하세요** (새로 고침만으로는 새 이름으로 바뀌지 않습니다):
- 플러그인으로 추가했다면: 사용자 정의(Customize) > 플러그인(Plugins)에서 `ai-chat-guide-ko`를 지우고, `sanh09-app-guide` 마켓플레이스를 새로 고친 뒤 `appguide-tutor`를 추가하세요.
- 스킬로 추가했다면: 사용자 정의 > 스킬에서 `ai-chat-guide-ko`를 지우고 [`dist/ai-chat-guide-skill.zip`](dist/ai-chat-guide-skill.zip)을 올리세요.

### 2026-11-25: 영어 README와 라이선스
- README 기본 언어를 영어로 바꾸고, 한국어는 이 파일(README.ko.md)에서 볼 수 있습니다. 플러그인 폴더에도 README와 LICENSE를 넣었습니다.

### 2026-11-25: 프로젝트 안내 바로잡기 (0.3.1)
- 프로젝트는 Free를 포함한 모든 사용자가 쓸 수 있고, Free 플랜은 최대 5개까지 만들 수 있다고 안내합니다. 이전에는 프로젝트 지침을 유료 기능으로 안내했습니다.
- 이 저장소가 `ai-chat-guide-ko`의 유일한 관리 위치가 되었습니다. guide-protocol에서는 이 스킬을 뺐습니다.

### 2026-11-25: 학습자 언어로 응답 (0.3.0)
- 학습자가 쓰는 언어(한국어, 영어, 일본어 등)로 답합니다. 퀴즈를 옮겨도 보기의 뜻은 유지하고, 채점은 뜻으로 대조합니다.

### 2026-11-25: 퀴즈 정답 노출 수정 (0.2.0)
- 퀴즈를 낼 때 정답이 문제·예시·힌트에 함께 보이던 문제를 고쳤습니다. 정답은 `references/quiz-answers.md`로 분리되어 채점할 때만 쓰입니다.
- 보기 순서가 매번 섞이고, 답 형식 예시는 `1-?, 2-?`처럼 자리 표시만 씁니다.
- 퀴즈 카드에서는 정답을 정답 칸에만 넣고, 퀴즈 모드로 엽니다. 선택형 질문 버튼으로는 퀴즈를 내지 않습니다.

**업데이트 방법**
- 플러그인으로 추가했다면: 사용자 정의(Customize) > 플러그인(Plugins)에서 `sanh09-app-guide` 마켓플레이스를 새로 고치거나, 플러그인을 지우고 다시 추가해 주세요.
- 스킬로 추가했다면: 사용자 정의 > 스킬에서 기존 스킬을 지우고 `dist/ai-chat-guide-ko-skill.zip`을 다시 올려 주세요.

전체 변경 기록: https://github.com/sanh09/code-guide-protocol/blob/main/maintenance/CHANGELOG.md

## 변경 방법

이 저장소의 변경은 `main`에 직접 push하지 않고 PR(Pull Request)로 진행합니다. 브랜치를 만들어 수정하고, 검증(`claude plugin validate .` 등)이 통과하면 PR을 merge합니다. 자동 업데이트도 같은 방식으로 PR을 만들고 merge합니다. 자세한 절차: https://github.com/sanh09/code-guide-protocol/blob/main/maintenance/MAINTENANCE.md

## 유지보수

`dist/` 파일은 `bash scripts/build-dist.sh`로 다시 만듭니다. 업데이트 절차와 기록은 https://github.com/sanh09/code-guide-protocol/tree/main/maintenance 에 있습니다.

## 라이선스

이 프로젝트는 라이선스 두 개를 씁니다.
- **코드**: 셸 스크립트(`*.sh`)와 JSON·YAML 설정 파일은 [MIT 라이선스](LICENSE)입니다. 레슨 안의 코드 예시도 MIT로 쓸 수 있습니다.
- **내용**: `SKILL.md`, 참고 파일(레슨, 사실, 퀴즈, 정답표), 평가(evals), README, 유지보수 문서, 이미지는 [크리에이티브 커먼즈 저작자표시 4.0(CC BY 4.0)](LICENSE-CC-BY-4.0.txt)입니다.

내용을 다시 쓸 때는 이렇게 출처를 밝혀 주세요: `app-guide-plugin by sanh09 (https://github.com/sanh09/app-guide-plugin), CC BY 4.0`. 자세한 범위와 Anthropic 상표 안내는 [`NOTICE.txt`](NOTICE.txt)에 있습니다. 플러그인 폴더와 `dist/`의 `.zip` 파일에도 세 파일이 모두 있습니다.
