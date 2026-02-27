<!-- AUTO-GENERATED -->

## 본인 직관 일지 캘린더 페이지 - 유저 응원팀의 특정 날짜 경기 일정 조회[팝업 형태]

### 개요

로그인한 유저의 **응원팀 기준으로**, 특정 날짜의 경기 일정을 조회합니다.

    반환된 `gameId`는 이후 **직관 일지 콘텐츠 업로드 API (`/journals/contents`)**에 사용됩니다.

    🗓️ 요청 날짜는 `YYYY-MM-DD` 형식으로 전달해야 합니다.

    ✅ 예시:
    `/journals/schedule?gameDate=2025-07-01`

### 엔드포인트

`GET /journals/schedule`

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
| gameDate | LocalDate | ✅ | 경기 일정 날짜 (예: 2025-07-01) |  |

### 응답 (Response)

#### 200 경기 일정 조회 성공 (또는 해당일에 경기 없음)

| 필드명 | 타입 | 설명 |
|--------|------|------|
| gameId | String | 경기 고유 ID |
| gameDate | String | 경기 시작 날짜 및 시간 |
| supportTeamSC | String | 우리팀 숏코드 |
| opponentSC | String | 상대 팀의 구단 식별자 (shortCode) |
| stadiumSC | String | 경기장이 위치한 구장의 식별자 (shortCode) |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "status": 200,
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "gameId": "20250701OBLT0",
    "gameDate": "2025-06-03 18:30",
    "supportTeamSC": "OB",
    "opponentSC": "LT",
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
