<!-- AUTO-GENERATED -->

## 닉네임 수정

### 개요

JWT 토큰에서 인증된 회원 정보를 추출하여, 사용자의 닉네임을 수정합니다.

요청 바디에는 새로운 닉네임이 포함되어야 하며, 중복된 닉네임일 경우 오류가 반환됩니다.

### 엔드포인트

`PATCH /member/nickname`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |
| Content-Type | application/json | ✅ |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| nickname | String |  |  |  |

### 응답 (Response)

#### 200 사용자 정보 업데이트 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| code | String |  |
| message | String |  |
| data | Object |  |

#### 응답 예시

```json
{
  "code": "NICKNAME_UPDATED",
  "message": "닉네임이 성공적으로 수정되었습니다.",
  "data": null
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
