# Pixel Agents

AI 코딩 에이전트를 가상 오피스 공간의 애니메이션 픽셀 아트 캐릭터로 바꿔주는 VS Code 확장 프로그램입니다.

열려 있는 각각의 Gemini CLI 터미널은 돌아다니거나 책상에 앉고 에이전트가 무엇을 하고 있는지 시각적으로 반영하는 캐릭터를 생성합니다 — 코드를 작성할 때는 타이핑을 하고, 파일을 검색할 때는 책을 읽고, 주의가 필요할 때는 대기합니다.

이것은 무료 [VS Code용 Pixel Agents 확장 프로그램](https://marketplace.visualstudio.com/items?itemName=pablodelucca.pixel-agents)의 소스 코드입니다 — 가구 카탈로그 전체가 포함된 상태로 마켓플레이스에서 직접 설치할 수 있습니다.

![Pixel Agents screenshot](webview-ui/public/Screenshot.jpg)

## Features (기능)

- **One agent, one character (1 에이전트, 1 캐릭터)** — 모든 Gemini CLI 터미널은 고유한 애니메이션 캐릭터를 갖습니다
- **Live activity tracking (실시간 활동 추적)** — 캐릭터는 에이전트가 실제로 수행하는 작업(작성, 읽기, 명령 실행)을 기반으로 애니메이션을 표시합니다
- **Office layout editor (오피스 레이아웃 에디터)** — 내장된 편집기를 사용하여 바닥, 벽 및 가구로 오피스를 디자인합니다
- **Speech bubbles (말풍선)** — 에이전트가 입력을 기다리거나 권한이 필요할 때 시각적 표시가 나타납니다
- **Sound notifications (소리 알림)** — 에이전트의 차례가 끝날 때 선택적 차임벨이 울립니다
- **Sub-agent visualization (보조 에이전트 시각화)** — Task 도구 보조 에이전트는 부모에 연결된 별도의 캐릭터로 생성됩니다
- **Persistent layouts (영구 레이아웃)** — 오피스 디자인은 저장되며 VS Code 창 전체에서 공유됩니다
- **Diverse characters (다양한 캐릭터)** — 6개의 다양한 캐릭터가 있습니다.

<p align="center">
  <img src="webview-ui/public/characters.png" alt="Pixel Agents characters" width="320" height="72" style="image-rendering: pixelated;">
</p>

## Requirements (요구 사항)

- VS Code 1.109.0 or later (VS Code 1.109.0 이상)
- [Gemini CLI](https://google.github.io/gemini-cli) installed and configured (설치 및 구성된 [Gemini CLI](https://google.github.io/gemini-cli))

## Getting Started (시작하기)

단순히 Pixel Agents를 사용하고 싶다면, [VS Code 확장 프로그램](https://marketplace.visualstudio.com/items?itemName=pablodelucca.pixel-agents)을 다운로드하는 것이 가장 쉬운 방법입니다. 코드를 가지고 놀거나, 개발하거나, 기여하고 싶다면 다음 방법을 따르세요:

### Install from source (소스로부터 설치)

```bash
git clone https://github.com/pablodelucca/pixel-agents.git
cd pixel-agents
npm install
cd webview-ui && npm install && cd ..
npm run build
```

그런 다음 VS Code에서 **F5**를 눌러 Extension Development Host를 실행합니다.

### Usage (사용법)

1. 터미널 옆 하단 패널 영역에 나타나는 **Pixel Agents** 패널을 엽니다
2. **+ Agent**를 클릭하여 새로운 Gemini CLI 터미널과 해당 캐릭터를 생성합니다
3. Gemini로 코딩을 시작하고 캐릭터가 실시간으로 반응하는 것을 확인하세요
4. 캐릭터를 클릭하여 선택한 다음, 좌석을 클릭하여 재배치합니다
5. **Layout**을 클릭하여 오피스 에디터를 열고 공간을 커스터마이즈합니다

## Layout Editor (레이아웃 에디터)

내장된 에디터로 오피스를 디자인할 수 있습니다:

- **Floor (바닥)** — 전체 HSB 색상 제어
- **Walls (벽)** — 색상 커스터마이즈가 포함된 자동 타일링 벽
- **Tools (도구)** — 선택, 페인트, 지우기, 배치, 스포이드, 줍기
- **Undo/Redo (실행 취소/다시 실행)** — Ctrl+Z / Ctrl+Y로 50단계 지원
- **Export/Import (내보내기/가져오기)** — 설정 모달을 통해 레이아웃을 JSON 파일로 공유

그리드는 64×64 타일까지 확장할 수 있습니다. 현재 그리드 바깥쪽의 고스트 테두리를 클릭하여 확장하세요.

### Office Assets (오피스 에셋)

이 프로젝트에 사용되고 확장 프로그램을 통해 사용할 수 있는 오피스 타일셋은 **Donarg**의 **[Office Interior Tileset (16x16)](https://donarg.itch.io/officetileset)** 이며, itch.io에서 **$2 USD**에 이용할 수 있습니다.

이 부분은 프로젝트에서 자유롭게 사용할 수 없는 유일한 부분입니다. 타일셋은 라이선스 문제로 이 레포지토리에 포함되어 있지 않습니다. 전체 오피스 가구 및 장식 세트와 함께 로컬에서 Pixel Agents를 사용하려면 해당 타일셋을 구매하고 에셋 임포트 파이프라인을 실행하세요:

```bash
npm run import-tileset
```

참고: 임포트 파이프라인은 그다지 직관적이지 않습니다. 기본 제공 타일셋 에셋이 작업하기 쉬운 편이 아니기 때문에 최대한 원활한 과정을 만들려고 노력했지만 약간의 수동 조정이 필요할 수도 있습니다. 픽셀 아트 오피스 에셋을 제작한 경험이 있거나 커뮤니티를 위해 자유롭게 사용할 수 있는 타일셋을 기여해 주신다면 매우 감사하겠습니다.

확장 프로그램은 타일셋 없이도 여전히 작동합니다. 기본 캐릭터와 기본 레이아웃을 제공받게 되지만 전체 가구 카탈로그를 사용하려면 임포트된 에셋이 필요합니다.

## How It Works (작동 원리)

Pixel Agents는 Gemini CLI의 JSONL 트랜스크립트 파일을 모니터링하여 각 에이전트가 무슨 작업을 하고 있는지 추적합니다. 에이전트가 도구(예: 파일 쓰기, 명령어 실행)를 사용할 때 확장 프로그램이 이를 감지하고 캐릭터의 애니메이션을 그에 따라 업데이트합니다. Gemini CLI 자체는 수정하지 않으며 전적으로 관찰에 의해 동작합니다.

웹뷰는 캔버스 렌더링, BFS 경로 찾기, 캐릭터 상태 머신(유휴 → 걷기 → 타이핑/읽기)이 포함된 경량 형태의 게임 루프를 실행합니다. 모든 것이 정수 확대/축소 배율로 픽셀 퍼펙트를 유지합니다.

## Tech Stack (기술 스택)

- **Extension (확장 프로그램)**: TypeScript, VS Code Webview API, esbuild
- **Webview (웹뷰)**: React 19, TypeScript, Vite, Canvas 2D

## Known Limitations (알려진 한계점)

- **Agent-terminal sync (에이전트-터미널 동기화)** — 에이전트가 Gemini CLI 터미널 인스턴스와 연결되는 방식이 매우 견고하지는 않아, 특히 터미널이 빠르게 열리거나 닫힐 때, 혹은 세션 간에 복원될 때 종종 동기화가 풀릴 수 있습니다.
- **Heuristic-based status detection (휴리스틱 기반 상태 감지)** — Gemini CLI의 JSONL 트랜스크립트 형식은 에이전트가 사용자 입력을 기다리는 중이거나 차례를 끝냈을 때 명확한 신호를 제공하지 않습니다. 현재 감지는 휴리스틱(유휴 타이머, 턴 지속 시간 이벤트) 기반이며 종종 감지 오류가 발생합니다. 에이전트가 잠시 잘못된 상태를 표시하거나 전환을 놓칠 수 있습니다.
- **Windows-only testing (Windows 전용 테스트 환경)** — 이 확장 프로그램은 Windows 11에서만 테스트되었습니다. macOS 또는 Linux에서도 작동할 수 있지만 해당 플랫폼에서 파일 감시, 경로 또는 터미널 동작과 관련하여 예기치 않은 문제가 발생할 수 있습니다.

## Roadmap (로드맵)

다음 영역에서의 기여를 환영합니다:

- **Improve agent-terminal reliability (에이전트-터미널 안정성 향상)** — 캐릭터와 Gemini CLI 인스턴스 간의 더 견고한 연결 및 동기화
- **Better status detection (상태 감지 개선)** — 에이전트 상태 전환(대기, 완료, 권한 필요)에 대해 더 명확한 신호 찾기 및 제안
- **Community assets (커뮤니티 에셋)** — 타사 에셋을 구매하지 않고 누구나 자유롭게 사용할 수 있는 픽셀 아트 타일셋 또는 캐릭터 제공
- **Agent creation and definition (에이전트 생성 및 정의)** — 에이전트를 실행하기 전에 커스텀 스킬, 시스템 프롬프트, 이름 및 스킨 정의
- **Desks as directories (디렉토리로서의 책상)** — 책상을 클릭하여 작업 디렉토리를 선택하고, 에이전트를 끌어다 놓거나 클릭하여 배치하여 특정 책상/프로젝트로 이동
- **Gemini CLI agent teams (Gemini CLI 에이전트 팀)** — 멀티 에이전트 조정 및 통신을 시각화하는 [에이전트 팀](https://google.github.io/gemini-cli/agent-teams) 기본 지원
- **Git worktree support (Git 워크트리 지원)** — 에이전트가 동일한 파일에 대한 병렬 작업으로 인한 충돌을 피하기 위해 다른 워크트리에서 작업 지원
- **Support for other agentic frameworks (기타 에이전트 프레임워크 지원)** — [OpenCode](https://github.com/nichochar/opencode) 또는 영감을 주는 [simile.ai](https://simile.ai/)와 같이 픽셀 아트 인터페이스 내에서 실행하고 싶은 다양한 형태의 기타 에이전트 실험 지원

관심 있는 내용이 있다면 편히 이슈를 등록하거나 PR을 제출해 주세요.

## Contributions (기여)

이 프로젝트에 참여하는 방법에 대한 설명은 [CONTRIBUTORS.md](CONTRIBUTORS.md)를 참조하세요.

참여하기 전에 [Code of Conduct(행동 강령)](CODE_OF_CONDUCT.md)을 읽어주세요.

## Supporting the Project (프로젝트 후원)

Pixel Agents가 유용하다고 생각되신다면 개발을 후원해 주세요:

<a href="https://github.com/sponsors/pablodelucca">
  <img src="https://img.shields.io/badge/Sponsor-GitHub-ea4aaa?logo=github" alt="GitHub Sponsors">
</a>
<a href="https://ko-fi.com/pablodelucca">
  <img src="https://img.shields.io/badge/Support-Ko--fi-ff5e5b?logo=ko-fi" alt="Ko-fi">
</a>

## License (라이선스)

이 프로젝트는 [MIT License](LICENSE)에 따라 라이선스가 부여됩니다.
