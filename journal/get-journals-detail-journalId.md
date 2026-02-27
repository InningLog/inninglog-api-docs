<!-- AUTO-GENERATED -->

## 특정 직관 일지 조회

### 개요

journalId는 직관일지 목록 API(/summary, /schedule)를 통해 확인된 값을 전달해야 합니다. seatViewId는 시야 정보가 연결된 경우에만 포함됩니다.

### 엔드포인트

`GET /journals/detail/{journalId}`

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
| journalId | Long | ✅ | 직관 일지 ID. 목록 API에서 선택한 항목의 ID를 전달 |  |

### 응답 (Response)

#### 200 직관일지 상세 조회 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| journalId | Long | 직관일지 Id |
| gameDate | String | 경기 날짜 |
| supportTeamSC | String | 우리팀 숏코드 |
| opponentTeamSC | String | 상대팀 숏코드 |
| ourScore | Integer | 우리팀 점수 |
| theirScore | Integer | 상대팀 점수 |
| stadiumSC | String | 경기장 숏코드 |
| emotion | String (감동, 짜릿함, 답답함, 아쉬움, 분노, 흡족) | 감정 태그 (감동/짜릿함/답답함/아쉬움/분노 중 하나) |
| media_url | String | 업로드한 이미지 파일명 (확장자 포함) |
| review_text | String | 후기글 |
| commentCount | Long | 댓글 수 |
| likeCount | Long | 좋아요 수 |
| likedByMe | Boolean | 현재 사용자의 좋아요 여부 |
| scrapCount | Long | 스크랩 수 |
| scrapedByMe | Boolean | 현재 사용자의 스크랩 여부 |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "jourDetail": {
      "journalId": 4,
      "gameDate": "2025-06-03 18:30",
      "supportTeamSC": "OB",
      "opponentTeamSC": "OB",
      "ourScore": 2,
      "theirScore": 10,
      "stadiumSC": "JAM",
      "emotion": "감동",
      "media_url": "",
      "review_text": ""
    },
    "seatViewId": null
  }
}
```
