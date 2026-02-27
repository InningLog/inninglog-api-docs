<!-- AUTO-GENERATED -->

## 좌석 시야 생성

### 개요

JWT 토큰에서 유저 정보를 추출하고, S3에 이미지 업로드 후 좌석 시야를 생성합니다.
        좌석 시야 작성 요청 JSON 예시입니다. S3에 이미지를 업로드한 후,
    업로드된 파일명을 'fileName' 필드에 포함하여 요청해야 합니다.

    ✅ 필수 입력 필드:
    - `journalId`: 연결된 직관 일지 ID
    - `stadiumShortCode`, `zoneShortCode`, `section`, `seatRow`: 좌석 정보
    - `emotionTagCodes`: 감정 태그 코드 배열 (문자열 리스트)
    - `fileName`: 업로드한 이미지 파일명 (확장자 포함)

    📌 Presigned URL을 통해 업로드된 파일명만 저장하며, 실제 S3 경로는 서버에서 조립됩니다.

### 엔드포인트

`POST /seatViews/contents`

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
| journalId | Long |  | 매핑되는 직관 일지의 ID | 12 |
| stadiumShortCode | String |  | 경기장 숏코드 (ex. JAMS, DAE) | JAM |
| zoneShortCode | String |  | 존 숏코드 (ex. JAM_BLUE ) | JAM_BLUE |
| section | String |  | 좌석의 구역 정보 | 101 |
| seatRow | String |  | 좌석의 열(Row) 정보 | 3 |
| emotionTagCodes | String[] |  | 감정 태그 코드 리스트 | CHEERING_MOSTLY_STANDING,SUN_NONE |
| fileName | String |  | 업로드할 이미지 파일명 (확장자 포함) | photo123.jpeg |

### 응답 (Response)

#### 201 좌석 시야 생성 성공

| 필드명 | 타입 | 설명 |
|--------|------|------|
| code | String |  |
| message | String |  |
| data | Object |  |

#### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "seatViewId": 12,
    "journalId": 7
  }
}
```

### 실패 (Error)

| 코드 | 설명 |
|------|------|
| 400 | 잘못된 요청 |
| 404 | 리소스를 찾을 수 없음 |
| 500 | 서버 내부 오류 |
