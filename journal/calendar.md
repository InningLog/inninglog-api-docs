## 캘린더 일지 목록

### 개요

본인의 직관일지를 캘린더 형태로 조회합니다. 경기 결과(WIN/LOSE/DRAW)로 필터링할 수 있습니다.

### 엔드포인트

`GET /journals/calendar`

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
| `resultScore` | String | 경기 결과 필터 (`WIN`, `LOSE`, `DRAW`) | |

### 요청 예시

```
GET /journals/calendar
GET /journals/calendar?resultScore=WIN
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 캘린더 일지 목록 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data[]` | Array | 직관일지 목록 |
| `data[].journalId` | Long | 직관일지 ID |
| `data[].ourScore` | int | 우리팀 점수 |
| `data[].theirScore` | int | 상대팀 점수 |
| `data[].resultScore` | String | 경기 결과 (`WIN`, `LOSE`, `DRAW`) |
| `data[].gameDate` | String | 경기 날짜 (`yyyy-MM-dd HH:mm`) |
| `data[].supportTeamSC` | String | 우리팀 숏코드 |
| `data[].opponentTeamSC` | String | 상대팀 숏코드 |
| `data[].stadiumSC` | String | 경기장 숏코드 |

### 응답 예시

```json
{
  "code": "JOURNAL_LIST_FETCHED",
  "message": "직관 일지 리스트 조회 성공",
  "data": [
    {
      "journalId": 1,
      "ourScore": 5,
      "theirScore": 3,
      "resultScore": "WIN",
      "gameDate": "2025-06-01 18:30",
      "supportTeamSC": "OB",
      "opponentTeamSC": "LG",
      "stadiumSC": "JAM"
    },
    {
      "journalId": 2,
      "ourScore": 2,
      "theirScore": 4,
      "resultScore": "LOSE",
      "gameDate": "2025-06-05 18:30",
      "supportTeamSC": "OB",
      "opponentTeamSC": "SS",
      "stadiumSC": "DAE"
    }
  ]
}
```

### 일지 없음 응답 예시

```json
{
  "code": "JOURNAL_EMPTY",
  "message": "해당 조건에 해당하는 직관 일지가 없습니다.",
  "data": []
}
```

</aside>
