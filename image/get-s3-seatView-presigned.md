<!-- AUTO-GENERATED -->

## 좌석 시야용 Presigned URL 발급

### 개요

좌석 시야 이미지를 업로드하기 위한 Presigned URL을 반환합니다.

### 엔드포인트

`GET /s3/seatView/presigned`

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
| fileName | String | ✅ | 업로드할 파일명 (확장자 포함) | seatview001.png |
| contentType | String | ✅ | 파일 MIME 타입 | image/png |

### 응답 (Response)

#### 200 Presigned URL 발급 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| code | String |  |
| message | String |  |
| data | Object |  |

#### 응답 예시

```json
{
  "code": "OK",
  "message": "요청이 성공적으로 처리되었습니다.",
  "data": "https://inninglog.s3.ap-northeast-2.amazonaws.com/seatView/1/seatview001.png?X-Amz-Algorithm=..."
}
```
