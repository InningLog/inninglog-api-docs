<!-- AUTO-GENERATED -->

## 본인 직관 일지 목록 페이지 - 모아보기

### 개요

로그인한 유저의 직관 일지를 목록 형식으로 조회합니다.

📌 *무한 스크롤 방식 지원*
🔍 *`resultScore` 파라미터를 통해 경기 결과(WIN, LOSE, DRAW)로 필터링 가능*
🧭 *`page`, `size` 파라미터로 페이지네이션 처리 (기본: 1페이지당 10개)*

✅ 예시 요청:
- 전체 조회: `/journals/summary?page=0&size=10`
- 승리 경기만: `/journals/summary?page=1&size=10&resultScore=WIN`

### 엔드포인트

`GET /journals/summary`

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
| resultScore | String (WIN, DRAW, LOSE) |  | 경기 결과 필터 (WIN, LOSE, DRAW) | WIN |
| page | Integer |  | 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 페이지 크기 (한 페이지당 항목 수) | 10 |

### 응답 (Response)

#### 200 일지 조회 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| journalId | Long | 일지 고유 ID |
| media_url | String | 일지에 첨부된 미디어 파일 S3 URL |
| resultScore | String (WIN, DRAW, LOSE) | 경기 결과 (WIN, LOSE, DRAW) |
| emotion | String (감동, 짜릿함, 답답함, 아쉬움, 분노, 흡족) | 기록 시 감정 태그 (감동, 짜릿함, ...) |
| gameDate | String | 경기 날짜 및 시간 |
| supportTeamSC | String | 우리팀 숏코드 |
| opponentTeamSC | String | 경기 상대 팀 숏코드 |
| stadiumSC | String | 경기장 숏코드 |
| likeCount | Long | 좋아요 수 |
| commentCount | Long | 댓글 수 |
| scrapCount | Long | 스크랩 수 |
| likedByMe | Boolean | 내가 좋아요 눌렀는지 여부 |
| scrapedByMe | Boolean | 내가 스크랩했는지 여부 |

#### 응답 예시

```json
{
  "code": "JOURNAL_LIST_FETCHED",
  "message": "직관 일지 리스트 조회 성공",
  "data": {
    "content": [
      {
        "journalId": 7,
        "media_url": "https://inninglog-bucket.s3.ap-northeast-2.amazonaws.com/journal/1/photo123.jpeg?X-Amz-Expires=600&X-Amz-Signature=...",
        "resultScore": "승",
        "emotion": "감동",
        "gameDate": "2025-06-03 18:30",
        "supportTeamSC": "OB",
        "opponentTeamSC": "SS",
        "stadiumSC": "JAM",
        "likeCount": 15,
        "commentCount": 8,
        "scrapCount": 3,
        "likedByMe": true,
        "scrapedByMe": false
      }
    ],
    "pageNumber": 0,
    "pageSize": 10,
    "totalElements": 6,
    "totalPages": 1,
    "last": true
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
