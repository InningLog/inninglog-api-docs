<!-- AUTO-GENERATED -->

## 일반 좌석 검색 (게시물 형태)

### 개요

구장, 존, 구역, 열 정보를 통해 좌석 시야 후기를 검색합니다.
모든 조건은 선택사항이지만, 열 정보만으로는 검색할 수 없습니다 (최소 존 정보 필요).

※ 결과는 **최신순으로 정렬**됩니다.

### 엔드포인트

`GET /seatViews/normal/gallery`

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
| stadiumShortCode | String (JAM, GOC, ICN, SUW, DJN, DAE, BUS, GWJ, CHW) | ✅ | 구장 단축코드 | JAM |
| zoneShortCode | String |  | 존 단축코드 (선택사항) | JAM_BLUE |
| section | String |  | 구역 정보 (선택사항) | 13 |
| seatRow | String |  | 열 정보 (선택사항, 단독 사용 불가 - 최소 존 정보 필요) | 3 |
| page | Integer |  | 페이지 번호 (0부터 시작) | 0 |
| size | Integer |  | 페이지 크기 (한 페이지당 항목 수) | 10 |

### 응답 (Response)

#### 200 좌석 시야 검색 완료

| 필드명 | 타입 | 설명 |
|--------|------|------|
| searchSummary | String | 검색 조건 요약 문구 |
| seatViews | Object[] | 검색 조건에 해당하는 좌석 정보 리스트 |
| seatViews[].seatViewId | Long | 좌석 시야 정보의 고유 ID |
| seatViews[].viewMediaUrl | String | 좌석 시야 이미지 URL |
| seatViews[].seatInfo | Object | 좌석 기본 정보 |
| seatViews[].seatInfo.zoneName | String |  |
| seatViews[].seatInfo.zoneShortCode | String |  |
| seatViews[].seatInfo.section | String |  |
| seatViews[].seatInfo.seatRow | String |  |
| seatViews[].seatInfo.stadiumName | String |  |
| seatViews[].emotionTags | Object[] | 감정 태그 목록 |
| seatViews[].emotionTags[].code | String |  |
| seatViews[].emotionTags[].label | String |  |
| totalCount | Integer | 총 검색 결과 수 |

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
| 400 | 잘못된 요청 (열 정보만 입력한 경우) |
| 500 | 서버 내부 오류 |
