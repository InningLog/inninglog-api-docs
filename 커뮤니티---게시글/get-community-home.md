<!-- AUTO-GENERATED -->

## 커뮤니티 홈 조회

### 개요

커뮤니티 홈 화면에 필요한 데이터를 조회합니다.

- 내 응원팀 숏 코드
- 인기 게시글 최신 2개 (좋아요 10개 이상)
  - 작성자 정보 제외
  - 내가 좋아요 누른 여부 (likedByMe)
  - 내가 스크랩한 여부 (scrapedByMe)

### 엔드포인트

`GET /community/home`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

### 응답 (Response)

#### 200 커뮤니티 홈 조회 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| supportTeamShortCode | String | 내 응원팀 숏 코드 |
| popularPosts | Object[] | 인기 게시글 목록 (최신 2개) |
| popularPosts[].postId | Long | 게시글 ID |
| popularPosts[].teamShortCode | String | 팀 숏 코드 (어느 팀 게시판인지) |
| popularPosts[].title | String | 게시글 제목 |
| popularPosts[].content | String | 게시글 본문 |
| popularPosts[].likeCount | Long | 좋아요 수 |
| popularPosts[].scrapCount | Long | 스크랩 수 |
| popularPosts[].commentCount | Long | 댓글 수 |
| popularPosts[].thumbImageUrl | String | 대표 이미지 URL (없으면 null) |
| popularPosts[].imageCount | Long | 게시글에 포함된 전체 이미지 개수 |
| popularPosts[].postAt | String | 작성일 |
| popularPosts[].likedByMe | Boolean | 내가 좋아요 눌렀는지 |
| popularPosts[].scrapedByMe | Boolean | 내가 스크랩 했는지 |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "supportTeamShortCode": "LG",
    "popularPosts": [
      {
        "postId": 45,
        "teamShortCode": "LG",
        "title": "역전승 후기",
        "content": "9회말 투런홈런!",
        "likeCount": 24,
        "scrapCount": 5,
        "commentCount": 18,
        "thumbImageUrl": "https://s3.amazonaws.com/.../thumb.jpg",
        "imageCount": 3,
        "postAt": "2025-06-03 18:30",
        "likedByMe": true,
        "scrapedByMe": false
      }
    ]
  }
}
```
