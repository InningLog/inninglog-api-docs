## 게시글 좋아요 / 좋아요 취소

### 개요

게시글에 좋아요를 누르거나 취소합니다.

---

## 게시글 좋아요

### 📌 엔드포인트

`POST /community/posts/{postId}/likes`

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
| `postId` | Long | 좋아요할 게시글 ID |

</aside>

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 좋아요 성공 |

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
| `400 Bad Request` | 이미 좋아요를 누른 콘텐츠 | `LIKE_ALREADY_EXISTS` |

</aside>

---

---

## 게시글 좋아요 취소

### 📌 엔드포인트

`DELETE /community/posts/{postId}/likes`

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
| `postId` | Long | 좋아요 취소할 게시글 ID |

</aside>

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 좋아요 취소 성공 |

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
| `404 Not Found` | 존재하지 않는 좋아요 | `LIKE_NOT_FOUND` |

</aside>
