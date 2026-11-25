# app-guide-plugin: Claude 앱 사용법 한국어 튜터 플러그인

Claude **웹(claude.ai)·데스크톱 앱**을 처음 쓰는 분부터 기능을 더 깊이 쓰고 싶은 분까지, Claude 사용법을 한국어로 한 단계씩 배우는 튜터 플러그인입니다. 코딩 지식은 필요 없습니다.

## 과정 구성 (3단계, 12개 레슨)

- **기초**: 첫 대화와 화면 둘러보기, 좋은 질문 쓰기, 파일·이미지 올리기, 웹 검색·Research·생각 설정
- **활용**: 프로젝트, 지침·메모리·이전 채팅 검색·시크릿 채팅, 아티팩트와 파일 만들기, 음성 모드와 모바일
- **고급**: 커넥터로 앱 연결하기, 스킬, 여러 기능 조합하기, 안전하고 믿을 수 있게 쓰기

레슨마다 설명, 새 채팅에서 해 보는 실습, 퀴즈가 있습니다. 메뉴 경로와 기능 정보는 공식 도움말(https://support.claude.com)로 확인한 내용입니다(2026-11 기준).

## 설치 방법

### 방법 1. 플러그인으로 추가 (유료 플랜: Pro, Max, Ultra, Team, Enterprise)

1. Claude 웹 또는 데스크톱 앱 왼쪽 메뉴에서 **사용자 정의(Customize)** → **플러그인(Plugins)** 탭으로 갑니다.
2. **추가(Add)** → **마켓플레이스 추가(Add marketplace)** → **저장소에서 추가(Add from a repository)**를 고르고 `sanh09/app-guide-plugin`을 입력합니다.
3. 추가된 마켓플레이스에서 `ai-chat-guide-ko`를 찾아 **추가(Add)**합니다.

웹·데스크톱에서 추가한 플러그인은 계정에 저장되어, 같은 계정으로 로그인한 Claude Code에도 이어집니다. 조직이 마켓플레이스를 제한하는 경우에는 관리자에게 문의하세요.

### 방법 2. 스킬로 추가 (무료 플랜 포함)

1. [`dist/ai-chat-guide-ko-skill.zip`](dist/ai-chat-guide-ko-skill.zip)을 내려받습니다(파일을 연 뒤 "Download raw file"). 압축은 풀지 않습니다.
2. **사용자 정의(Customize)** → **스킬(Skills)** → **"+"** → **"+ 스킬 만들기"** → **"스킬 업로드"**에서 파일을 올립니다.
3. 목록에 나타난 스킬이 켜져 있는지 확인합니다.

스킬을 쓰려면 설정에서 코드 실행(파일 생성) 기능이 켜져 있어야 합니다. 플러그인과 스킬 중 **하나만** 추가하세요. 둘 다 추가하면 같은 튜터가 두 번 보입니다.

### 플러그인 파일을 직접 올릴 때

직접 업로드가 필요한 환경을 위해 플러그인 압축 파일 [`dist/ai-chat-guide-ko-plugin.zip`](dist/ai-chat-guide-ko-plugin.zip)도 함께 둡니다.

## 사용법

새 채팅에서 이렇게 말하면 시작됩니다.

- "Claude 처음 써 봐요. 사용법 알려 주세요"
- "프로젝트 기능이 뭐예요?"
- "메모리 끄는 법 알려 주세요"
- "커넥터 연결하는 법 알려 주세요"
- "Claude 사용법 퀴즈 내 주세요"

플러그인으로 추가했다면 `/ai-chat-guide-ko:ai-chat-guide-ko`로 직접 부를 수도 있습니다.

## 구조

```
.claude-plugin/marketplace.json            마켓플레이스 정의 (sanh09-app-guide)
plugins/ai-chat-guide-ko/
  .claude-plugin/plugin.json               플러그인 정의
  skills/ai-chat-guide-ko/
    SKILL.md                               튜터 규칙
    references/curriculum.md               레슨 1~12, 실습, 퀴즈 문제 은행
    references/facts.md                    도움말 문서로 확인한 메뉴 경로·기능 정리
dist/
  ai-chat-guide-ko-skill.zip               스킬 업로드용
  ai-chat-guide-ko-plugin.zip              플러그인 업로드용
```

내용을 고친 뒤에는 `plugin.json`의 `version`을 올리고, `dist/`의 압축 파일도 다시 만들어 주세요.

## 관련 저장소

- Claude 앱에서 배우는 Claude Code 과정: https://github.com/sanh09/guide-protocol
- Claude Code 안에서 배우는 Claude Code 과정: https://github.com/sanh09/code-guide-protocol

## 유지보수

`dist/` 파일은 `bash scripts/build-dist.sh`로 다시 만듭니다. 업데이트 절차와 기록은 https://github.com/sanh09/code-guide-protocol/tree/main/maintenance 에 있습니다.
