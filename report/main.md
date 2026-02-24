## 직관 리포트 조회

### 개요

사용자의 직관 리포트 정보를 조회합니다. 총 직관 경기 수, 승률, 응원팀 시즌 승률, 직관 시 베스트/워스트 선수 순위를 제공합니다.

### 📌 엔드포인트

`GET /report/main`

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

별도의 Path Parameters, Query Parameters, Body가 필요하지 않습니다.

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 직관 리포트 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.nickname` | String | 유저 닉네임 |
| `data.totalVisitedGames` | int | 직관한 총 경기 수 |
| `data.winGames` | int | 직관 중 승리 횟수 |
| `data.loseGames` | int | 직관 중 패배 횟수 |
| `data.drawGames` | int | 직관 중 무승부 횟수 |
| `data.myWeaningRate` | int | 직관 승률 (할푼리, ×1000) |
| `data.teamWinRate` | double | 응원팀 시즌 승률 |
| `data.topBatters[]` | Array | 직관 시 베스트 타자 |
| `data.topPitchers[]` | Array | 직관 시 베스트 투수 |
| `data.bottomBatters[]` | Array | 직관 시 워스트 타자 |
| `data.bottomPitchers[]` | Array | 직관 시 워스트 투수 |

**PlayerRankingDto (선수 순위 항목)**

| Key | Type | 설명 |
| --- | --- | --- |
| `playerId` | Long | 선수 ID |
| `playerName` | String | 선수 이름 |
| `playerType` | String | 선수 유형 (`PITCHER` / `HITTER`) |
| `totalHits` | int | 누적 안타 수 (타자) |
| `totalAtBats` | int | 누적 타수 (타자) |
| `totalEarned` | int | 누적 자책점 (투수) |
| `totalInning` | double | 누적 이닝 수 (투수) |
| `halPoongRi` | int | 할푼리 (타율/방어율 ×1000) |

### 응답 예시

```json
{
  "code": "REPORT_GENERATED",
  "message": "리포트가 생성되었습니다.",
  "data": {
    "nickname": "야구천재",
    "totalVisitedGames": 15,
    "winGames": 10,
    "loseGames": 3,
    "drawGames": 2,
    "myWeaningRate": 667,
    "teamWinRate": 0.583,
    "topBatters": [
      {
        "playerId": 101,
        "playerName": "김재환",
        "playerType": "HITTER",
        "totalHits": 18,
        "totalAtBats": 45,
        "totalEarned": 0,
        "totalInning": 0.0,
        "halPoongRi": 400
      }
    ],
    "topPitchers": [
      {
        "playerId": 201,
        "playerName": "곽빈",
        "playerType": "PITCHER",
        "totalHits": 0,
        "totalAtBats": 0,
        "totalEarned": 5,
        "totalInning": 30.0,
        "halPoongRi": 150
      }
    ],
    "bottomBatters": [
      {
        "playerId": 102,
        "playerName": "양석환",
        "playerType": "HITTER",
        "totalHits": 3,
        "totalAtBats": 30,
        "totalEarned": 0,
        "totalInning": 0.0,
        "halPoongRi": 100
      }
    ],
    "bottomPitchers": [
      {
        "playerId": 202,
        "playerName": "브랜든",
        "playerType": "PITCHER",
        "totalHits": 0,
        "totalAtBats": 0,
        "totalEarned": 20,
        "totalInning": 15.0,
        "halPoongRi": 1200
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
| `400 Bad Request` | 직관한 경기가 없음 | `NO_VISITED_GAMES` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
