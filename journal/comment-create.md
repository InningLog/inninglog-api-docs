## 직관일지 댓글 생성

### 개요

직관일지에 댓글을 작성합니다. 대댓글도 지원합니다.

### 엔드포인트

`POST /journals/{journalId}/comments`

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
| `Content-Type` | String | `application/json` | |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | |

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `journalId` | Long | 댓글을 작성할 직관일지 ID |

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `rootCommentId` | Long | 상위 댓글 ID (대댓글인 경우, 일반 댓글이면 `null`) | |
| `content` | String | 댓글 내용 | |

### 요청 예시 (일반 댓글)

```json
{
  "rootCommentId": null,
  "content": "오늘 경기 정말 좋았겠네요!"
}
```

### 요청 예시 (대댓글)

```json
{
  "rootCommentId": 5,
  "content": "맞아요! 역전 순간이 최고였어요"
}
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 댓글 생성 완료 |

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
| `404 Not Found` | 작성하지 않은 일지 | `JOURNAL_NOT_FOUND` |
| `404 Not Found` | 존재하지 않는 상위 댓글 | `ROOT_COMMENT_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
