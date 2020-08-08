# Discord-Publisher

## 설명
**공지 채널에 메시지 나 뉴스를 게시하세요!**

## 동기 예제
`봇이 관리자 권한이 있는 상태여야 합니다.`
```py
import requests

Bot_Token = "" # 자신의 디스코드 봇토큰 (발행을 할 서버에 봇이 있어야함)

channel_id = 000000000000000000 # 채널아이디
message_id = 000000000000000000 # 메시지아이디

URL = f"https://discord.com/api/v6/channels/{channel_id}/messages/{message_id}/crosspost"
headers = {'Authorization': f'Bot {Bot_Token}'}
r = requests.post(URL, headers=headers)
print(r)
```
---
## 비동기 예제
`봇이 공지 채널에 메시지 읽기, 메시지 보내기, 메시지 관리 권한만 있으면 가능합니다.`
```py
import aiohttp
import asyncio

Bot_Token = "" # 자신의 디스코드 봇토큰 (발행을 할 서버에 봇이 있어야함)

channel_id = 000000000000000000 # 채널아이디
message_id = 000000000000000000 # 메시지아이디

async def POST():
    
    async with aiohttp.ClientSession() as session:
        headers = {
            'Authorization': f'Bot {Bot_Token}'
        }
        async with session.post(
            f"https://discord.com/api/v6/channels/{channel_id}/messages/{message_id}/crosspost",
            headers=headers
            ) as r:
                print(r.status)
                if r.status == 200:
                    print("발신성공")
                    
asyncio.run(POST())
```

Discord : `OWO#1996`
