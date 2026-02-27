<!-- AUTO-GENERATED -->

## 공개 직관 일지 피드 조회

### 개요

공개 설정된 직관 일지를 조회합니다. 인증이 필요합니다.

📌 **팀 필터링**
- `teamShortCode=ALL`: 전체 공개 일지 조회
- `teamShortCode=LG`: 특정 팀(작성자 응원팀 기준) 일지만 조회

📌 **페이지네이션**
- 무한 스크롤 방식 (Slice 기반)
- `page`, `size` 파라미터로 제어
- 최신순(createdAt DESC)으로 정렬

📌 **응답 필드**
- `writedByMe`: 내가 작성한 일지인지 여부
- `likedByMe`: 내가 좋아요 눌렀는지 여부
- `scrapedByMe`: 내가 스크랩했는지 여부

✅ 예시 요청:
- 전체 조회: `/journals/feed?teamShortCode=ALL&page=0&size=10`
- LG팬 일지만: `/journals/feed?teamShortCode=LG&page=0&size=10`

### 엔드포인트

`GET /journals/feed`

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
| teamShortCode | String | ✅ | 팀 숏코드 (ALL: 전체 조회, 특정 팀코드: 해당 팀 응원 사용자 일지만) | ALL |
| page | Integer |  | 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 페이지 크기 | 10 |

### 응답 (Response)

#### 200 피드 조회 성공

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
        "journalId": 123,
        "thumbnailUrl": "https://s3.amazonaws.com/.../image.jpg",
        "member": {
          "nickName": "볼빨간스트라스버그",
          "profile_url": "https://k.kakaocdn.net/.../img.jpg"
        },
        "writedByMe": false,
        "reviewPreview": "오늘 경기 정말 재밌었다! 우리 팀이 역전승...",
        "createdAt": "2025-06-03 18:30",
        "likeCount": 15,
        "likedByMe": true,
        "commentCount": 3,
        "scrapCount": 2,
        "scrapedByMe": false
      }
    ],
    "hasNext": true,
    "page": 0,
    "size": 10
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
