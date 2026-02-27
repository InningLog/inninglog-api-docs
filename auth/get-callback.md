<!-- AUTO-GENERATED -->

## 카카오 로그인 콜백(프론트 신경 쓰지 않아도 됨)

### 개요

카카오 로그인 인가 코드를 통해 JWT 토큰과 사용자 정보를 반환합니다.프론트에서 신경 쓰지 않아도 됨

### 엔드포인트

`GET /callback`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

#### Query Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| code | String | ✅ |  |  |

### 응답 (Response)

#### 200 로그인 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| code | String |  |
| message | String |  |
| data | Object |  |

#### 응답 예시

```json
{
  "code": "LOGIN_SUCCESS",
  "message": "로그인이 성공적으로 되었습니다.",
  "data": {
    "nickname": "야구팬123",
    "newMember": false
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
