<!-- AUTO-GENERATED -->

## 내가 스크랩한 글 목록 조회

### 개요

내가 스크랩한 게시글 목록을 조회합니다.

✔ 최근 스크랩한 순으로 정렬되어 반환됩니다.
✔ page는 0부터 시작합니다. (0=첫 페이지)
✔ size는 한 페이지에서 가져올 게시글 수를 의미합니다.
✔ hasNext가 true이면 다음 페이지 요청이 가능합니다.

### 엔드포인트

`GET /community/posts/my/scrapped`

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
| page | Integer |  | 조회할 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 한 페이지당 게시글 개수 | 10 |

### 응답 (Response)

#### 200 내가 스크랩한 글 목록 조회 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| content | Object[] | 조회된 데이터 목록 |
| hasNext | Boolean | 다음 페이지가 존재하는지 여부 |
| page | Integer | 현재 페이지 번호 |
| size | Integer | 페이지 크기 |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "content": [
      {
        "postId": 58,
        "teamShortCode": "LG",
        "title": "잠실 좌석 추천",
        "content": "1루 응원석 뷰가 정말 좋아요!",
        "member": {
          "nickName": "야구덕후",
          "profile_url": "https://k.kakaocdn.net/.../img.jpg"
        },
        "likeCount": 28,
        "scrapCount": 12,
        "commentCount": 7,
        "thumbImageUrl": "https://s3.amazonaws.com/.../view.jpg",
        "imageCount": 5,
        "postAt": "2025-06-01 14:00",
        "likedByMe": true,
        "scrapedByMe": true
      }
    ],
    "hasNext": true,
    "page": 0,
    "size": 10
  }
}
```
