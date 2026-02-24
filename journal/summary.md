## 모아보기 일지 목록

### 개요

본인의 직관일지를 모아보기 형태로 조회합니다. 페이지네이션과 경기 결과 필터링을 지원합니다.

### 엔드포인트

`GET /journals/summary`

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
| `page` | int | 페이지 번호 (0부터 시작) | |
| `size` | int | 한 페이지 아이템 수 | |

### 요청 예시

```
GET /journals/summary?resultScore=WIN&page=0&size=10
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 모아보기 일지 목록 조회 성공 |

**Body (SimplePageResponse)**

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
| `data.content[].likedByMe` | Boolean | 내가 좋아요 눌렀는지 여부 |
| `data.content[].scrapedByMe` | Boolean | 내가 스크랩했는지 여부 |
| `data.pageNumber` | int | 현재 페이지 번호 |
| `data.pageSize` | int | 페이지 크기 |
| `data.isLast` | boolean | 마지막 페이지 여부 |
| `data.totalElements` | long | 총 요소 수 |
| `data.totalPages` | int | 총 페이지 수 |

### 응답 예시

```json
{
  "code": "JOURNAL_LIST_FETCHED",
  "message": "직관 일지 리스트 조회 성공",
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
        "likedByMe": true,
        "scrapedByMe": false
      }
    ],
    "pageNumber": 0,
    "pageSize": 10,
    "isLast": true,
    "totalElements": 1,
    "totalPages": 1
  }
}
```

</aside>
