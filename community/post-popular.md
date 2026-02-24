## 인기 게시글 목록

### 개요

좋아요 10개 이상의 인기 게시글 목록을 조회합니다. 무한 스크롤(Slice) 방식을 사용합니다.

### 📌 엔드포인트

`GET /community/posts/popular`

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

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `page` | int | 페이지 번호 (0부터 시작) | ⬜️ |
| `size` | int | 한 페이지 아이템 수 | ⬜️ |

### ▶️ 요청 예시

```
GET /community/posts/popular?page=0&size=10
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 인기 게시글 목록 조회 성공 |

**Body (SliceResponse)**

응답 형식은 [팀별 게시글 목록](post-by-team.md)과 동일합니다.

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
    "hasNext": false,
    "hasPrevious": false
  }
}
```

</aside>
