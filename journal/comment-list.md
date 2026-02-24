## 직관일지 댓글 목록 조회

### 개요

직관일지에 달린 댓글 목록을 조회합니다. 대댓글은 부모 댓글의 `replies` 배열에 포함됩니다.

### 엔드포인트

`GET /journals/{journalId}/comments`

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
| `journalId` | Long | 댓글을 조회할 직관일지 ID |

### 요청 예시

```
GET /journals/42/comments
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

| Key | Type | 설명 |
| --- | --- | --- |
| `data.comments[]` | Array | 댓글 목록 (루트 댓글만) |
| `data.comments[].commentId` | long | 댓글 ID |
| `data.comments[].memberShortResDto.nickName` | String | 작성자 닉네임 |
| `data.comments[].memberShortResDto.profile_url` | String | 작성자 프로필 이미지 URL |
| `data.comments[].writedByMe` | boolean | 내가 작성한 댓글인지 |
| `data.comments[].content` | String | 댓글 내용 (삭제 시 `"삭제된 댓글입니다."`) |
| `data.comments[].commentAt` | String | 작성 시각 (`yyyy-MM-dd HH:mm`) |
| `data.comments[].likeCount` | long | 좋아요 수 |
| `data.comments[].likedByMe` | boolean | 내가 좋아요 눌렀는지 |
| `data.comments[].isDeleted` | boolean | 삭제 여부 |
| `data.comments[].replies[]` | Array | 대댓글 목록 (같은 구조) |

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
        "content": "오늘 경기 정말 좋았겠네요!",
        "commentAt": "2025-06-22 21:00",
        "likeCount": 3,
        "likedByMe": false,
        "isDeleted": false,
        "replies": [
          {
            "commentId": 2,
            "memberShortResDto": {
              "nickName": "야구천재",
              "profile_url": "https://k.kakaocdn.net/..."
            },
            "writedByMe": true,
            "content": "감사합니다! 진짜 최고였어요",
            "commentAt": "2025-06-22 21:15",
            "likeCount": 1,
            "likedByMe": false,
            "isDeleted": false,
            "replies": []
          }
        ]
      }
    ]
  }
}
```

</aside>
