## 게시글 이미지 Presigned URL 발급

### 개요

게시글에 첨부할 이미지의 S3 Presigned URL을 발급받습니다. 클라이언트는 발급받은 Presigned URL로 직접 S3에 이미지를 업로드합니다.

### 엔드포인트

`POST /images/upload/post`

### 인증

- **인증 필요 여부:** JWT 인증 필요

> 요청 헤더(Header)에 아래와 같이 Authorization 필드를 포함해야 합니다.
>
> `Authorization: Bearer {JWT_TOKEN}`

---

### 요청 (Request)

<aside>

### Headers

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `Content-Type` | String | `application/json` | |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | |

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `imageUploadReqDto` | Array | 이미지 업로드 요청 리스트 | |
| `imageUploadReqDto[].sequence` | int | 이미지 순서 | |
| `imageUploadReqDto[].fileName` | String | 이미지 파일명 (확장자 포함) | |
| `imageUploadReqDto[].contentType` | String | MIME 타입 (예: `image/png`) | |

### 요청 예시

```json
{
  "imageUploadReqDto": [
    {
      "sequence": 1,
      "fileName": "game_photo.jpg",
      "contentType": "image/jpeg"
    },
    {
      "sequence": 2,
      "fileName": "scoreboard.png",
      "contentType": "image/png"
    }
  ]
}
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | Presigned URL 발급 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.imageUploadResDtos[]` | Array | 업로드 응답 리스트 |
| `data.imageUploadResDtos[].sequence` | int | 이미지 순서 |
| `data.imageUploadResDtos[].presignedUrl` | String | S3 Presigned URL (이 URL로 PUT 요청하여 업로드) |
| `data.imageUploadResDtos[].key` | String | S3 이미지 경로 키 (게시글 생성 시 사용) |

### 응답 예시

```json
{
  "code": "S3_UPLOAD_SUCCESS",
  "message": "이미지 업로드가 성공적으로 완료되었습니다.",
  "data": {
    "imageUploadResDtos": [
      {
        "sequence": 1,
        "presignedUrl": "https://s3.amazonaws.com/bucket/post/1/game_photo.jpg?X-Amz-...",
        "key": "post/1/game_photo.jpg"
      },
      {
        "sequence": 2,
        "presignedUrl": "https://s3.amazonaws.com/bucket/post/1/scoreboard.png?X-Amz-...",
        "key": "post/1/scoreboard.png"
      }
    ]
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `400 Bad Request` | 파일명에 슬래시 또는 경로문자 포함 | `INVALID_FILE_NAME` |
| `400 Bad Request` | 업로드할 파일이 없음 | `FILE_IS_EMPTY` |
| `500 Internal Server Error` | S3 업로드 중 오류 | `S3_UPLOAD_FAILED` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>

---

### 이미지 업로드 플로우

```
1. POST /images/upload/post → Presigned URL 발급
2. PUT {presignedUrl} → S3에 직접 이미지 업로드 (클라이언트)
3. POST /community/{teamSC}/posts/create → 게시글 생성 시 key 값 전달
```
