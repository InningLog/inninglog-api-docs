## 공개 일지 피드

### 개요

다른 사용자가 공개한 직관일지를 피드 형태로 조회합니다. 팀별 필터링이 가능하며, 무한 스크롤(Slice) 방식을 사용합니다.

### 엔드포인트

`GET /journals/feed`

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
| `teamShortCode` | String | 팀 필터 숏코드 (예: `LG`) | |
| `page` | int | 페이지 번호 (0부터 시작) | |
| `size` | int | 한 페이지 아이템 수 | |

### 요청 예시

```
GET /journals/feed?page=0&size=10
GET /journals/feed?teamShortCode=LG&page=0&size=10
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 공개 일지 피드 조회 성공 |

**Body (SliceResponse)**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.content[]` | Array | 공개 일지 목록 |
| `data.content[].journalId` | Long | 일지 ID |
| `data.content[].thumbnailUrl` | String | 썸네일 이미지 URL (Presigned) |
| `data.content[].member.nickName` | String | 작성자 닉네임 |
| `data.content[].member.profile_url` | String | 작성자 프로필 이미지 URL |
| `data.content[].writedByMe` | boolean | 내가 작성한 일지인지 여부 |
| `data.content[].reviewPreview` | String | 후기 미리보기 (최대 50자) |
| `data.content[].createdAt` | String | 작성 시간 (`yyyy-MM-dd HH:mm`) |
| `data.content[].likeCount` | long | 좋아요 수 |
| `data.content[].likedByMe` | boolean | 내가 좋아요 눌렀는지 |
| `data.content[].commentCount` | long | 댓글 수 |
| `data.content[].scrapCount` | long | 스크랩 수 |
| `data.content[].scrapedByMe` | boolean | 내가 스크랩했는지 |
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
        "journalId": 42,
        "thumbnailUrl": "https://s3.amazonaws.com/...",
        "member": {
          "nickName": "야구천재",
          "profile_url": "https://k.kakaocdn.net/..."
        },
        "writedByMe": false,
        "reviewPreview": "오늘 경기 짜릿했다! 역전승이라니...",
        "createdAt": "2025-06-22 20:30",
        "likeCount": 12,
        "likedByMe": true,
        "commentCount": 3,
        "scrapCount": 5,
        "scrapedByMe": false
      }
    ],
    "currentPage": 0,
    "size": 10,
    "hasNext": true,
    "hasPrevious": false
  }
}
```

</aside>
