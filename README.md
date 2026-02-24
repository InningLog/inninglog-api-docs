# InningLog API Documentation

## 프로젝트 소개

**InningLog**는 야구 팬을 위한 직관 리포트 플랫폼입니다.\
경기 관람 경험을 감정, 좌석 후기, 개인 통계와 함께 기록하고 공유할 수 있습니다.

---

## Base URL

| 환경 | URL |
| --- | --- |
| 운영 | `https://api.inninglog.com` |
| 로컬 | `http://localhost:8080` |

---

## 인증 방식

InningLog API는 **JWT(JSON Web Token)** 기반 인증을 사용합니다.\
카카오 OAuth 로그인을 통해 발급받은 토큰을 요청 헤더에 포함해야 합니다.

```
Authorization: Bearer {JWT_TOKEN}
```

> 일부 공개 API(로그인, KBO 데이터 등)를 제외한 **모든 API는 JWT 인증이 필수**입니다.

---

## 공통 응답 형식

### 성공 응답 (SuccessResponse)

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": { ... }
}
```

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 (예: `SUCCESS`, `LOGIN_SUCCESS`, `JOURNAL_CREATED`) |
| `message` | String | 성공 메시지 |
| `data` | Object | 응답 데이터 (없을 경우 `null`) |

### 주요 성공 코드

| Code | HTTP Status | Message |
| --- | --- | --- |
| `SUCCESS` | 200 OK | 요청이 정상적으로 처리되었습니다. |
| `LOGIN_SUCCESS` | 200 OK | 로그인이 성공적으로 되었습니다. |
| `NICKNAME_UPDATED` | 200 OK | 닉네임이 성공적으로 수정되었습니다. |
| `TEAM_SET` | 200 OK | 응원 팀이 성공적으로 설정되었습니다. |
| `NO_SCHEDULE_ON_DATE` | 200 OK | 해당 날짜에 예정된 경기가 없습니다. |
| `S3_UPLOAD_SUCCESS` | 200 OK | 이미지 업로드가 성공적으로 완료되었습니다. |
| `JOURNAL_CREATED` | 201 Created | 직관 일지가 등록되었습니다. |
| `REPORT_GENERATED` | 200 OK | 리포트가 생성되었습니다. |

---

### 에러 응답 (ErrorResponse)

```json
{
  "code": "USER_NOT_FOUND",
  "message": "존재하지 않는 회원입니다."
}
```

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 에러 코드 |
| `message` | String | 에러 메시지 |

> 전체 에러 코드는 [에러 코드 목록](error/README.md)을 참고하세요.

---

## 페이지네이션

### Page 방식 (SimplePageResponse)

총 개수가 필요한 목록 조회에 사용됩니다.

```json
{
  "content": [ ... ],
  "pageNumber": 0,
  "pageSize": 10,
  "isLast": false,
  "totalElements": 48,
  "totalPages": 5
}
```

| Key | Type | 설명 |
| --- | --- | --- |
| `content` | Array | 페이지 데이터 |
| `pageNumber` | int | 현재 페이지 번호 (0부터 시작) |
| `pageSize` | int | 페이지 크기 |
| `isLast` | boolean | 마지막 페이지 여부 |
| `totalElements` | long | 총 요소 수 |
| `totalPages` | int | 총 페이지 수 |

### Slice 방식 (SliceResponse)

무한 스크롤에 사용됩니다. 다음 페이지 존재 여부만 제공합니다.

```json
{
  "content": [ ... ],
  "currentPage": 0,
  "size": 10,
  "hasNext": true,
  "hasPrevious": false
}
```

| Key | Type | 설명 |
| --- | --- | --- |
| `content` | Array | 페이지 데이터 |
| `currentPage` | int | 현재 페이지 번호 |
| `size` | int | 페이지 크기 |
| `hasNext` | boolean | 다음 페이지 존재 여부 |
| `hasPrevious` | boolean | 이전 페이지 존재 여부 |

---

## 공통 Query Parameters (페이지네이션)

| Key | Type | 설명 | 기본값 |
| --- | --- | --- | --- |
| `page` | int | 페이지 번호 (0부터 시작) | `0` |
| `size` | int | 한 페이지에 보여줄 아이템 개수 | `10` |

---

## 주요 데이터 타입

### ResultScore (경기 결과)

| 값 | 설명 |
| --- | --- |
| `WIN` | 승리 |
| `LOSE` | 패배 |
| `DRAW` | 무승부 |

### EmotionTag (감정 태그)

| 값 | 설명 |
| --- | --- |
| `MOVED` | 감동 |
| `THRILLED` | 짜릿함 |
| `FRUSTRATED` | 답답함 |
| `REGRETFUL` | 아쉬움 |
| `ANGRY` | 분노 |

### 팀 숏코드 (Team Short Code)

| 숏코드 | 팀명 |
| --- | --- |
| `OB` | 두산 베어스 |
| `LG` | LG 트윈스 |
| `SS` | 삼성 라이온즈 |
| `HH` | 한화 이글스 |
| `HT` | KIA 타이거즈 |
| `SK` | SSG 랜더스 |
| `LT` | 롯데 자이언츠 |
| `NC` | NC 다이노스 |
| `WO` | 키움 히어로즈 |
| `KT` | KT 위즈 |
