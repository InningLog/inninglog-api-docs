<!-- AUTO-GENERATED -->

## 게시글 수정

### 개요

게시글의 제목·내용 수정뿐 아니라 **기존 이미지 유지/삭제/순서 변경**,
**새로운 이미지 추가**까지 모두 처리하는 API입니다.

### 🔧 요청 규칙

#### 1) 기존 이미지 수정 (`remainImages`)
- 기존 ContentImage의 `id` 와 수정된 `sequence`즉 순서를 전달합니다.
- 전달된 이미지들만 유지되며, 전달되지 않은 기존 이미지는 삭제됩니다.

#### 2) 신규 이미지 추가 (`newImages`)
- S3 Presigned URL을 통해 업로드된 후의 이미지 key와,
  최종 반영할 `sequence` 를 전달합니다.

#### 3) sequence 정책
- **프론트에서 보내준 sequence 값이 최종 순서입니다.**
- 백엔드는 별도의 재정렬을 하지 않고, 전달받은 순서 그대로 저장합니다.

---
### 📌 예시 요청
```json
{
  "title": "수정된 제목",
  "content": "변경된 내용입니다.",
  "remainImages": [
    { "remainImageId": 12, "sequence": 1 },
    { "remainImageId": 14, "sequence": 3 }
  ],
  "newImages": [
    { "sequence": 2, "key": "post/1/new-image.jpeg" }
  ]
}
```

### 엔드포인트

`PATCH /community/posts/{postId}`

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
| postId | Long | ✅ | 수정할 게시글 ID | 123 |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| title | String |  | 게시글 제목 | 오늘 직관 후기 수정합니다 |
| content | String |  | 게시글 본문 내용 | 경기 내용이 너무 좋아서 내용 수정했어요! |
| remainImages | Object[] |  | 기존 이미지 중 유지할 이미지 목록 (삭제되지 않는 이미지) | [object Object],[object Object] |
| remainImages[].remainImageId | Long |  | 기존 이미지 Id | 1 |
| remainImages[].sequence | Integer |  | 수정 후 이미지 업로드 순서 | 2 |
| newImages | Object[] |  | 새로 추가된 이미지 정보 목록 | [object Object],[object Object] |
| newImages[].sequence | Integer |  | 이미지 업로드 순서 | 2 |
| newImages[].key | String |  | 이미지 경로 키 | post/1/cat.jpeg |
| imageCount | Long |  | 게시글에 포함된 전체 이미지 개수 (기존 + 신규) | 4 |

### 응답 (Response)

#### 200 게시글 수정 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 401 | 인증 실패 |
| 403 | 작성자만 수정 가능 |
| 404 | 게시글을 찾을 수 없음 |
