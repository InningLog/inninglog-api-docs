<!-- AUTO-GENERATED -->

## 직관 일지 작성 페이지 - 직관 일지 콘텐츠 사전 정보 조회

### 개요

해당 경기 ID(gameId)를 기반으로, 현재 로그인한 사용자의 응원 팀과 상대 팀 정보를 조회합니다.

- 이 API는 직관 일지 작성을 시작하기 전, 작성 페이지에 필요한 정보를 제공합니다.
- 반환되는 데이터는 사용자의 응원 팀, 상대 팀, 경기장 정보, 경기 일시 등을 포함합니다.
- 유저의 응원 팀은 미리 설정되어 있어야 하며, gameId는 유효한 경기여야 합니다.

### 엔드포인트

`GET /journals/contents`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

#### Query Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| gameId | String | ✅ | 경기 Id (gameId) |  |

### 응답 (Response)

#### 200 요청이 정상적으로 처리되었습니다.

| 필드명 | 타입 | 설명 |
|--------|------|------|
| gameId | String | 게임 Id |
| gameDate | String | 경기 날짜 |
| supportTeamSC | String | 우리팀 숏코드 |
| opponentTeamSC | String | 상대팀 숏코드 |
| stadiumSC | String | 경기장 숏코드 |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "gameId": "20250625OBLG0",
    "gameDate": "2025-06-03 18:30",
    "supportTeamSC": "LG",
    "opponentTeamSC": "OB",
    "stadiumSC": "JAM"
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
