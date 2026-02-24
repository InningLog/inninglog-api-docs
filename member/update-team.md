## 응원팀 설정

### 개요

로그인한 사용자의 응원팀을 설정합니다. 최초 1회만 가능하며, 이후 변경할 수 없습니다.

### 엔드포인트

`PATCH /member/setup`

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
| `teamShortCode` | String | 응원팀 숏코드 (예: `OB`, `LG`) | |

### 요청 예시

```json
{
  "teamShortCode": "OB"
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
| `200 OK` | 응원팀 설정 완료 |

### 응답 예시

```json
{
  "code": "TEAM_SET",
  "message": "응원 팀이 성공적으로 설정되었습니다.",
  "data": null
}
```

</aside>

---

### 실패 (Error)

<aside>

| HTTP Status | 의미 | 에러 코드 |
| --- | --- | --- |
| `404 Not Found` | 등록되지 않은 팀 | `TEAM_NOT_FOUND` |
| `409 Conflict` | 이미 팀이 설정됨 (변경 불가) | `ALREADY_SET` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

**응답 예시 (409 Conflict)**

```json
{
  "code": "ALREADY_SET",
  "message": "이미 팀이 설정되어 변경할 수 없습니다."
}
```

</aside>
