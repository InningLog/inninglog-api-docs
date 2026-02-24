## 직관일지 스크랩 / 스크랩 취소

### 개요

직관일지를 스크랩(북마크)하거나 스크랩을 취소합니다.

---

## 직관일지 스크랩

### 엔드포인트

`POST /journals/{journalId}/scraps`

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
| `journalId` | Long | 스크랩할 직관일지 ID |

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 스크랩 성공 |

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
| `404 Not Found` | 작성하지 않은 일지 | `JOURNAL_NOT_FOUND` |
| `400 Bad Request` | 이미 스크랩한 콘텐츠 | `SCRAP_ALREADY_EXISTS` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>

---

---

## 직관일지 스크랩 취소

### 엔드포인트

`DELETE /journals/{journalId}/scraps`

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
| `journalId` | Long | 스크랩 취소할 직관일지 ID |

</aside>

---

---

### 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 스크랩 취소 성공 |

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
| `404 Not Found` | 존재하지 않는 스크랩 | `SCRAP_NOT_FOUND` |
| `401 Unauthorized` | 인증 실패 | `UNAUTHORIZED_ACCESS` |

</aside>
