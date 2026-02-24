## 카카오 OAuth 콜백

### 개요

카카오 로그인 완료 후 리다이렉트되는 콜백 엔드포인트입니다. 인가 코드를 받아 JWT 토큰을 발급합니다. 신규 사용자인 경우 자동으로 회원가입이 진행됩니다.

### 📌 엔드포인트

`GET /callback`

### 🔐 인증

- **인증 필요 여부:** 필요 없음

---

### ▶️ 요청 (Request)

<aside>

### Headers

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `Content-Type` | String | `application/json` | ⬜️ |

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `code` | String | 카카오 OAuth 인가 코드 | ✅ |

### ▶️ 요청 예시

```
GET /callback?code=카카오에서_발급받은_인가코드
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 로그인 성공 및 토큰 발급 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.nickname` | String | 사용자 닉네임 |
| `data.isNewMember` | boolean | 신규 가입 여부 (`true`: 신규, `false`: 기존) |
| `data.accessToken` | String | JWT 액세스 토큰 |
| `data.refreshToken` | String | JWT 리프레시 토큰 |

### 응답 예시

```json
{
  "code": "LOGIN_SUCCESS",
  "message": "로그인이 성공적으로 되었습니다.",
  "data": {
    "nickname": "야구팬123",
    "isNewMember": false,
    "accessToken": "eyJhbGciOiJIUzI1NiJ9...",
    "refreshToken": "eyJhbGciOiJIUzI1NiJ9..."
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `500 Internal Server Error` | 카카오 인증 처리 중 오류 | `INTERNAL_SERVER_ERROR` |

**응답 예시 (500 Internal Server Error)**

```json
{
  "code": "INTERNAL_SERVER_ERROR",
  "message": "서버에 문제가 발생했습니다."
}
```

</aside>
