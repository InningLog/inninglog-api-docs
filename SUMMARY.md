# Table of contents

* [InningLog](README.md)

## 인증 <a href="#auth" id="auth"></a>

* [카카오 로그인](auth/kakao-login.md)
* [카카오 OAuth 콜백](auth/kakao-callback.md)

## 회원 <a href="#member" id="member"></a>

* [닉네임 + 응원팀 초기 설정](member/setup.md)
* [닉네임 수정](member/update-nickname.md)
* [응원팀 설정](member/update-team.md)
* [내 팀 정보 조회](member/get-team.md)

## 홈 <a href="#home" id="home"></a>

* [홈 화면 정보 조회](home/view.md)

## 직관일지 <a href="#journal" id="journal"></a>

* [경기 일정 조회](journal/schedule.md)
* [경기 정보 조회](journal/game-info.md)
* [직관일지 생성](journal/create.md)
* [직관일지 상세 조회](journal/detail.md)
* [직관일지 수정](journal/update.md)
* [캘린더 일지 목록](journal/calendar.md)
* [모아보기 일지 목록](journal/summary.md)
* [공개 일지 피드](journal/feed.md)
* [내가 쓴 일지 목록](journal/my.md)
* [직관일지 댓글 생성](journal/comment-create.md)
* [직관일지 댓글 목록 조회](journal/comment-list.md)
* [직관일지 좋아요](journal/like.md)
* [직관일지 스크랩](journal/scrap.md)

## 커뮤니티 <a href="#community" id="community"></a>

* [커뮤니티 홈 조회](community/home.md)
* [게시글 생성](community/post-create.md)
* [게시글 단일 조회](community/post-detail.md)
* [팀별 게시글 목록](community/post-by-team.md)
* [인기 게시글 목록](community/post-popular.md)
* [내가 쓴 게시글 목록](community/post-my.md)
* [내가 댓글 단 게시글 목록](community/post-my-commented.md)
* [내가 스크랩한 게시글 목록](community/post-my-scrapped.md)
* [게시글 수정](community/post-update.md)
* [게시글 삭제](community/post-delete.md)
* [게시글 댓글 생성](community/comment-create.md)
* [게시글 댓글 목록 조회](community/comment-list.md)
* [댓글 삭제](community/comment-delete.md)
* [게시글 좋아요](community/post-like.md)
* [댓글 좋아요](community/comment-like.md)
* [게시글 스크랩](community/post-scrap.md)

## 좌석시야 <a href="#seatview" id="seatview"></a>

* [좌석시야 생성](seatview/create.md)
* [좌석시야 상세 조회](seatview/detail.md)
* [일반 좌석 검색](seatview/search-normal.md)
* [해시태그 기반 좌석 검색](seatview/search-hashtag.md)

## 이미지 <a href="#image" id="image"></a>

* [게시글 이미지 Presigned URL 발급](image/upload-post.md)

## 직관 리포트 <a href="#report" id="report"></a>

* [직관 리포트 조회](report/main.md)

## 에러 코드 <a href="#error" id="error"></a>

* [에러 코드 목록](error/README.md)

<!-- AUTO-GENERATED-START -->

## 인증

* [일반 회원가입](auth/post-auth-signup.md)
* [일반 로그인](auth/post-auth-login.md)
* [카카오 로그인 페이지 요청](auth/get-login-page.md)
* [카카오 로그인 콜백(프론트 신경 쓰지 않아도 됨)](auth/get-callback.md)
* [아이디 중복 체크](auth/get-auth-check-id.md)

## 이미지

* [게시글 이미지 Presigned URL 목록 발급](image/post-images-upload-post.md)
* [좌석 시야용 Presigned URL 발급](image/get-s3-seatView-presigned.md)
* [직관 일지용 Presigned URL 발급](image/get-s3-journal-presigned.md)

## 직관일지

* [직관 일지 작성 페이지 - 직관 일지 콘텐츠 사전 정보 조회](journal/get-journals-contents.md)
* [직관 일지 작성 페이지 - 직관 일지 콘텐츠 업로드](journal/post-journals-contents.md)
* [특정 직관 일지 수정](journal/patch-journals-update-journalId.md)
* [본인 직관 일지 목록 페이지 - 모아보기](journal/get-journals-summary.md)
* [공개 직관 일지 검색](journal/get-journals-search.md)
* [본인 직관 일지 캘린더 페이지 - 유저 응원팀의 특정 날짜 경기 일정 조회[팝업 형태]](journal/get-journals-schedule.md)
* [공개 직관 일지 피드 조회](journal/get-journals-feed.md)
* [특정 직관 일지 조회](journal/get-journals-detail-journalId.md)
* [본인 직관 일지 목록 페이지 - 캘린더](journal/get-journals-calendar.md)

