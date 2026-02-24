## 경기 정보 조회

### 개요

직관일지 작성 전, 특정 경기의 상세 정보를 조회합니다.

### 엔드포인트

`GET /journals/contents`

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

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `gameId` | String | 경기 고유 ID (예: `20250619OBSS0`) | |

### 요청 예시

```
GET /journals/contents?gameId=20250619OBSS0
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 경기 정보 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.gameId` | String | 경기 고유 ID |
| `data.gameDate` | String | 경기 시작 날짜 및 시간 (`yyyy-MM-dd HH:mm`) |
| `data.supportTeamSC` | String | 우리팀 숏코드 |
| `data.opponentTeamSC` | String | 상대팀 숏코드 |
| `data.stadiumSC` | String | 경기장 숏코드 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "gameId": "20250619OBSS0",
    "gameDate": "2025-06-19 18:30",
    "supportTeamSC": "OB",
    "opponentTeamSC": "SS",
    "stadiumSC": "JAM"
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 등록되지 않은 경기 | `GAME_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
