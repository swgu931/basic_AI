# OpenClaw

## install
curl -fsSL https://openclaw.ai/install.sh | bash


## documents

https://openclaw.ai/

https://docs.openclaw.ai/

https://docs.openclaw.ai/web/control-ui

http://127.0.0.1:18789/

```
◇  Hooks ──────────────────────────────────────────────────────────╮
│                                                                  │
│  Hooks let you automate actions when agent commands are issued.  │
│  Example: Save session context to memory when you issue /new.    │
│                                                                  │
│  Learn more: https://docs.openclaw.ai/automation/hooks           │
│                                                                  │
├──────────────────────────────────────────────────────────────────╯
│
◇  Enable hooks?
│  Skip for now
Config overwrite: /home/mssw/.openclaw/openclaw.json (sha256 45ad3c9faea99fec56dc4c0f79239a77fa04131c91f3734c68676a978e0c49e4 -> 0e8b01435b8861e74a6a7b11041f843c8196ee5391e75f952602ee0d9199f0c1, backup=/home/mssw/.openclaw/openclaw.json.bak)
│
◇  Systemd ────────────────────────────────────────────────────────────────────────────────╮
│                                                                                          │
│  Linux installs use a systemd user service by default. Without lingering, systemd stops  │
│  the user session on logout/idle and kills the Gateway.                                  │
│  Enabling lingering now (may require sudo; writes /var/lib/systemd/linger).              │
│                                                                                          │
├──────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  Systemd ─────────────────────────────╮
│                                       │
│  Enabled systemd lingering for mssw.  │
│                                       │
├───────────────────────────────────────╯
│
◇  Gateway service runtime ────────────────────────────────────────────╮
│                                                                      │
│  QuickStart uses Node for the Gateway service (stable + supported).  │
│                                                                      │
├──────────────────────────────────────────────────────────────────────╯
│
◓  Installing Gateway service…..
Installed systemd service: /home/mssw/.config/systemd/user/openclaw-gateway.service
◇  Gateway service installed.
│
◇  
Health check failed: gateway closed (1006 abnormal closure (no close frame)): no close reason
  Gateway target: ws://127.0.0.1:18789
  Source: local loopback
  Config: /home/mssw/.openclaw/openclaw.json
  Bind: loopback
│
◇  Health check help ────────────────────────────────╮
│                                                    │
│  Docs:                                             │
│  https://docs.openclaw.ai/gateway/health           │
│  https://docs.openclaw.ai/gateway/troubleshooting  │
│                                                    │
├────────────────────────────────────────────────────╯
│
◇  Optional apps ────────────────────────╮
│                                        │
│  Add nodes for extra features:         │
│  - macOS app (system + notifications)  │
│  - iOS app (camera/canvas)             │
│  - Android app (camera/canvas)         │
│                                        │
├────────────────────────────────────────╯
│
◇  Control UI ───────────────────────────────────────────────────────────────────────────────╮
│                                                                                            │
│  Web UI: http://127.0.0.1:18789/                                                           │
│  Web UI (with token):                                                                      │
│  http://127.0.0.1:18789/#token=50d75f0238a073ef3bcb74a4e673aaea4f5aa878791e9365            │
│  Gateway WS: ws://127.0.0.1:18789                                                          │
│  Gateway: not detected (gateway closed (1006 abnormal closure (no close frame)): no close  │
│  reason)                                                                                   │
│  Docs: https://docs.openclaw.ai/web/control-ui                                             │
│                                                                                            │
├────────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  Workspace backup ────────────────────────────────────────╮
│                                                           │
│  Back up your agent workspace.                            │
│  Docs: https://docs.openclaw.ai/concepts/agent-workspace  │
│                                                           │
├───────────────────────────────────────────────────────────╯
│
◇  Security ──────────────────────────────────────────────────────╮
│                                                                 │
│  Running agents on your computer is risky — harden your setup:  │
│  https://docs.openclaw.ai/security                              │
│                                                                 │
├─────────────────────────────────────────────────────────────────╯
│
◇  Shell completion ────────────────────────────────────────────────────────╮
│                                                                           │
│  Shell completion installed. Restart your shell or run: source ~/.bashrc  │
│                                                                           │
├───────────────────────────────────────────────────────────────────────────╯
│
◇  Dashboard ready ────────────────────────────────────────────────────────────────╮
│                                                                                  │
│  Dashboard link (with token):                                                    │
│  http://127.0.0.1:18789/#token=50d75f0238a073ef3bcb74a4e673aaea4f5aa878791e9365  │
│  Opened in your browser. Keep that tab to control OpenClaw.                      │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────╯
│
◇  Web search (optional) ─────────────────────────────────────────────────────────────────╮
│                                                                                         │
│  If you want your agent to be able to search the web, you’ll need an API key.           │
│                                                                                         │
│  OpenClaw uses Brave Search for the `web_search` tool. Without a Brave Search API key,  │
│  web search won’t work.                                                                 │
│                                                                                         │
│  Set it up interactively:                                                               │
│  - Run: openclaw configure --section web                                                │
│  - Enable web_search and paste your Brave Search API key                                │
│                                                                                         │
│  Alternative: set BRAVE_API_KEY in the Gateway environment (no config changes).         │
│  Docs: https://docs.openclaw.ai/tools/web                                               │
│                                                                                         │
├─────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  What now ─────────────────────────────────────────────────────────────╮
│                                                                        │
│  What now: https://openclaw.ai/showcase ("What People Are Building").  │
│                                                                        │
├────────────────────────────────────────────────────────────────────────╯
│
└  Onboarding complete. Dashboard opened; keep that tab to control OpenClaw.
```


