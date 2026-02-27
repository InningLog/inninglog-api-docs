<!-- AUTO-GENERATED -->

## 회원의 응원 팀 설정

### 개요

로그인한 회원의 응원 팀을 설정합니다.
요청 시 아래의 **구단 식별자(shortCode)** 중 하나를 전달해야 합니다.

- LG 트윈스: `LG`
- 두산 베어스: `OB`
- SSG 랜더스: `SK`
- 한화 이글스: `HH`
- 삼성 라이온즈: `SS`
- KT 위즈: `KT`
- 롯데 자이언츠: `LT`
- KIA 타이거즈: `HT`
- NC 다이노스: `NC`
- 키움 히어로즈: `WO`

⚠️ **주의:** 이미 응원 팀이 설정된 회원은 변경할 수 없습니다.
이 경우 `400 Bad Request` 에러가 반환됩니다.

### 엔드포인트

`PATCH /member/setup`

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
| teamShortCode | String |  | 응원 팀의 식별자 shortCode (예: DOOSAN, KIA, SSG 등) | OB |

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
  "code": "TEAM_SET",
  "message": "응원 팀이 성공적으로 설정되었습니다.",
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
