## 게시글 단일 조회

### 개요

특정 게시글의 상세 정보를 조회합니다. 작성자 정보, 이미지, 좋아요/스크랩 상태를 포함합니다.

### 엔드포인트

`GET /community/posts/{postId}`

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
| `postId` | Long | 조회할 게시글 ID |

### 요청 예시

```
GET /community/posts/10
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 게시글 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.member.nickName` | String | 작성자 닉네임 |
| `data.member.profile_url` | String | 작성자 프로필 이미지 URL |
| `data.writedByMe` | boolean | 내가 쓴 글인지 여부 |
| `data.postId` | Long | 게시글 ID |
| `data.teamShortCode` | String | 팀 숏코드 |
| `data.title` | String | 게시글 제목 |
| `data.content` | String | 게시글 본문 |
| `data.likeCount` | long | 좋아요 수 |
| `data.likedByMe` | boolean | 내가 좋아요 눌렀는지 |
| `data.scrapCount` | long | 스크랩 수 |
| `data.scrapedByMe` | boolean | 내가 스크랩했는지 |
| `data.commentCount` | long | 댓글 수 |
| `data.postAt` | String | 작성일 (`yyyy-MM-dd HH:mm`) |
| `data.isEdit` | boolean | 수정 여부 |
| `data.imageListResDto.imageResDtos[]` | Array | 이미지 목록 |
| `data.imageListResDto.imageResDtos[].imageId` | Long | 이미지 PK |
| `data.imageListResDto.imageResDtos[].sequence` | int | 이미지 순서 |
| `data.imageListResDto.imageResDtos[].url` | String | 이미지 URL |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "member": {
      "nickName": "야구팬123",
      "profile_url": "https://k.kakaocdn.net/..."
    },
    "writedByMe": false,
    "postId": 10,
    "teamShortCode": "LG",
    "title": "오늘 트윈스 경기 보셨나요?",
    "content": "진짜 역대급 경기였음... 9회말 역전 대박",
    "likeCount": 25,
    "likedByMe": true,
    "scrapCount": 8,
    "scrapedByMe": false,
    "commentCount": 12,
    "postAt": "2025-06-22 20:00",
    "isEdit": false,
    "imageListResDto": {
      "imageResDtos": [
        {
          "imageId": 1,
          "sequence": 1,
          "url": "https://s3.amazonaws.com/..."
        }
      ]
    }
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 존재하지 않는 게시글 | `POST_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
