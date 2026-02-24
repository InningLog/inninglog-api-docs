## 좌석시야 생성

### 개요

직관일지에 연결된 좌석시야 후기를 작성합니다. 좌석 위치 정보와 감정 태그, 시야 사진을 포함합니다. 하나의 직관일지에는 하나의 좌석시야만 작성 가능합니다.

### 엔드포인트

`POST /seatViews/contents`

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
| `journalId` | Long | 매핑할 직관일지 ID | |
| `stadiumShortCode` | String | 경기장 숏코드 (예: `JAM`) | |
| `zoneShortCode` | String | 존 숏코드 (예: `JAM_BLUE`) | |
| `section` | String | 좌석 구역 (예: `101`) | |
| `seatRow` | String | 좌석 열 (예: `3`) | |
| `emotionTagCodes` | Array\<String\> | 감정 태그 코드 리스트 | |
| `fileName` | String | 업로드할 시야 이미지 파일명 (확장자 포함) | |

### 요청 예시

```json
{
  "journalId": 42,
  "stadiumShortCode": "JAM",
  "zoneShortCode": "JAM_BLUE",
  "section": "101",
  "seatRow": "3",
  "emotionTagCodes": ["CHEERING_MOSTLY_STANDING", "SUN_NONE"],
  "fileName": "seat_view.jpg"
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
| `200 OK` | 좌석시야 생성 완료 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `data.seatViewId` | Long | 생성된 좌석시야 ID |
| `data.journalId` | Long | 연관된 직관일지 ID |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "seatViewId": 15,
    "journalId": 42
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 작성하지 않은 일지 | `JOURNAL_NOT_FOUND` |
| `404 Not Found` | 등록되지 않은 존 | `ZONE_NOT_FOUND` |
| `404 Not Found` | 등록되지 않은 경기장 | `STADIUM_NOT_FOUND` |
| `400 Bad Request` | 이미 좌석시야가 작성된 일지 | `SEATVIEW_ALREADY_EXISTS` |
| `400 Bad Request` | 파일명 형식 오류 | `INVALID_FILE_NAME` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
