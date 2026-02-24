## 카카오 로그인 페이지 URL 조회

### 개요

카카오 OAuth 로그인 페이지로 리다이렉트할 URL을 반환합니다. 클라이언트는 이 URL로 사용자를 이동시켜 카카오 로그인을 진행합니다.

### 엔드포인트

`GET /login/page`

### 인증

- **인증 필요 여부:** 필요 없음

---

### 요청 (Request)

<aside>

### Headers

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `Content-Type` | String | `application/json` | |

별도의 Path Parameters, Query Parameters, Body가 필요하지 않습니다.

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 로그인 페이지 URL 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.location` | String | 카카오 로그인 리다이렉트 URL |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "location": "https://kauth.kakao.com/oauth/authorize?response_type=code&client_id=abc123&redirect_uri=http://localhost:8080/callback"
  }
}
```

</aside>
