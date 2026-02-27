<!-- AUTO-GENERATED -->

## 게시글 생성

### 개요

게시글을 생성합니다.

⚾ 이미지 업로드 흐름:
1) 먼저 Presigned URL 발급 API로 S3 업로드용 URL을 발급받고
2) 프론트는 해당 Presigned URL로 S3에 직접 업로드한 뒤
3) 아래 createPost API 호출 시 업로드된 이미지들의 s3Key(sequence 포함)를 함께 전달해야 합니다.

### 엔드포인트

`POST /community/{teamSC}/posts/create`

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
| teamSC | String | ✅ | 팀 숏 코드 (ex: LG) | LG |

#### Body

| 필드명 | 타입 | 필수 | 설명 | 예시 |
|--------|------|------|------|------|
| title | String |  | 게시글 제목 | 오늘 두산 경기 왜이럼? |
| content | String |  | 게시글 본문 | 아 진짜 화나네 진짜 |
| imageCreateReqDto | Object[] |  | 첨부 이미지 리스트 |  |
| imageCreateReqDto[].sequence | Integer |  | 이미지 업로드 순서 | 2 |
| imageCreateReqDto[].key | String |  | 이미지 경로 키 | post/1/cat.jpeg |
| imageCount | Long |  | 게시글에 포함된 전체 이미지 개수 | 3 |

### 응답 (Response)

#### 200 게시글 생성 성공

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 요청 값 오류 |
| 401 | 인증 필요 |
