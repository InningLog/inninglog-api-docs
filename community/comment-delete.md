## 댓글 삭제

### 개요

본인이 작성한 댓글을 삭제합니다. 소프트 삭제(Soft Delete) 방식으로 처리되어, 삭제된 댓글은 "삭제된 댓글입니다."로 표시됩니다.

### 엔드포인트

`DELETE /community/comments/{commentId}`

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
| `commentId` | Long | 삭제할 댓글 ID |

### 요청 예시

```
DELETE /community/comments/5
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 댓글 삭제 완료 |

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
| `404 Not Found` | 존재하지 않는 댓글 | `COMMENT_NOT_FOUND` |
| `401 Unauthorized` | 본인 댓글만 삭제 가능 | `UNAUTHORIZED_ACCESS` |

</aside>
