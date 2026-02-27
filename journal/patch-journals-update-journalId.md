<!-- AUTO-GENERATED -->

## 특정 직관 일지 수정

### 개요

기존에 작성된 직관 일지 내용을 수정합니다. 본인만 수정할 수 있으며,
    수정 시 감정 태그, 리뷰, 점수, 이미지 링크 등을 포함할 수 있습니다.
    seatView는 별도 API로 연결되며 본 API에서 수정되지 않습니다.

### 엔드포인트

`PATCH /journals/update/{journalId}`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |
| Content-Type | application/json | ✅ |

#### Path Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| journalId | Long | ✅ |  |  |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| ourScore | Integer |  | 우리팀 점수 | 3 |
| theirScore | Integer |  | 상대팀 점수 | 1 |
| media_url | String |  | 업로드한 이미지 파일명 (확장자 포함) | photo123.jpeg |
| emotion | String (감동, 짜릿함, 답답함, 아쉬움, 분노, 흡족) |  | 감정 태그 (감동/짜릿함/답답함/아쉬움/분노 중 하나) | 감동 |
| review_text | String |  | 후기글 작성 | 오늘 경기는 정말 재미있었다! |
| public | Boolean |  |  |  |

### 응답 (Response)

#### 200 직관일지 수정 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| jourDetail | Object |  |
| jourDetail.journalId | Long | 직관일지 Id |
| jourDetail.gameDate | String | 경기 날짜 |
| jourDetail.supportTeamSC | String | 우리팀 숏코드 |
| jourDetail.opponentTeamSC | String | 상대팀 숏코드 |
| jourDetail.ourScore | Integer | 우리팀 점수 |
| jourDetail.theirScore | Integer | 상대팀 점수 |
| jourDetail.stadiumSC | String | 경기장 숏코드 |
| jourDetail.emotion | String (감동, 짜릿함, 답답함, 아쉬움, 분노, 흡족) | 감정 태그 (감동/짜릿함/답답함/아쉬움/분노 중 하나) |
| jourDetail.media_url | String | 업로드한 이미지 파일명 (확장자 포함) |
| jourDetail.review_text | String | 후기글 |
| jourDetail.commentCount | Long | 댓글 수 |
| jourDetail.likeCount | Long | 좋아요 수 |
| jourDetail.likedByMe | Boolean | 현재 사용자의 좋아요 여부 |
| jourDetail.scrapCount | Long | 스크랩 수 |
| jourDetail.scrapedByMe | Boolean | 현재 사용자의 스크랩 여부 |
| seatViewId | Long |  |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "jourDetail": {
      "journalId": 3,
      "gameDate": "2025-06-03 18:30",
      "supportTeamSC": "OB",
      "opponentTeamSC": "OB",
      "stadiumSC": "JAM",
      "emotion": "감동",
      "media_url": "https://s3.amazonaws.com/.../image.jpg",
      "review_text": "후기를 수정했어요!"
    },
    "seatViewId": 3
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
