## 좌석시야 상세 조회

### 개요

특정 좌석시야의 상세 정보를 조회합니다.

### 엔드포인트

`GET /seatViews/{seatViewId}`

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

### Path Parameters

| Key | Type | 설명 |
| --- | --- | --- |
| `seatViewId` | Long | 조회할 좌석시야 ID |

### 요청 예시

```
GET /seatViews/15
```

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 좌석시야 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.seatViewId` | Long | 좌석시야 ID |
| `data.viewMediaUrl` | String | 시야 이미지 URL (Presigned) |
| `data.seatInfo.zoneName` | String | 존 이름 (예: `익사이팅존`) |
| `data.seatInfo.zoneShortCode` | String | 존 숏코드 (예: `JAM_RED`) |
| `data.seatInfo.section` | String | 좌석 구역 (예: `13구역`) |
| `data.seatInfo.seatRow` | String | 좌석 열 (예: `3열`) |
| `data.seatInfo.stadiumName` | String | 경기장 이름 |
| `data.emotionTags[]` | Array | 감정 태그 목록 |
| `data.emotionTags[].code` | String | 태그 코드 |
| `data.emotionTags[].label` | String | 태그 라벨 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "seatViewId": 15,
    "viewMediaUrl": "https://s3.amazonaws.com/...",
    "seatInfo": {
      "zoneName": "익사이팅존",
      "zoneShortCode": "JAM_RED",
      "section": "13구역",
      "seatRow": "3열",
      "stadiumName": "잠실야구장"
    },
    "emotionTags": [
      {
        "code": "CHEERING_MOSTLY_STANDING",
        "label": "응원 대부분 서서"
      },
      {
        "code": "SUN_NONE",
        "label": "햇빛 없음"
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
| `404 Not Found` | 작성하지 않은 좌석시야 | `SEATVIEW_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
