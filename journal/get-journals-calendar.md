<!-- AUTO-GENERATED -->

## 본인 직관 일지 목록 페이지 - 캘린더

### 개요

JWT 토큰에서 유저 정보를 추출하여 본인의 직관 일지를 조회합니다.

✅ 선택적으로 `resultScore` 파라미터를 통해 경기 결과에 따른 필터링이 가능합니다.

📌 필터링 예시:
- `/journals/calendar?resultScore=승`
- `/journals/calendar?resultScore=패`
- `/journals/calendar?resultScore=무승부`

🔁 필터링 가능한 값:
- 승 (WIN)
- 패 (LOSE)
- 무승부 (DRAW)

### 엔드포인트

`GET /journals/calendar`

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
| resultScore | String (WIN, DRAW, LOSE) |  |  |  |

### 응답 (Response)

#### 200 조회 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| journalId | Long | 직관일지 Id |
| ourScore | Integer | 우리팀 점수 |
| theirScore | Integer | 상대팀 점수 |
| resultScore | String (WIN, DRAW, LOSE) | 경기 결과 승/무/패 중 하나 |
| gameDate | String | 경기 날짜 및 시간 |
| supportTeamSC | String | 우리팀 숏코드 |
| opponentTeamSC | String | 경기 상대 팀 이름 |
| stadiumSC | String | 경기장 이름 |

#### 응답 예시

```json
{
  "code": "JOURNAL_LIST_FETCHED",
  "message": "직관 일지 리스트 조회 성공",
  "data": [
    {
      "journalId": 5,
      "ourScore": 3,
      "theirScore": 1,
      "resultScore": "승",
      "gameDate": "2025-06-03 18:30",
      "supportTeamSC": "OB",
      "opponentTeamSC": "SS",
      "stadiumSC": "JAM"
    }
  ]
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
