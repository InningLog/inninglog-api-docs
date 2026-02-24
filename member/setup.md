## 닉네임 + 응원팀 초기 설정

### 개요

신규 가입 후 최초 1회 닉네임과 응원팀을 동시에 설정합니다.

### 엔드포인트

`POST /member/setup`

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
| `nickname` | String | 설정할 닉네임 | |
| `teamShortCode` | String | 응원팀 숏코드 (예: `LG`, `OB`) | |

### 요청 예시

```json
{
  "nickname": "야구천재",
  "teamShortCode": "LG"
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
| `200 OK` | 초기 설정 완료 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data` | null | 없음 |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": null
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `400 Bad Request` | 이미 존재하는 닉네임 | `DUPLICATE_NICKNAME` |
| `400 Bad Request` | 닉네임 형식이 올바르지 않음 | `INVALID_NICKNAME` |
| `404 Not Found` | 등록되지 않은 팀 | `TEAM_NOT_FOUND` |
| `409 Conflict` | 이미 팀이 설정됨 | `ALREADY_SET` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

**응답 예시 (400 Bad Request)**

```json
{
  "code": "DUPLICATE_NICKNAME",
  "message": "이미 존재하는 닉네임입니다."
}
```

</aside>
