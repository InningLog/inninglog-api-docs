<!-- AUTO-GENERATED -->

## 직관 일지 작성 페이지 - 직관 일지 콘텐츠 업로드

### 개요

직관 일지 본문 데이터를 업로드하는 API입니다.

사용자는 사전에 Presigned URL 발급 API(`/s3/journal/presigned`)를 통해
S3에 이미지를 직접 업로드한 뒤, 업로드 경로에 해당하는 `fileName`을 포함하여
본 API를 호출해야 합니다.

이 API는 전달받은 정보를 바탕으로 새로운 Journal 객체를 생성합니다.

✅ 필수 필드:
- `gameId`: 경기 고유 ID (예: 20250622OBLG0)
- `fileName`: 업로드한 이미지 파일명 (확장자 포함, ex. photo123.jpeg)
- `ourScore`, `theirScore`: 점수 정보
- `opponentTeamShortCode`, `stadiumShortCode`: 상대팀 및 경기장 숏코드
- `gameDateTime`: 경기 일시 (`yyyy-MM-dd HH:mm` 형식)
- `emotion`: 감정 태그 (감동, 짜릿함, 답답함, 아쉬움, 분노, 흡족 중 하나)
- `review_text`: 후기 내용

### 엔드포인트

`POST /journals/contents`

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
| gameId | String |  | 게임 Id | 20250622OBLG0 |
| gameDate | String |  | 경기 날짜 (LocalDateTime 형식) | 2025-06-03 18:30 |
| stadiumSC | String |  | 경기장 숏코드 | JAM |
| opponentTeamSC | String |  | 상대팀 숏코드 | OB |
| ourScore | Integer |  | 우리팀 점수 | 3 |
| theirScore | Integer |  | 상대팀 점수 | 1 |
| fileName | String |  | 업로드할 이미지 파일명 (확장자 포함) | photo123.jpeg |
| emotion | String (감동, 짜릿함, 답답함, 아쉬움, 분노, 흡족) |  | 감정 태그 (감동/짜릿함/답답함/아쉬움/분노 중 하나) | 감동 |
| review_text | String |  | 후기글 작성 | 오늘 경기는 정말 재미있었다! |
| public | Boolean |  |  |  |

### 응답 (Response)

#### 201 일지 생성 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| journalId | Long | 직관 일지 Id |

#### 응답 예시

```json
{
  "code": "JOURNAL_CREATED",
  "message": "직관 일지가 등록되었습니다.",
  "data": {
    "journalId": 123
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
