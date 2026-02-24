## 경기 일정 조회

### 개요

특정 날짜에 사용자 응원팀의 경기 일정을 조회합니다. 직관일지 작성 전 경기를 선택하기 위해 사용됩니다.

### 📌 엔드포인트

`GET /journals/schedule`

### 🔐 인증

- **인증 필요 여부:** JWT 인증 필요

> 요청 헤더(Header)에 아래와 같이 Authorization 필드를 포함해야 합니다.
>
> `Authorization: Bearer {JWT_TOKEN}`

---

### ▶️ 요청 (Request)

<aside>

### Headers

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | ✅ |

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `gameDate` | String | 조회할 경기 날짜 (`yyyy-MM-dd`) | ✅ |

### ▶️ 요청 예시

```
GET /journals/schedule?gameDate=2025-07-01
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 경기 일정 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.gameId` | String | 경기 고유 ID |
| `data.gameDate` | String | 경기 시작 날짜 및 시간 (`yyyy-MM-dd HH:mm`) |
| `data.supportTeamSC` | String | 우리팀 숏코드 |
| `data.opponentSC` | String | 상대팀 숏코드 |
| `data.stadiumSC` | String | 경기장 숏코드 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "gameId": "20250701LGSS0",
    "gameDate": "2025-07-01 18:30",
    "supportTeamSC": "LG",
    "opponentSC": "SS",
    "stadiumSC": "JAM"
  }
}
```

### 경기 없음 응답 예시

```json
{
  "code": "NO_SCHEDULE_ON_DATE",
  "message": "해당 날짜에 예정된 경기가 없습니다.",
  "data": null
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `400 Bad Request` | 날짜 형식 오류 | `TYPE_MISMATCH` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
