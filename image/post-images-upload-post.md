<!-- AUTO-GENERATED -->

## 게시글 이미지 Presigned URL 목록 발급

### 개요

게시글 작성 시 S3에 이미지를 업로드하기 위한 Presigned PUT URL 목록을 발급합니다.

1) 프론트는 fileName / contentType / sequence 정보를 보내면
2) 서버는 각 이미지에 대한 Presigned PUT URL + 저장될 S3 Key 를 생성하여 반환합니다.
3) 프론트는 받은 Presigned URL 로 S3에 직접 업로드한 뒤
4) 게시글 생성 API 호출 시 해당 key 목록을 포함해 전송해야 합니다.

### 엔드포인트

`POST /images/upload/post`

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
| imageUploadReqDto | Object[] |  | 이미지 리스트 S3 업로드 요청 |  |
| imageUploadReqDto[].sequence | Integer |  | 이미지 업로드 순서 | 2 |
| imageUploadReqDto[].fileName | String |  | 이미지 파일명(확장자 포함) | cat.png |
| imageUploadReqDto[].contentType | String |  | 이미지 파일 MIME 타입 | image/png |

### 응답 (Response)

#### 200 Presigned URL 생성 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 파일명 검증 실패 |
| 401 | 인증 필요 |
