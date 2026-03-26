# Openclaw 에 채널로 discord 를 연결하는 방법

```
0. discord 서버 생성
---
     Discord 좌측 서버 목록에서 + 버튼
     Create My Own
     For me and my friends 
     서버 이름 아무거나 (예: OpenClaw-Test)
---
1. Discord Bot 생성
2. Bot Token 확보
3. Bot을 Discord 서버에 초대
4. openclaw.json에 token 설정
5. OpenClaw 재시작
6. Discord에서 메시지 보내기


https://discord.com/developers/applications 에 접속하여 new application을 생성하고,
Bot을 추가한다.
   - Bot Token 복사하여 저장

Discord 서버에 bot 초대 (메뉴중 OAuth2 -> URL Generator)
scope 
   bot
Bot permission
   Send Message
   Read Message History


생성된 URL로 접속하고 내 discord 서버를 선택하여 Bot 초대 승인
openclaw.json 에 아래 추가
---

  "channels": {
    "discord": {
      "enabled": true,
      "token": "DISCORD_BOT_TOKEN"
    }
  }
---

openclaw gateway restart
openclaw plugins list | grep discord
```