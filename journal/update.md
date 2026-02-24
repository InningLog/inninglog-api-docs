## 직관일지 수정

### 개요

기존 직관일지의 내용을 수정합니다. 점수, 감정 태그, 후기, 이미지, 공개 여부를 변경할 수 있습니다.

### 엔드포인트

`PATCH /journals/update/{journalId}`

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
| `Content-Type` | String | `application/json` | |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | |

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `journalId` | Long | 수정할 직관일지의 고유 ID |

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `ourScore` | int | 우리팀 점수 | |
| `theirScore` | int | 상대팀 점수 | |
| `media_url` | String | 이미지 파일명 (확장자 포함) | |
| `emotion` | String | 감정 태그 | |
| `review_text` | String | 후기글 | |
| `isPublic` | boolean | 공개 여부 (기본값: `false`) | |

### 요청 예시

```json
{
  "ourScore": 6,
  "theirScore": 3,
  "media_url": "updated_photo.jpg",
  "emotion": "MOVED",
  "review_text": "수정된 후기입니다. 감동적인 경기였다!",
  "isPublic": true
}
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 직관일지 수정 완료 |

**Body**

응답 형식은 [직관일지 상세 조회](detail.md)와 동일합니다.

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
      "ourScore": 6,
      "theirScore": 3,
      "stadiumSC": "JAM",
      "emotion": "MOVED",
      "media_url": "https://s3.amazonaws.com/...",
      "review_text": "수정된 후기입니다. 감동적인 경기였다!",
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
| `401 Unauthorized` | 인증 실패 (본인 일지만 수정 가능) | `UNAUTHORIZED_ACCESS` |

</aside>
