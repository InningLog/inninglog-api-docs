## 내가 스크랩한 게시글 목록

### 개요

마이페이지에서 내가 스크랩한 게시글 목록을 조회합니다. 무한 스크롤(Slice) 방식을 사용합니다.

### 📌 엔드포인트

`GET /community/posts/my/scrapped`

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
| `Authorization` | String | `Bearer {JWT_TOKEN}` | ✅ |

### Query Parameters

| Key | Type | 설명 | 필수 |
| --- | --- | --- | --- |
| `page` | int | 페이지 번호 (0부터 시작) | ⬜️ |
| `size` | int | 한 페이지 아이템 수 | ⬜️ |

</aside>

---

---

### ◀️ 응답 (Response)

<aside>

### 성공 (Success)

| HTTP Status | 의미 |
| --- | --- |
| `200 OK` | 스크랩한 게시글 목록 조회 성공 |

**Body (SliceResponse)**

응답 형식은 [팀별 게시글 목록](post-by-team.md)과 동일합니다.\
`likedByMe`, `scrapedByMe` 필드가 마이페이지에서는 실제 값으로 제공됩니다.

</aside>
