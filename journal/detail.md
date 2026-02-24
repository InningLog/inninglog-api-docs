## 직관일지 상세 조회

### 개요

특정 직관일지의 상세 정보를 조회합니다. 경기 정보, 감정 태그, 후기, 좋아요/스크랩 상태를 포함합니다.

### 📌 엔드포인트

`GET /journals/detail/{journalId}`

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

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `journalId` | Long | 조회할 직관일지의 고유 ID |

### ▶️ 요청 예시

```
GET /journals/detail/42
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 직관일지 상세 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.jourDetail.journalId` | Long | 직관일지 ID |
| `data.jourDetail.gameDate` | String | 경기 날짜 (`yyyy-MM-dd HH:mm`) |
| `data.jourDetail.supportTeamSC` | String | 우리팀 숏코드 |
| `data.jourDetail.opponentTeamSC` | String | 상대팀 숏코드 |
| `data.jourDetail.ourScore` | int | 우리팀 점수 |
| `data.jourDetail.theirScore` | int | 상대팀 점수 |
| `data.jourDetail.stadiumSC` | String | 경기장 숏코드 |
| `data.jourDetail.emotion` | String | 감정 태그 |
| `data.jourDetail.media_url` | String | 이미지 URL (Presigned URL) |
| `data.jourDetail.review_text` | String | 후기글 |
| `data.jourDetail.commentCount` | long | 댓글 수 |
| `data.jourDetail.likeCount` | long | 좋아요 수 |
| `data.jourDetail.likedByMe` | boolean | 내가 좋아요 눌렀는지 여부 |
| `data.jourDetail.scrapCount` | long | 스크랩 수 |
| `data.jourDetail.scrapedByMe` | boolean | 내가 스크랩했는지 여부 |
| `data.seatViewId` | Long | 연관된 좌석시야 ID (`null` 가능) |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "jourDetail": {
      "journalId": 42,
      "gameDate": "2025-06-22 18:30",
      "supportTeamSC": "OB",
      "opponentTeamSC": "LG",
      "ourScore": 5,
      "theirScore": 3,
      "stadiumSC": "JAM",
      "emotion": "THRILLED",
      "media_url": "https://s3.amazonaws.com/...",
      "review_text": "오늘 경기 짜릿했다! 역전승!",
      "commentCount": 3,
      "likeCount": 12,
      "likedByMe": true,
      "scrapCount": 5,
      "scrapedByMe": false
    },
    "seatViewId": 15
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 작성하지 않은 일지 | `JOURNAL_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
