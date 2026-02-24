# 에러 코드 목록

InningLog API에서 반환하는 모든 에러 코드 목록입니다.

---

## 에러 응답 형식

```json
{
  "code": "에러_코드",
  "message": "에러 메시지"
}
```

---

## 유효성 / 파라미터 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `VALIDATION_ERROR` | 400 Bad Request | 요청값이 올바르지 않습니다. |
| `TYPE_MISMATCH` | 400 Bad Request | 요청 파라미터 타입이 올바르지 않습니다. |
| `METHOD_ARGUMENT_NOT_VALID` | 400 Bad Request | 잘못된 인자입니다. |
| `PARAMETER_NOT_FOUND` | 400 Bad Request | Parameter가 존재하지 않습니다. |
| `METHOD_NOT_ALLOWED` | 405 Method Not Allowed | 지원하지 않는 HTTP 메서드입니다. |
| `RESOURCE_NOT_FOUND` | 404 Not Found | 요청한 리소스를 찾을 수 없습니다. |

---

## 인증 / 회원 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `UNAUTHORIZED_ACCESS` | 401 Unauthorized | 권한이 없습니다. |
| `USER_NOT_FOUND` | 404 Not Found | 존재하지 않는 회원입니다. |
| `DUPLICATE_NICKNAME` | 400 Bad Request | 이미 존재하는 닉네임입니다. |
| `INVALID_NICKNAME` | 400 Bad Request | 닉네임 형식이 올바르지 않습니다. |
| `ALREADY_SET` | 409 Conflict | 이미 팀이 설정되어 변경할 수 없습니다. |
| `EXIST_USERID` | 400 Bad Request | 이미 존재하는 아이디입니다. |
| `INVALID_PASSWORD_FORMAT` | 400 Bad Request | 비밀번호 형식이 올바르지 않습니다. |
| `INVALID_PASSWORD` | 400 Bad Request | 비밀번호가 일치하지 않습니다. |
| `INVALID_USERID_FORMAT` | 400 Bad Request | 아이디 형식이 올바르지 않습니다. |

---

## 팀 / 구장 / 경기 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `TEAM_NOT_FOUND` | 404 Not Found | 등록되지 않은 팀입니다. |
| `STADIUM_NOT_FOUND` | 404 Not Found | 등록되지 않은 경기장입니다. |
| `GAME_NOT_FOUND` | 404 Not Found | 등록되지 않은 경기입니다. |
| `NO_VISITED_GAMES` | 400 Bad Request | 직관한 경기가 없습니다. |

---

## 직관일지 / 좌석시야 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `JOURNAL_NOT_FOUND` | 404 Not Found | 작성하지 않은 일지입니다. |
| `EMOTION_TAG_NOT_FOUND` | 404 Not Found | 감정 태그가 없습니다. |
| `ZONE_NOT_FOUND` | 404 Not Found | 등록되지 않은 존입니다. |
| `SEATVIEW_NOT_FOUND` | 404 Not Found | 작성하지 않은 좌석시야 후기입니다. |
| `SEATVIEW_ALREADY_EXISTS` | 400 Bad Request | 이미 좌석시야 글이 작성된 직관일지입니다. |
| `INVALID_SEAT_SEARCH` | 400 Bad Request | 존 정보 없이 열만으로는 검색할 수 없습니다. |
| `INVALID_HASHTAG_REQUEST` | 400 Bad Request | 해시태그는 최소 1개, 최대 5개까지 가능합니다. |

---

## 이미지 / 파일 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `INVALID_FILE_NAME` | 400 Bad Request | 파일명에 슬래시(/) 또는 경로문자(../)를 포함할 수 없습니다. |
| `FILE_IS_EMPTY` | 400 Bad Request | 업로드할 파일이 없습니다. |
| `S3_UPLOAD_FAILED` | 500 Internal Server Error | 이미지 업로드 중 오류가 발생했습니다. |

---

## 게시글 / 댓글 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `POST_NOT_FOUND` | 404 Not Found | 존재하지 않는 게시글입니다. |
| `ROOT_COMMENT_NOT_FOUND` | 404 Not Found | 존재하지 않는 상위 댓글입니다. |
| `COMMENT_NOT_FOUND` | 404 Not Found | 존재하지 않는 댓글입니다. |

---

## 좋아요 / 스크랩 관련

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `LIKE_ALREADY_EXISTS` | 400 Bad Request | 이미 좋아요를 누른 콘텐츠입니다. |
| `LIKE_NOT_FOUND` | 404 Not Found | 존재하지 않는 좋아요입니다. |
| `SCRAP_ALREADY_EXISTS` | 400 Bad Request | 이미 스크랩한 콘텐츠입니다. |
| `SCRAP_NOT_FOUND` | 404 Not Found | 존재하지 않는 스크랩입니다. |

---

## 서버 오류

| 에러 코드 | HTTP Status | 설명 |
| --- | --- | --- |
| `INTERNAL_SERVER_ERROR` | 500 Internal Server Error | 서버에 문제가 발생했습니다. |
