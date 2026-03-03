<!-- AUTO-GENERATED -->

## 회원 초기 설정 (닉네임 + 응원팀)

### 개요

회원 가입 후 최초 1회에 한해 닉네임과 응원팀을 한 번에 설정합니다.

⚠️ 응원팀은 한 번 설정하면 변경할 수 없습니다.

### 엔드포인트

`POST /member/setup`

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
| nickname | String |  | 설정할 닉네임 | 야구천재 |
| teamShortCode | String |  | 응원팀 shortCode | LG |

### 응답 (Response)

#### 200 회원 정보 설정 완료

| 필드명 | 타입 | 설명 |
|--------|------|------|
| code | String |  |
| message | String |  |
| data | Object |  |

#### 응답 예시

```json
{
  "code": "MEMBER_SETUP_SUCCESS",
  "message": "회원 정보 설정이 완료되었습니다.",
  "data": null
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 409 | 이미 팀이 설정됨 |
| 500 | 서버 내부 오류 |