```
OpenClaw에서 제공하는 Hooks는 시스템이 실행되거나 특정 이벤트(명령어 실행 등)가 발생할 때 자동으로 동작하게 만드는 기능 확장 플러그인들입니다.

각 옵션의 상세 의미는 다음과 같습니다.

1. 🚀 boot-md
의미: 서버가 시작될 때 특정 마크다운(BOOT.md) 파일을 자동으로 읽고 실행하는 기능입니다.
용도: 서비스가 켜지자마자 에이전트에게 초기 지침이나 오늘의 할 일 등을 자동으로 주입하고 싶을 때 사용합니다.

2. 📎 bootstrap-extra-files
의미: 에이전트의 작업 공간(Workspace)을 초기화할 때, 미리 지정한 추가 설정 파일이나 데이터를 자동으로 복사해 넣는 기능입니다.
용도: 특정 프로젝트 환경이나 반복적으로 사용하는 설정 파일들을 에이전트가 항상 가지고 시작할 수 있게 해줍니다.

3. 📝 command-logger
의미: 사용자와 AI 사이에 오간 모든 명령어와 실행 결과를 로그 파일(~/.openclaw/logs/commands.log)에 차곡차곡 기록하는 기능입니다.
용도: 나중에 어떤 명령어를 내렸는지 추적하거나, 에러가 발생했을 때 원인을 파악하는 감사(Audit) 및 디버깅 용도로 매우 유용합니다.

4. 💾 session-memory
의미: 대화 세션이 종료되거나 새로 시작될 때, 이전 대화의 핵심 내용을 에이전트의 메모리 공간에 문서 형태로 자동 저장하는 기능입니다.
용도: AI가 과거에 했던 대화나 사용자의 취향을 장기적으로 기억(Long-term memory)하게 만들어, 다음 대화에서도 맥락을 이어가게 돕습니다.
```



1. 마법사(Wizard) 다시 실행 (가장 쉬운 방법)
터미널에서 아래 명령어를 입력하면 처음 설치할 때처럼 단계별 설정을 다시 진행할 수 있습니다.

모든 설정 재구성:

openclaw onboard
간단한 설정 변경:

openclaw configure
(또는 openclaw config라고만 입력해도 마법사가 실행됩니다.)


2. 웹 대시보드에서 수정 (시각적인 방법)
OpenClaw가 실행 중이라면 웹 화면에서 마우스로 설정할 수 있습니다.

대시보드 접속 (보통 터미널에 나온 주소 또는 openclaw dashboard 실행)
상단 메뉴의 Config 또는 Settings 탭으로 이동
Hooks 섹션에서 원하는 항목을 켜고 끄기


3. 파일 직접 수정 (전문가용)
저희가 이전에 했던 것처럼 설정 파일을 직접 열어 편집할 수 있습니다.

