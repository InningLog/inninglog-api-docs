## 팀별 게시글 목록

### 개요

특정 팀 게시판의 게시글 목록을 조회합니다. 무한 스크롤(Slice) 방식을 사용합니다.

### 엔드포인트

`GET /community/posts/team/{teamShortCode}`

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

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `teamShortCode` | String | 팀 숏코드 (예: `LG`, `OB`) |

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `page` | int | 페이지 번호 (0부터 시작) | |
| `size` | int | 한 페이지 아이템 수 | |

### 요청 예시

```
GET /community/posts/team/LG?page=0&size=10
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 팀별 게시글 목록 조회 성공 |

**Body (SliceResponse)**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.content[]` | Array | 게시글 목록 |
| `data.content[].postId` | Long | 게시글 ID |
| `data.content[].teamShortCode` | String | 팀 숏코드 |
| `data.content[].title` | String | 게시글 제목 |
| `data.content[].content` | String | 게시글 본문 |
| `data.content[].member.nickName` | String | 작성자 닉네임 |
| `data.content[].member.profile_url` | String | 작성자 프로필 이미지 URL |
| `data.content[].likeCount` | long | 좋아요 수 |
| `data.content[].scrapCount` | long | 스크랩 수 |
| `data.content[].commentCount` | long | 댓글 수 |
| `data.content[].thumbImageUrl` | String | 대표 이미지 URL (없으면 `null`) |
| `data.content[].imageCount` | Long | 이미지 개수 |
| `data.content[].postAt` | String | 작성일 (`yyyy-MM-dd HH:mm`) |
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
        "postId": 10,
        "teamShortCode": "LG",
        "title": "오늘 트윈스 경기 보셨나요?",
        "content": "진짜 역대급 경기였음...",
        "member": {
          "nickName": "야구팬123",
          "profile_url": "https://k.kakaocdn.net/..."
        },
        "likeCount": 25,
        "scrapCount": 8,
        "commentCount": 12,
        "thumbImageUrl": "https://s3.amazonaws.com/...",
        "imageCount": 3,
        "postAt": "2025-06-22 20:00",
        "likedByMe": null,
        "scrapedByMe": null
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

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 등록되지 않은 팀 | `TEAM_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
