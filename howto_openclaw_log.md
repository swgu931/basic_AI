openclaw onboard --install-daemon 

🦞 OpenClaw 2026.4.26 (be8c246) — I run on caffeine, JSON5, and the audacity of "it worked on my machine."

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
██░▄▄▄░██░▄▄░██░▄▄▄██░▀██░██░▄▄▀██░████░▄▄▀██░███░██
██░███░██░▀▀░██░▄▄▄██░█░█░██░█████░████░▀▀░██░█░█░██
██░▀▀▀░██░█████░▀▀▀██░██▄░██░▀▀▄██░▀▀░█░██░██▄▀▄▀▄██
▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀
                  🦞 OPENCLAW 🦞                    
 
┌  OpenClaw setup
│
◇  Security disclaimer ──────────────────────────────────────────────────────────────────────╮
│                                                                                            │
│  OpenClaw is a hobby project and still in beta. Expect sharp edges.                        │
│  By default, OpenClaw is a personal agent: one trusted operator boundary.                  │
│  This bot can read files and run actions if tools are enabled.                             │
│  A bad prompt can trick it into doing unsafe things.                                       │
│                                                                                            │
│  OpenClaw is not a hostile multi-tenant boundary by default.                               │
│  If multiple users can message one tool-enabled agent, they share that delegated tool      │
│  authority.                                                                                │
│                                                                                            │
│  If you’re not comfortable with security hardening and access control, don’t run           │
│  OpenClaw.                                                                                 │
│  Ask someone experienced to help before enabling tools or exposing it to the internet.     │
│                                                                                            │
│  Recommended baseline                                                                      │
│  - Pairing/allowlists + mention gating.                                                    │
│  - Multi-user/shared inbox: split trust boundaries (separate gateway/credentials, ideally  │
│    separate OS users/hosts).                                                               │
│  - Sandbox + least-privilege tools.                                                        │
│  - Shared inboxes: isolate DM sessions (session.dmScope: per-channel-peer) and keep tool   │
│    access minimal.                                                                         │
│  - Keep secrets out of the agent’s reachable filesystem.                                   │
│  - Use the strongest available model for any bot with tools or untrusted inboxes.          │
│                                                                                            │
│  Run regularly                                                                             │
│  openclaw security audit --deep                                                            │
│  openclaw security audit --fix                                                             │
│                                                                                            │
│  Learn more                                                                                │
│  - https://docs.openclaw.ai/gateway/security                                               │
│                                                                                            │
├────────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  I understand this is personal-by-default and shared/multi-user use requires lock-down. Continue?
│  Yes
│
◇  Setup mode
│  QuickStart
│
◇  QuickStart ─────────────────────────╮
│                                      │
│  Gateway port: 18789                 │
│  Gateway bind: Loopback (127.0.0.1)  │
│  Gateway auth: Token (default)       │
│  Tailscale exposure: Off             │
│  Direct to chat channels.            │
│                                      │
├──────────────────────────────────────╯
│
◇  Model/auth provider
│  Custom Provider
│
◇  API Base URL
│  http://127.0.0.1:11434
│
◇  How do you want to provide this API key?
│  Paste API key now
│
│
│
◇  Model ID
│  gpt-4.1-nano
│
◇  Verification failed: status 404
│
◇  What would you like to change?
│  Change base URL
│
◇  API Base URL
│
◇  How do you want to provide this API key?
│  Paste API key now
│
│
◇  Verification successful.
│
◇  Model alias (optional)
│
◇  How channels work ───────────────────────────────────────────────────────────────────────╮
│                                                                                           │
│  DM security: default is pairing; unknown DMs get a pairing code.                         │
│  Approve with: openclaw pairing approve <channel> <code>                                  │
│  Public DMs require dmPolicy="open" + allowFrom=["*"].                                    │
│  Multi-user DMs: run: openclaw config set session.dmScope "per-channel-peer" (or          │
│  "per-account-channel-peer" for multi-account channels) to isolate sessions.              │
│  Docs: channels/pairing                  │
│                                                                                           │
│  Feishu: 飞书/Lark enterprise messaging with doc/wiki/drive tools.                        │
│  Google Chat: Google Workspace Chat app with HTTP webhook.                                │
│  Nostr: Decentralized protocol; encrypted DMs via NIP-04.                                 │
│  Microsoft Teams: Teams SDK; enterprise support.                                          │
│  Mattermost: self-hosted Slack-style chat; install the plugin to enable.                  │
│  Nextcloud Talk: Self-hosted chat via Nextcloud Talk webhook bots.                        │
│  Matrix: open protocol; install the plugin to enable.                                     │
│  BlueBubbles: iMessage via the BlueBubbles mac app + REST API.                            │
│  LINE: LINE Messaging API webhook bot.                                                    │
│  Zalo: Vietnam-focused messaging platform with Bot API.                                   │
│  Zalo Personal: Zalo personal account via QR code login.                                  │
│  Synology Chat: Connect your Synology NAS Chat to OpenClaw with full agent capabilities.  │
│  Tlon: decentralized messaging on Urbit; install the plugin to enable.                    │
│  Discord: very well supported right now.                                                  │
│  iMessage: this is still a work in progress.                                              │
│  IRC: classic IRC networks with DM/channel routing and pairing controls.                  │
│  QQ Bot: connect to QQ via official QQ Bot API with group chat and direct message         │
│  support.                                                                                 │
│  Signal: signal-cli linked device; more setup (David Reagans: "Hop on Discord.").         │
│  Slack: supported (Socket Mode).                                                          │
│  Telegram: simplest way to get started — register a bot with @BotFather and get going.    │
│  Twitch: Twitch chat integration                                                          │
│  WhatsApp: works with your own number; recommend a separate phone + eSIM.                 │
│  WeCom: Enterprise messaging and documents, scheduling, task tools.                       │
│  Yuanbao: Tencent Yuanbao AI assistant conversation channel.                              │
│                                                                                           │
├───────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  Select channel (QuickStart)
│  Discord (Bot API)
│
◇  Install Discord plugin?
│  Use local plugin path
│
◇  Discord bot token ───────────────────────────────────────────────────────────────────────╮
│                                                                                           │
│  1) Discord Developer Portal -> Applications -> New Application                           │
│  2) Bot -> Add Bot -> Reset Token -> copy token                                           │
│  3) OAuth2 -> URL Generator -> scope 'bot' -> invite to your server                       │
│  Tip: enable Message Content Intent if you need message text. (Bot -> Privileged Gateway  │
│  Intents -> Message Content Intent)                                                       │
│  Docs: discord                                    │
│                                                                                           │
├───────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  How do you want to provide this Discord bot token?
│
│
◇  Configure Discord channels access?
│  Yes
│
◇  Discord channels access
│  Allowlist (recommended)
│
◇  Discord channels allowlist (comma-separated)
│
│
◇  Selected channels ───────────────────────────────────────────────────────────────────────────────────────╮
│                                                                                                           │
│  Discord — very well supported right now. Docs: discord  │
│                                                                                                           │
├───────────────────────────────────────────────────────────────────────────────────────────────────────────╯
Updated ~/.openclaw/openclaw.json
Workspace OK: ~/.openclaw/workspace
Sessions OK: ~/.openclaw/agents/main/sessions
│
◇  Web search ─────────────────────────────────────────────────────────────────╮
│                                                                              │
│  Web search lets your agent look things up online.                           │
│  Choose a provider. Some providers need an API key, and some work key-free.  │
│  Docs: https://docs.openclaw.ai/tools/web                                    │
│                                                                              │
├──────────────────────────────────────────────────────────────────────────────╯
│
◇  Search provider
│  Skip for now
│
◇  Skills status ─────────────╮
│                             │
│  Eligible: 8                │
│  Missing requirements: 41   │
│  Unsupported on this OS: 7  │
│  Blocked by allowlist: 0    │
│                             │
├─────────────────────────────╯
│
◇  Configure skills now? (recommended)
│  Yes
│
◇  Install missing skill dependencies
│  Skip for now
│
◇  Set GOOGLE_PLACES_API_KEY for goplaces?
│  No
│
◇  Set NOTION_API_KEY for notion?
│  No
│
◇  Set OPENAI_API_KEY for openai-whisper-api?
│  No
│
◇  Set ELEVENLABS_API_KEY for sag?
│  No
│
◇  Hooks ──────────────────────────────────────────────────────────────────╮
│                                                                          │
│  Hooks let you automate actions when agent commands are issued.          │
│  Example: Save session context to memory when you issue /new or /reset.  │
│                                                                          │
│  Learn more: https://docs.openclaw.ai/automation/hooks                   │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────╯
│
◇  Enable hooks?
│  Skip for now
Config overwrite: /home/mssw/.openclaw/openclaw.json (sha256 dfcb1317e2a32b90fa6c6b9f1d8d0e7cd179dcdfb2d431202c5a5d53f01dd434 -> 5c451f859cedda9106637df1ba094628d16d3f5d1504b3779d4c704fef43cc1c, backup=/home/mssw/.openclaw/openclaw.json.bak)
│
◇  Gateway service runtime ────────────────────────────────────────────╮
│                                                                      │
│  QuickStart uses Node for the Gateway service (stable + supported).  │
│                                                                      │
├──────────────────────────────────────────────────────────────────────╯
│
◇  Gateway service already installed
│  Restart
│
◐  Restarting Gateway service…Restarted systemd service: openclaw-gateway.service
◇  Gateway service restarted.
Health check failed: connect ECONNREFUSED 127.0.0.1:18789
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
◇  Control UI ─────────────────────────────────────────────────────────────────────╮
│                                                                                  │
│  Web UI: http://127.0.0.1:18789/                                                 │
│  Web UI (with token):                                                            │
│  http://127.0.0.1:18789/#token=b8789f2a00ab5250e1020043dc8ac4109356339f315348b4  │
│  Gateway WS: ws://127.0.0.1:18789                                                │
│  Gateway: not detected (connect ECONNREFUSED 127.0.0.1:18789)                    │
│  Docs: https://docs.openclaw.ai/web/control-ui                                   │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────╯
│
◇  Start TUI (best option!) ─────────────────────────────────╮
│                                                            │
│  This is the defining action that makes your agent you.    │
│  Please take your time.                                    │
│  The more you tell it, the better the experience will be.  │
│  We will send: "Wake up, my friend!"                       │
│                                                            │
├────────────────────────────────────────────────────────────╯
│
◇  How do you want to hatch your bot?
│  Hatch in Terminal (recommended)

