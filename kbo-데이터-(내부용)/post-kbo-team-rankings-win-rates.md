<!-- AUTO-GENERATED -->

## POST /api/kbo/team-rankings/win-rates

### 개요

POST /api/kbo/team-rankings/win-rates

### 엔드포인트

`POST /api/kbo/team-rankings/win-rates`

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
| date | String |  |  |  |
| winRates | Object[] |  |  |  |
| winRates[].team | String |  |  |  |
| winRates[].date | String |  |  |  |
| winRates[].winRate | Number |  |  |  |
| totalTeams | Integer |  |  |  |
| crawledAt | String |  |  |  |

### 응답 (Response)

#### 200 OK
