## 게시글 수정

### 개요

본인이 작성한 게시글을 수정합니다. 제목, 본문, 이미지를 변경할 수 있으며, 기존 이미지 유지/삭제와 새 이미지 추가가 가능합니다.

### 📌 엔드포인트

`PATCH /community/posts/{postId}`

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
| `Content-Type` | String | `application/json` | ✅ |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | ✅ |

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `postId` | Long | 수정할 게시글 ID |

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `title` | String | 게시글 제목 | ✅ |
| `content` | String | 게시글 본문 | ✅ |
| `remainImages` | Array | 기존 이미지 중 유지할 이미지 목록 | ⬜️ |
| `remainImages[].remainImageId` | Long | 유지할 기존 이미지 ID | ✅ |
| `remainImages[].sequence` | int | 수정 후 이미지 순서 | ✅ |
| `newImages` | Array | 새로 추가할 이미지 목록 | ⬜️ |
| `newImages[].sequence` | int | 이미지 순서 | ✅ |
| `newImages[].key` | String | 이미지 S3 경로 키 | ✅ |
| `imageCount` | Long | 전체 이미지 개수 (기존 유지 + 신규) | ⬜️ |

### ▶️ 요청 예시

```json
{
  "title": "수정된 제목입니다",
  "content": "수정된 본문 내용입니다",
  "remainImages": [
    {
      "remainImageId": 1,
      "sequence": 1
    }
  ],
  "newImages": [
    {
      "sequence": 2,
      "key": "post/10/new_image.jpg"
    }
  ],
  "imageCount": 2
}
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 게시글 수정 완료 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": null
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 존재하지 않는 게시글 | `POST_NOT_FOUND` |
| `401 Unauthorized` | 본인 게시글만 수정 가능 | `UNAUTHORIZED_ACCESS` |

</aside>
