## 게시글 삭제

### 개요

본인이 작성한 게시글을 삭제합니다. 게시글에 달린 댓글, 좋아요, 스크랩도 함께 삭제됩니다 (Hard Delete).

### 📌 엔드포인트

`DELETE /community/posts/{postId}`

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

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `postId` | Long | 삭제할 게시글 ID |

### ▶️ 요청 예시

```
DELETE /community/posts/10
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 게시글 삭제 완료 |

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
| `401 Unauthorized` | 본인 게시글만 삭제 가능 | `UNAUTHORIZED_ACCESS` |

</aside>