## KBO 데이터 (내부용)

* [POST /api/kbo/team-rankings/win-rates](kbo-데이터-(내부용)/post-kbo-team-rankings-win-rates.md)
* [선수 기록 저장](kbo-데이터-(내부용)/post-kbo-player-stats.md)
* [POST /api/kbo/games/schedule](kbo-데이터-(내부용)/post-kbo-games-schedule.md)
* [POST /api/kbo/games/results](kbo-데이터-(내부용)/post-kbo-games-results.md)
* [게임별 선수 기록 조회](kbo-데이터-(내부용)/get-kbo-player-stats-gameId.md)
* [GET /api/kbo/games/with-boxscore](kbo-데이터-(내부용)/get-kbo-games-with-boxscore.md)
* [GET /api/kbo/games/stats](kbo-데이터-(내부용)/get-kbo-games-stats.md)

## 회원

* [회원 초기 설정 (닉네임 + 응원팀)](member/post-member-setup.md)
* [회원의 응원 팀 설정](member/patch-member-setup.md)
* [닉네임 수정](member/patch-member-nickname.md)
* [내 팀 정보 조회](member/get-member-team.md)

## 검색

* [최근 검색어 조회](검색/get-search-history.md)
* [검색어 삭제](검색/delete-search-history-searchHistoryId.md)

## 마이페이지

* [내가 쓴 직관 일지 목록 조회](마이페이지/get-journals-my.md)
* [내가 쓴 글 목록 조회](마이페이지/get-community-posts-my.md)
* [내가 스크랩한 글 목록 조회](마이페이지/get-community-posts-my-scrapped.md)
* [내가 댓글 단 글 목록 조회](마이페이지/get-community-posts-my-commented.md)

## 좌석시야

* [좌석 시야 생성](좌석시야/post-seatViews-contents.md)
* [특정 좌석 시야 조회](좌석시야/get-seatViews-seatViewId.md)
* [일반 좌석 검색 (게시물 형태)](좌석시야/get-seatViews-normal-gallery.md)
* [해시태그 기반 좌석 검색 (모아보기)](좌석시야/get-seatViews-hashtag-gallery.md)

## 직관일지 - 리포트

* [직관 리포트 정보 가져오기](직관일지---리포트/get-report-main.md)

## 직관일지 - 소셜

* [직관일지 스크랩](직관일지---소셜/post-journals-journalId-scraps.md)
* [직관일지 스크랩 취소](직관일지---소셜/delete-journals-journalId-scraps.md)
* [직관일지 좋아요](직관일지---소셜/post-journals-journalId-likes.md)
* [직관일지 좋아요 취소](직관일지---소셜/delete-journals-journalId-likes.md)
* [직관일지 댓글 목록 조회](직관일지---소셜/get-journals-journalId-comments.md)
* [직관일지 댓글 생성](직관일지---소셜/post-journals-journalId-comments.md)

## 커뮤니티 - 게시글

* [게시글 생성](커뮤니티---게시글/post-community-teamSC-posts-create.md)
* [게시글 단일 조회](커뮤니티---게시글/get-community-posts-postId.md)
* [게시글 수정](커뮤니티---게시글/patch-community-posts-postId.md)
* [게시글 삭제](커뮤니티---게시글/delete-community-posts-postId.md)
* [팀별 게시글 목록 조회](커뮤니티---게시글/get-community-posts-team-teamShortCode.md)
* [게시글 검색](커뮤니티---게시글/get-community-posts-search.md)
* [인기 게시글 목록 조회](커뮤니티---게시글/get-community-posts-popular.md)
* [커뮤니티 홈 조회](커뮤니티---게시글/get-community-home.md)

## 커뮤니티 - 소셜

* [게시글 스크랩 생성](커뮤니티---소셜/post-community-posts-postsId-scraps.md)
* [게시글 좋아요 생성](커뮤니티---소셜/post-community-posts-postId-likes.md)
* [게시글 좋아요 취소](커뮤니티---소셜/delete-community-posts-postId-likes.md)
* [게시글 댓글 목록 조회](커뮤니티---소셜/get-community-posts-postId-comments.md)
* [게시글 댓글 생성](커뮤니티---소셜/post-community-posts-postId-comments.md)
* [댓글 좋아요 생성](커뮤니티---소셜/post-community-comments-commentId-likes.md)
* [댓글 좋아요 취소](커뮤니티---소셜/delete-community-comments-commentId-likes.md)
* [게시글 스크랩 취소](커뮤니티---소셜/delete-community-posts-postId-scraps.md)
* [댓글 삭제](커뮤니티---소셜/delete-community-comments-commentId.md)

## 홈

* [홈 화면 정보 조회](홈/get-home-view.md)

<!-- AUTO-GENERATED-END -->
