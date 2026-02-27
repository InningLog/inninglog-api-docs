<!-- AUTO-GENERATED -->

## 게임별 선수 기록 조회

### 개요

특정 게임의 모든 선수 기록을 조회합니다.

### 엔드포인트

`GET /api/kbo/player-stats/{gameId}`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

#### Path Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| gameId | String | ✅ | 경기 ID | 20250601HHNC0 |

### 응답 (Response)

#### 200 조회 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 404 | 게임을 찾을 수 없음 |
