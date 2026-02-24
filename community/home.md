## 커뮤니티 홈 조회

### 개요

커뮤니티 홈 화면 정보를 조회합니다. 사용자의 응원팀 정보와 인기 게시글 2개를 반환합니다.

### 엔드포인트

`GET /community/home`

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
| `200 OK` | 커뮤니티 홈 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.supportTeamShortCode` | String | 내 응원팀 숏코드 |
| `data.popularPosts[]` | Array | 인기 게시글 목록 (최대 2개) |
| `data.popularPosts[].postId` | Long | 게시글 ID |
| `data.popularPosts[].teamShortCode` | String | 게시판 팀 숏코드 |
| `data.popularPosts[].title` | String | 게시글 제목 |
| `data.popularPosts[].content` | String | 게시글 본문 |
| `data.popularPosts[].likeCount` | long | 좋아요 수 |
| `data.popularPosts[].scrapCount` | long | 스크랩 수 |
| `data.popularPosts[].commentCount` | long | 댓글 수 |
| `data.popularPosts[].thumbImageUrl` | String | 대표 이미지 URL (없으면 `null`) |
| `data.popularPosts[].imageCount` | Long | 게시글 이미지 수 |
| `data.popularPosts[].postAt` | String | 작성일 (`yyyy-MM-dd HH:mm`) |
| `data.popularPosts[].likedByMe` | boolean | 내가 좋아요 눌렀는지 |
| `data.popularPosts[].scrapedByMe` | boolean | 내가 스크랩했는지 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "supportTeamShortCode": "LG",
    "popularPosts": [
      {
        "postId": 10,
        "teamShortCode": "LG",
        "title": "오늘 트윈스 경기 보셨나요?",
        "content": "진짜 역대급 경기였음...",
        "likeCount": 25,
        "scrapCount": 8,
        "commentCount": 12,
        "thumbImageUrl": "https://s3.amazonaws.com/...",
        "imageCount": 3,
        "postAt": "2025-06-22 20:00",
        "likedByMe": true,
        "scrapedByMe": false
      }
    ]
  }
}
```

</aside>
