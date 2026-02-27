<!-- AUTO-GENERATED -->

## 해시태그 기반 좌석 검색 (모아보기)

### 개요

선택한 감정 태그를 기준으로 좌석 시야 후기를 검색합니다.
최대 **5개까지 태그 선택**이 가능하며, **선택한 모든 태그를 포함한 좌석만 조회**됩니다.
해당 API는 **모아보기(사진만 제공)** 형태로 결과를 반환합니다.

※ 결과는 **최신순으로 정렬**됩니다.

### 엔드포인트

`GET /seatViews/hashtag/gallery`

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
| stadiumShortCode | String | ✅ | 구장 단축코드 | JAM |
| hashtagCodes | String[] | ✅ | 해시태그 코드 목록 (최대 5개 선택 가능) |  |
| page | Integer |  | 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 페이지 크기 (한 페이지당 항목 수) | 10 |

### 응답 (Response)

#### 200 해시태그 검색 완료

#### 응답 예시

```json
{
  "code": "SEATVIEW_LIST_FETCHED",
  "message": "시야 사진 조회 성공",
  "data": {
    "content": [
      {
        "seatViewId": 3,
        "viewMediaUrl": "https://your-s3-bucket-url/image.jpg"
      }
    ],
    "pageNumber": 0,
    "pageSize": 10,
    "totalElements": 3,
    "totalPages": 1,
    "last": false
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
