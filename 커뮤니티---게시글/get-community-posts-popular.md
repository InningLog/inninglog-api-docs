<!-- AUTO-GENERATED -->

## 인기 게시글 목록 조회

### 개요

좋아요가 10개 이상인 인기 게시글 목록을 조회합니다.

✔ 최신순(postAt DESC)으로 정렬되어 반환됩니다.
✔ page는 0부터 시작합니다. (0=첫 페이지)
✔ size는 한 페이지에서 가져올 게시글 수를 의미합니다.
✔ hasNext가 true이면 다음 페이지 요청이 가능합니다.

### 엔드포인트

`GET /community/posts/popular`

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

#### 200 인기 게시글 목록 조회 성공

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
        "postId": 45,
        "teamShortCode": "LG",
        "title": "오늘 경기 역전승 후기",
        "content": "9회말 역전 투런홈런! 잠실이 터졌어요!",
        "member": {
          "nickName": "볼빨간스트라스버그",
          "profile_url": "https://k.kakaocdn.net/.../img.jpg"
        },
        "likeCount": 24,
        "scrapCount": 5,
        "commentCount": 18,
        "thumbImageUrl": "https://s3.amazonaws.com/.../thumb.jpg",
        "imageCount": 3,
        "postAt": "2025-06-03 18:30"
      }
    ],
    "hasNext": true,
    "page": 0,
    "size": 10
  }
}
```
