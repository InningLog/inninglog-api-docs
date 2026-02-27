<!-- AUTO-GENERATED -->

## 검색어 삭제

### 개요

특정 검색어를 삭제합니다. 본인의 검색어만 삭제 가능합니다.

### 엔드포인트

`DELETE /search/history/{searchHistoryId}`

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
| searchHistoryId | Long | ✅ | 검색 기록 ID | 1 |

### 응답 (Response)

#### 200 검색어 삭제 성공
