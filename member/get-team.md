## 내 팀 정보 조회

### 개요

로그인한 사용자의 응원팀 정보를 조회합니다.

### 엔드포인트

`GET /member/team`

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

별도의 Path Parameters, Query Parameters, Body가 필요하지 않습니다.

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 팀 정보 조회 성공 |

**Body**

| Key | Type | 설명 |
| --- | --- | --- |
| `code` | String | 성공 코드 |
| `message` | String | 성공 메시지 |
| `data.teamShortCode` | String | 응원팀 숏코드 (예: `LG`) |

### 응답 예시

```json
{
  "code": "SUCCESS",
  "message": "요청이 정상적으로 처리되었습니다.",
  "data": {
    "teamShortCode": "LG"
  }
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |
| `404 Not Found` | 존재하지 않는 회원 | `USER_NOT_FOUND` |

**응답 예시 (401 Unauthorized)**

```json
{
  "code": "UNAUTHORIZED_ACCESS",
  "message": "권한이 없습니다."
}
```

</aside>
