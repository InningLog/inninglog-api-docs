## 일반 좌석 검색

### 개요

구장, 존, 구역, 열 조건으로 좌석시야를 검색합니다. Page 방식 페이지네이션을 사용합니다.

### 엔드포인트

`GET /seatViews/normal/gallery`

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
| `Authorization` | String | `Bearer {JWT_TOKEN}` | |

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `stadiumShortCode` | String | 경기장 숏코드 (예: `JAM`) | |
| `zoneShortCode` | String | 존 숏코드 (예: `JAM_BLUE`) | |
| `section` | String | 구역 (예: `101`) | |
| `seatRow` | String | 열 (예: `3`) | |
| `page` | int | 페이지 번호 (0부터 시작) | |
| `size` | int | 한 페이지 아이템 수 | |

> **검색 규칙:**
> - `stadiumShortCode`는 필수입니다.
> - `seatRow`만 단독으로 검색할 수 없습니다. 최소한 `zoneShortCode` 또는 `section`이 함께 필요합니다.

### 요청 예시

```
GET /seatViews/normal/gallery?stadiumShortCode=JAM&zoneShortCode=JAM_BLUE&page=0&size=10
GET /seatViews/normal/gallery?stadiumShortCode=JAM&zoneShortCode=JAM_BLUE&section=101&seatRow=3
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 좌석 검색 성공 |

**Body (SimplePageResponse)**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.content[]` | Array | 좌석시야 상세 목록 |
| `data.content[].seatViewId` | Long | 좌석시야 ID |
| `data.content[].viewMediaUrl` | String | 시야 이미지 URL |
| `data.content[].seatInfo.zoneName` | String | 존 이름 |
| `data.content[].seatInfo.zoneShortCode` | String | 존 숏코드 |
| `data.content[].seatInfo.section` | String | 좌석 구역 |
| `data.content[].seatInfo.seatRow` | String | 좌석 열 |
| `data.content[].seatInfo.stadiumName` | String | 경기장 이름 |
| `data.content[].emotionTags[]` | Array | 감정 태그 목록 |
| `data.pageNumber` | int | 현재 페이지 |
| `data.pageSize` | int | 페이지 크기 |
| `data.isLast` | boolean | 마지막 페이지 여부 |
| `data.totalElements` | long | 총 요소 수 |
| `data.totalPages` | int | 총 페이지 수 |

### 응답 예시

```json
{
  "code": "SEATVIEW_LIST_FETCHED",
  "message": "시야 사진 조회 성공",
  "data": {
    "content": [
      {
        "seatViewId": 15,
        "viewMediaUrl": "https://s3.amazonaws.com/...",
        "seatInfo": {
          "zoneName": "블루존",
          "zoneShortCode": "JAM_BLUE",
          "section": "101구역",
          "seatRow": "3열",
          "stadiumName": "잠실야구장"
        },
        "emotionTags": [
          { "code": "CHEERING_MOSTLY_STANDING", "label": "응원 대부분 서서" }
        ]
      }
    ],
    "pageNumber": 0,
    "pageSize": 10,
    "isLast": true,
    "totalElements": 1,
    "totalPages": 1
  }
}
```

### 결과 없음 응답 예시

```json
{
  "code": "SEATVIEW_EMPTY",
  "message": "해당 조건에 해당하는 시야 사진이 없습니다.",
  "data": {
    "content": [],
    "pageNumber": 0,
    "pageSize": 10,
    "isLast": true,
    "totalElements": 0,
    "totalPages": 0
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `400 Bad Request` | 존 정보 없이 열만으로는 검색 불가 | `INVALID_SEAT_SEARCH` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