경로: ~/.openclaw/openclaw.json
파일 내용 중 hooks 섹션을 찾아 아래와 같이 수정하면 됩니다:
json
"hooks": [
  "command-logger",
  "session-memory"
]
(파일을 저장하면 대부분의 설정은 서비스 재시작 없이 즉시 적용됩니다.)


3.1. boot-md, bootstrap-extra-files 를 설정하는 방법

"hooks": [
    "command-logger",
    "session-memory",
    "boot-md",
    "bootstrap-extra-files"
  ],
  "bootstrapExtraFiles": {
    "include": [
      "/path/to/your/files/*"
    ]
  }
}


#####################################
```
Ollama는 원래 API 키가 필요 없지만, OpenClaw 내부 보안 검증 절차상 **가짜 API 키(더미 키)**라도 등록되어 있어야 실행이 가능합니다. 에러 메시지에서 auth-profiles.json에 정보가 없다고 나오는 이유입니다.

가장 빠르고 확실한 해결 방법 2가지를 안내해 드립니다.

방법 1: 환경 변수로 임시 키 설정 (가장 빠름)
현재 터미널에서 아래 명령어를 입력하여 OpenClaw가 Ollama용 키가 있다고 착각하게 만듭니다.

bash
export OLLAMA_API_KEY="ollama"
openclaw
(매번 입력하기 번거롭다면 ~/.bashrc 파일 끝에 export OLLAMA_API_KEY="ollama"를 추가해 두시면 반영구적으로 해결됩니다.)

방법 2: OpenClaw 명령어로 키 등록 (권장)
환경 변수 설정이 복잡하다면 OpenClaw 자체 명령어를 사용하여 설정 파일에 가짜 키를 박아 넣을 수 있습니다.

bash
openclaw config set models.providers.ollama.apiKey ollama
위 명령어를 실행한 후 다시 openclaw를 실행해 보세요.

만약 여전히 에러가 난다면? (최후의 수단)
에러 메시지에 나온 대로 특정 에이전트의 인증 프로필에 정보를 직접 복제해 주는 명령어입니다.

bash
openclaw agents add main
이미 에이전트가 존재한다고 나오면, openclaw doctor --fix 명령어를 실행해 보세요. 시스템이 누락된 auth-profiles.json 항목을 최신 설정(openclaw.json)을 기반으로 자동으로 생성해 줍니다.

요약: 방법 2를 먼저 실행해 보시고, 그래도 안 되면 방법 1을 적용한 후 실행해 보시기 바랍니다!

gateway는 어떻게 재시작을 하지?
Searched web for "OpenClaw restart gateway command stop start service"

OpenClaw Gateway를 재시작하는 방법은 현재 실행 중인 방식에 따라 몇 가지가 있습니다.

1. 가장 간단한 명령어 (CLI)
터미널에서 아래 명령어를 입력하여 즉시 재시작할 수 있습니다.

bash
openclaw gateway restart
만약 프로세스가 꼬여서 재시작이 안 된다면, 수동으로 껐다 켤 수도 있습니다.

중지: openclaw gateway stop
시작: openclaw gateway
2. Linux 시스템 서비스(systemd) 사용 시
Ubuntu와 같은 리눅스 환경에서 시스템 서비스로 등록해 두었다면 아래 명령어를 사용합니다.

bash
systemctl --user restart openclaw-gateway.service
3. 터미널에서 직접 실행 중인 경우
만약 터미널 창 하나를 열어놓고 openclaw 명령어를 입력해둔 상태라면:

해당 터미널 창에서 **Ctrl + C**를 눌러 프로세스를 강제 종료합니다.
다시 openclaw 명령어를 입력하여 실행합니다.
4. 최후의 방법 (프로세스 강제 종료)
위의 방법들로도 반응이 없을 때는 실행 중인 OpenClaw 프로세스를 직접 찾아 죽인 후 다시 시작합니다.

bash
# 관련 프로세스 찾아서 모두 중지
pkill -f openclaw
# 다시 시작
openclaw
팁: 설정을 변경한 후 적용하기 위해 재시작하는 것이라면, openclaw doctor --fix 명령어를 실행하는 것만으로도 대부분의 설정 꼬임이 풀리고 게이트웨이가 안정적으로 로드됩니다.
```

