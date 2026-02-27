<!-- AUTO-GENERATED -->

## POST /api/kbo/games/schedule

### 개요

POST /api/kbo/games/schedule

### 엔드포인트

`POST /api/kbo/games/schedule`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |
| Content-Type | application/json | ✅ |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| games | Object[] |  |  |  |
| games[].awayTeam | String |  |  |  |
| games[].homeTeam | String |  |  |  |
| games[].awayScore | Integer |  |  |  |
| games[].homeScore | Integer |  |  |  |
| games[].stadium | String |  |  |  |
| games[].gameDateTime | String |  |  |  |
| games[].gameId | String |  |  |  |
| games[].boxscoreUrl | String |  |  |  |
| games[].status | String |  |  |  |
| yearMonth | String |  |  |  |
| type | String |  |  |  |

### 응답 (Response)

#### 200 OK
