<!-- AUTO-GENERATED -->

## 카카오 로그인 페이지 요청

### 개요

프론트에서 카카오 로그인 페이지로 리다이렉트하기 위한 URL을 반환합니다.

### 엔드포인트

`GET /login/page`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

### 응답 (Response)

#### 200 카카오 로그인 URL 반환

| 필드명 | 타입 | 설명 |
|--------|------|------|
| location | String | 카카오 로그인 리다이렉트 URL |
