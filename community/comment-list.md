## 게시글 댓글 목록 조회

### 개요

게시글에 달린 댓글 목록을 조회합니다. 대댓글은 부모 댓글의 `replies` 배열에 포함됩니다.

### 엔드포인트

`GET /community/posts/{postId}/comments`

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
| `postId` | Long | 댓글을 조회할 게시글 ID |

### 요청 예시

```
GET /community/posts/10/comments
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 댓글 목록 조회 성공 |

**Body**

응답 형식은 [직관일지 댓글 목록 조회](../journal/comment-list.md)와 동일합니다.

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "comments": [
      {
        "commentId": 1,
        "memberShortResDto": {
          "nickName": "야구팬123",
          "profile_url": "https://k.kakaocdn.net/..."
        },
        "writedByMe": false,
        "content": "완전 공감합니다!",
        "commentAt": "2025-06-22 21:00",
        "likeCount": 3,
        "likedByMe": false,
        "isDeleted": false,
        "replies": []
      }
    ]
  }
}
```

</aside>
