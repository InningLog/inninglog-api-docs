<!-- AUTO-GENERATED -->

## 홈 화면 정보 조회

### 개요

유저의 직관 승률과 응원팀 이번 달 경기 일정을 반환합니다.

### 엔드포인트

`GET /home/view`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

### 응답 (Response)

#### 200 요청 성공 시 홈 데이터 반환

| 필드명 | 타입 | 설명 |
|--------|------|------|
| nickName | String | 유저의 닉네임 |
| supportTeamSC | String | 유저의 응원팀 숏코드 |
| myWeaningRate | Integer | 나의 직관 승률 (단위: 할푼리) |
| myTeamSchedule | Object[] | 내 응원 팀의 경기 일정 목록 |
| myTeamSchedule[].myTeam | String | 내 응원 팀의 숏코드 |
| myTeamSchedule[].opponentTeam | String | 경기 상대 팀의 숏코드 |
| myTeamSchedule[].stadium | String | 경기장이 열리는 구장 숏코드 |
| myTeamSchedule[].gameDateTime | String | 경기 일시 (yyyy-MM-dd HH:mm) |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "nickName": "구혜승",
    "supportTeamSC": "OB",
    "myWeaningRate": 1000,
    "myTeamSchedule": [
      {
        "myTeam": "OB",
        "opponentTeam": "SS",
        "stadium": "JAM",
        "gameDateTime": "2025-07-01 18:30"
      },
      {
        "myTeam": "OB",
        "opponentTeam": "KT",
        "stadium": "JAM",
        "gameDateTime": "2025-07-04 18:30"
      }
    ]
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
