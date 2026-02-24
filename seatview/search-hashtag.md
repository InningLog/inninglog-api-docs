## 해시태그 기반 좌석 검색

### 개요

감정 태그(해시태그)를 기반으로 좌석시야를 검색합니다. 최소 1개, 최대 2개의 해시태그로 검색 가능하며, AND/OR 조건을 선택할 수 있습니다. Page 방식 페이지네이션을 사용합니다.

### 📌 엔드포인트

`GET /seatViews/hashtag/gallery`

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
| `Authorization` | String | `Bearer {JWT_TOKEN}` | ✅ |

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `stadiumShortCode` | String | 경기장 숏코드 (예: `JAM`) | ⬜️ |
| `hashtagCodes` | List\<String\> | 해시태그 코드 (최소 1개, 최대 2개) | ✅ |
| `isAndCondition` | Boolean | AND 조건 여부 (`true`: AND, `false`: OR, 기본값: `false`) | ⬜️ |
| `page` | int | 페이지 번호 (0부터 시작) | ⬜️ |
| `size` | int | 한 페이지 아이템 수 | ⬜️ |

### ▶️ 요청 예시

```
GET /seatViews/hashtag/gallery?hashtagCodes=CHEERING_MOSTLY_STANDING&hashtagCodes=SUN_NONE&isAndCondition=true&page=0&size=10
GET /seatViews/hashtag/gallery?stadiumShortCode=JAM&hashtagCodes=CHEERING_MOSTLY_STANDING
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 해시태그 검색 성공 |

**Body (SimplePageResponse)**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.content[]` | Array | 좌석시야 이미지 목록 |
| `data.content[].seatViewId` | Long | 좌석시야 ID |
| `data.content[].viewMediaUrl` | String | 시야 이미지 URL |
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
        "viewMediaUrl": "https://s3.amazonaws.com/..."
      },
      {
        "seatViewId": 22,
        "viewMediaUrl": "https://s3.amazonaws.com/..."
      }
    ],
    "pageNumber": 0,
    "pageSize": 10,
    "isLast": true,
    "totalElements": 2,
    "totalPages": 1
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `400 Bad Request` | 해시태그는 최소 1개, 최대 2개 | `INVALID_HASHTAG_REQUEST` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
