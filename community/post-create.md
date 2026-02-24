## 게시글 생성

### 개요

팀별 커뮤니티에 새로운 게시글을 작성합니다. 이미지를 첨부할 수 있습니다.

### 📌 엔드포인트

`POST /community/{teamSC}/posts/create`

### 🔐 인증

- **인증 필요 여부:** JWT 인증 필요

> 요청 헤더(Header)에 아래와 같이 Authorization 필드를 포함해야 합니다.
>
> `Authorization: Bearer {JWT_TOKEN}`

---

### ▶️ 요청 (Request)

<aside>

### Headers

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `Content-Type` | String | `application/json` | ✅ |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | ✅ |

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `teamSC` | String | 게시판 팀 숏코드 (예: `LG`, `OB`) |

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `title` | String | 게시글 제목 | ✅ |
| `content` | String | 게시글 본문 | ✅ |
| `imageCreateReqDto` | Array | 첨부 이미지 리스트 | ⬜️ |
| `imageCreateReqDto[].sequence` | int | 이미지 순서 | ✅ |
| `imageCreateReqDto[].key` | String | 이미지 S3 경로 키 (예: `post/1/cat.jpeg`) | ✅ |
| `imageCount` | Long | 전체 이미지 개수 | ⬜️ |

### ▶️ 요청 예시

```json
{
  "title": "오늘 두산 경기 왜이럼?",
  "content": "아 진짜 화나네 진짜",
  "imageCreateReqDto": [
    {
      "sequence": 1,
      "key": "post/1/game_photo.jpg"
    },
    {
      "sequence": 2,
      "key": "post/1/score_board.png"
    }
  ],
  "imageCount": 2
}
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 게시글 생성 완료 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": null
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 등록되지 않은 팀 | `TEAM_NOT_FOUND` |
| `400 Bad Request` | 요청값이 올바르지 않음 | `VALIDATION_ERROR` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
