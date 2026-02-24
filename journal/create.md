## 직관일지 생성

### 개요

새로운 직관일지를 작성합니다. 경기 정보, 점수, 감정 태그, 후기, 이미지를 포함할 수 있습니다.

### 📌 엔드포인트

`POST /journals/contents`

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
| `Content-Type` | String | `application/json` | ✅ |
| `Authorization` | String | `Bearer {JWT_TOKEN}` | ✅ |

### Body

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `gameId` | String | 경기 고유 ID (예: `20250622OBLG0`) | ✅ |
| `gameDate` | String | 경기 날짜 (`yyyy-MM-dd HH:mm`) | ✅ |
| `stadiumSC` | String | 경기장 숏코드 (예: `JAM`) | ✅ |
| `opponentTeamSC` | String | 상대팀 숏코드 (예: `OB`) | ✅ |
| `ourScore` | int | 우리팀 점수 | ✅ |
| `theirScore` | int | 상대팀 점수 | ✅ |
| `fileName` | String | 업로드할 이미지 파일명 (확장자 포함) | ⬜️ |
| `emotion` | String | 감정 태그 (`MOVED`, `THRILLED`, `FRUSTRATED`, `REGRETFUL`, `ANGRY`) | ✅ |
| `review_text` | String | 후기글 | ⬜️ |
| `isPublic` | boolean | 공개 여부 (기본값: `false`) | ⬜️ |

### ▶️ 요청 예시

```json
{
  "gameId": "20250622OBLG0",
  "gameDate": "2025-06-22 18:30",
  "stadiumSC": "JAM",
  "opponentTeamSC": "LG",
  "ourScore": 5,
  "theirScore": 3,
  "fileName": "game_photo.jpg",
  "emotion": "THRILLED",
  "review_text": "오늘 경기 짜릿했다! 역전승!",
  "isPublic": true
}
```

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `201 Created` | 직관일지 생성 완료 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.journalId` | Long | 생성된 직관일지 ID |

### 응답 예시

```json
{
  "code": "JOURNAL_CREATED",
  "message": "직관 일지가 등록되었습니다.",
  "data": {
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
| `404 Not Found` | 등록되지 않은 경기 | `GAME_NOT_FOUND` |
| `404 Not Found` | 등록되지 않은 경기장 | `STADIUM_NOT_FOUND` |
| `404 Not Found` | 등록되지 않은 팀 | `TEAM_NOT_FOUND` |
| `404 Not Found` | 감정 태그가 없음 | `EMOTION_TAG_NOT_FOUND` |
| `400 Bad Request` | 파일명 형식 오류 | `INVALID_FILE_NAME` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

**응답 예시 (404 Not Found)**

```json
{
  "code": "GAME_NOT_FOUND",
  "message": "등록되지 않은 경기입니다."
}
```

</aside>
