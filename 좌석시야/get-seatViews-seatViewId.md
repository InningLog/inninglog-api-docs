<!-- AUTO-GENERATED -->

## 특정 좌석 시야 조회

### 개요

seatViewId에 해당하는 좌석 시야 데이터를 상세 조회합니다.

### 엔드포인트

`GET /seatViews/{seatViewId}`

### 인증

🔒 JWT 인증 필요

### 요청 (Request)

#### Headers

| 헤더 | 값 | 필수 |
|------|------|------|
| Authorization | Bearer {token} | ✅ |

#### Path Parameters

| 파라미터 | 타입 | 필수 | 설명 | 예시 |
|----------|------|------|------|------|
| seatViewId | Long | ✅ | 조회할 SeatView의 ID |  |

### 응답 (Response)

#### 200 조회 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| seatViewId | Long | 좌석 시야 정보의 고유 ID |
| viewMediaUrl | String | 좌석 시야 이미지 URL |
| seatInfo | Object | 좌석 기본 정보 |
| seatInfo.zoneName | String |  |
| seatInfo.zoneShortCode | String |  |
| seatInfo.section | String |  |
| seatInfo.seatRow | String |  |
| seatInfo.stadiumName | String |  |
| emotionTags | Object[] | 감정 태그 목록 |
| emotionTags[].code | String |  |
| emotionTags[].label | String |  |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "seatViewId": 3,
    "viewMediaUrl": "https://your-s3-bucket-url/image.jpg",
    "seatInfo": {
      "zoneName": "블루석",
      "zoneShortCode": "JAM_BLUE",
      "section": "13",
      "seatRow": "3",
      "stadiumName": "잠실"
    },
    "emotionTags": [
      {
        "code": "VIEW_OBSTRUCT_NET",
        "label": "시야 방해 - 그물"
      },
      {
        "code": "SUN_STRONG",
        "label": "햇빛 - 강함"
      }
    ]
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
