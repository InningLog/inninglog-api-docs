<!-- AUTO-GENERATED -->

## 선수 기록 저장

### 개요

Python 크롤러에서 수집한 선수들의 투타 기록을 데이터베이스에 저장합니다.

### 엔드포인트

`POST /api/kbo/player-stats`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |
| Content-Type | application/json | ✅ |

#### Query Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| gameId | String | ✅ | 경기 ID (예: 20250601HHNC0) | 20250601HHNC0 |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| pitchers | Object[] |  | 투수 기록 목록 | [object Object] |
| pitchers[].team | String | ✅ | 소속 팀명 | 한화 |
| pitchers[].playerName | String | ✅ | 선수명 | 홍길동 |
| pitchers[].innings | String | ✅ | 투구 이닝 | 5.2 |
| pitchers[].earnedRuns | Integer | ✅ | 자책점 | 3 |
| hitters | Object[] |  | 타자 기록 목록 | [object Object] |
| hitters[].team | String | ✅ | 소속 팀명 | NC |
| hitters[].playerName | String | ✅ | 선수명 | 김철수 |
| hitters[].atBats | Integer | ✅ | 타수 | 4 |
| hitters[].hits | Integer | ✅ | 안타 | 2 |

### 응답 (Response)

#### 200 선수 기록 저장 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 데이터 |
| 500 | 서버 내부 오류 |
