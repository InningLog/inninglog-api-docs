## 홈 화면 정보 조회

### 개요

홈 화면에 필요한 정보를 조회합니다. 사용자의 직관 승률과 이번 달 응원팀 경기 일정을 제공합니다.

### 엔드포인트

`GET /home/view`

### 인증

- **인증 필요 여부:** JWT 인증 필요

> 요청 헤더(Header)에 아래와 같이 Authorization 필드를 포함해야 합니다.
>
> `Authorization: Bearer {JWT_TOKEN}`

---

### 요청 (Request)

<aside>

### Headers

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | |

별도의 Path Parameters, Query Parameters, Body가 필요하지 않습니다.

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 홈 화면 정보 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.nickName` | String | 유저 닉네임 |
| `data.supportTeamSC` | String | 응원팀 숏코드 |
| `data.myWeaningRate` | int | 직관 승률 (할푼리 단위, ×1000) |
| `data.myTeamSchedule` | Array | 이번 달 응원팀 경기 일정 목록 |
| `data.myTeamSchedule[].myTeam` | String | 내 응원팀 숏코드 |
| `data.myTeamSchedule[].opponentTeam` | String | 상대팀 숏코드 |
| `data.myTeamSchedule[].stadium` | String | 경기장 숏코드 |
| `data.myTeamSchedule[].gameDateTime` | String | 경기 일시 (`yyyy-MM-dd HH:mm`) |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "nickName": "야구천재",
    "supportTeamSC": "OB",
    "myWeaningRate": 667,
    "myTeamSchedule": [
      {
        "myTeam": "OB",
        "opponentTeam": "LG",
        "stadium": "JAM",
        "gameDateTime": "2025-07-01 18:30"
      },
      {
        "myTeam": "OB",
        "opponentTeam": "SS",
        "stadium": "JAM",
        "gameDateTime": "2025-07-03 18:30"
      }
    ]
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |
| `404 Not Found` | 존재하지 않는 회원 | `USER_NOT_FOUND` |

</aside>