🦞 OpenClaw 2026.4.26 (be8c246) — If something's on fire, I can't extinguish it—but I can write a beautiful postmortem.

 openclaw tui - local embedded - agent main - session main                                                                                                                                                  

 session agent:main:main                                                                                                                                                                                    

                                                                                                                                                                                                            
Wake up, my friend!                                                                                                                                                                                         
                                                                                                                                                                                                            
 local ready | cleared input; press ctrl+c again to exit                                                                                                                                                    
 agent main | session main | custom-azureopenai-swgu-openai-azure-com/gpt-4.1-nano | tokens ?/400k                                                                                                          
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
                                                                                                                                                                                                            
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

11:16:29 [model-fallback/decision] model fallback decision: decision=candidate_failed requested=custom-azureopenai-swgu-openai-azure-com/gpt-4.1-nano candidate=custom-azureopenai-swgu-openai-azure-com/gpt-4.1-nano reason=timeout next=none detail=This operation was aborted
11:16:29 [model-fallback/decision] model fallback decision: decision=candidate_failed requested=custom-azureopenai-swgu-openai-azure-com/gpt-4.1-nano candidate=custom-azureopenai-swgu-openai-azure-com/gpt-4.1-nano reason=timeout next=none detail=This operation was aborted
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
◇  Web search ───────────────────────────────────────╮
│                                                    │
│  Web search was skipped. You can enable it later:  │
│    openclaw configure --section web                │
│                                                    │
│  Docs: https://docs.openclaw.ai/tools/web          │
│                                                    │
├────────────────────────────────────────────────────╯
│
◇  What now ─────────────────────────────────────────────────────────────╮
│                                                                        │
│  What now: https://openclaw.ai/showcase ("What People Are Building").  │
│                                                                        │
├────────────────────────────────────────────────────────────────────────╯
│
└  Onboarding complete. Use the dashboard link above to control OpenClaw.


