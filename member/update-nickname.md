## 닉네임 수정

### 개요

로그인한 사용자의 닉네임을 수정합니다.

### 📌 엔드포인트

`PATCH /member/nickname`

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

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `nickname` | String | 변경할 닉네임 | ✅ |

### ▶️ 요청 예시

```json
{
  "nickname": "새로운닉네임"
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
| `200 OK` | 닉네임 수정 완료 |

### 응답 예시

```json
{
  "code": "NICKNAME_UPDATED",
  "message": "닉네임이 성공적으로 수정되었습니다.",
  "data": null
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `400 Bad Request` | 이미 존재하는 닉네임 | `DUPLICATE_NICKNAME` |
| `400 Bad Request` | 닉네임 형식이 올바르지 않음 | `INVALID_NICKNAME` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

**응답 예시 (400 Bad Request)**

```json
{
  "code": "INVALID_NICKNAME",
  "message": "닉네임 형식이 올바르지 않습니다."
}
```

</aside>
