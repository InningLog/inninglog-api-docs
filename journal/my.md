## 내가 쓴 일지 목록

### 개요

마이페이지에서 내가 작성한 직관일지 목록을 조회합니다. 무한 스크롤(Slice) 방식을 사용합니다.

### 엔드포인트

`GET /journals/my`

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
| `page` | int | 페이지 번호 (0부터 시작) | |
| `size` | int | 한 페이지 아이템 수 | |

### 요청 예시

```
GET /journals/my?page=0&size=10
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 내 일지 목록 조회 성공 |

**Body (SliceResponse)**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.content[]` | Array | 직관일지 목록 |
| `data.content[].journalId` | Long | 직관일지 ID |
| `data.content[].media_url` | String | 이미지 S3 URL |
| `data.content[].resultScore` | String | 경기 결과 (`WIN`, `LOSE`, `DRAW`) |
| `data.content[].emotion` | String | 감정 태그 |
| `data.content[].gameDate` | String | 경기 날짜 (`yyyy-MM-dd HH:mm`) |
| `data.content[].supportTeamSC` | String | 우리팀 숏코드 |
| `data.content[].opponentTeamSC` | String | 상대팀 숏코드 |
| `data.content[].stadiumSC` | String | 경기장 숏코드 |
| `data.content[].likeCount` | Long | 좋아요 수 |
| `data.content[].commentCount` | Long | 댓글 수 |
| `data.content[].scrapCount` | Long | 스크랩 수 |
| `data.content[].likedByMe` | Boolean | 내가 좋아요 눌렀는지 |
| `data.content[].scrapedByMe` | Boolean | 내가 스크랩했는지 |
| `data.currentPage` | int | 현재 페이지 |
| `data.size` | int | 페이지 크기 |
| `data.hasNext` | boolean | 다음 페이지 존재 여부 |
| `data.hasPrevious` | boolean | 이전 페이지 존재 여부 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "content": [
      {
        "journalId": 1,
        "media_url": "https://s3.amazonaws.com/...",
        "resultScore": "WIN",
        "emotion": "THRILLED",
        "gameDate": "2025-06-22 18:30",
        "supportTeamSC": "OB",
        "opponentTeamSC": "LG",
        "stadiumSC": "JAM",
        "likeCount": 5,
        "commentCount": 2,
        "scrapCount": 1,
        "likedByMe": false,
        "scrapedByMe": false
      }
    ],
    "currentPage": 0,
    "size": 10,
    "hasNext": false,
    "hasPrevious": false
  }
}
```

</aside>
