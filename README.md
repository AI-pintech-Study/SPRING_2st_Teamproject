<h1>포켓몬 도감 클론 코딩 프로젝트</h1>

<h2>1. 개발 환경</h2>

- Intelli J
- Gradle
- java
- GitHub
- Spring

<h2>2. 역할분담</h2>

추후 추가 예정

<h2>3. UserflowChart</h2>

![image](https://github.com/user-attachments/assets/beb11a8e-b088-4af7-97ee-8bdb94d3e12e)


<h2>4. 기능 명세서</h2>

1] 메인 화면 도메인

메뉴 버튼
- 도감
- 게시글
- 회원정보
- QNA
- Game

2] 도감 도메인

2-1]도감 조회
- key값(이름) 검색해서 상세 조회 기능

- filter사용해서 카테고리별로 조회 기능
종족값 / 타입 / 서식지등

- maptree활용 정렬 / 역정렬
이름 / 번호

3] QNA 도메인

조회는 모든 권한에서 접근 가능
Q 작성은 회원만 가능
A 작성은 관리자만 가능

4] 게시글 관리 도메인

4-1]게시글 목록 조회
- 게시판 페이지(글 번호 / 글 제목 / 작성자 / 작성 날짜 / 조회수)
- 게시글 제목or내용or작성자 포함하는 문자열로 검색 기능
- 게시글 목록 최상단 5칸은 어느 페이지든 공지사항 고정
	- DB 글 역정렬해서 표기?

4-2]게시글 상세 조회 (글 내용 & 작성 시간)
- 댓글 CRUD 기능
- 이전글 / 다음글 글 제목 보이고 클릭시 해당 글 상세조회로 이동 가능

4-3]게시글 추가
- 글 제목
- 글 내용
- 이미지 추가(미확정)
- 관리자 로그인 되어있을경우 공지사항 여부 checkbox

4-4]게시글 수정
- 관리자 or 작성자 본인만 수정 가능
- 게시글 작성자 확인은 회원 비밀번호로 유효성 검사

4-5]게시글 삭제
- 관리자 or 게시글 작성자 본인만 삭제 가능
- 게시글 작성자 확인은 회원 비밀번호로 유효성 검사


5]회원 관리 도메인

5-1]회원 가입

5-1-1] 개인 가입
- ID / PW / PW체크 / 이름 / 닉네임 / 약관 / 휴대폰 번호

ID 유효성 : 6~15글자 / (NOT NULL)
PW 유효성 : 6~20글자 / NOT NULL
이름 유효성 : NOT NULL / ~4글자
닉네임 유효성 : NOT NULL / 2~6글자
약관 : checkbox 1칸 / 유효성 검사 true / false
휴대폰번호 : 숫자만 가능
회원 DB : 관리자 boolean false
회원 번호 대리키로 부여
Status 1 부여
Status -> 외래키
1 : 활동중
2 : 강퇴
3 : 탈퇴

5-1-2] 관리자 가입

관리자 유효성 확인
- String값으로 관리자 전용 암호 입력 받아서 유효성 검사하면 관리자 가입 접근 가능
- 개인 가입 기능과 동일
- 회원 DB : 관리자 boolean true

5-2] 회원 정보 수정 (사용자 본인 PW로 유효성 확인 후 접근 가능)
- 수정 가능 목록 : 닉네임 / PW / 휴대폰 번호
- 회원 강퇴 (관리자쪽에서 접근시 노출)

5-3] 회원 탈퇴
5-3-1] 탈퇴
- 일반 회원 : 본인 비밀번호 유효성 검사 후 페이지 접근
- 정말 탈퇴하겠냐고 한번더 묻고(checkbox) true시
탈퇴 처리(Status 3 부여)
	
5-4] 회원 조회
- 관리자 권한 유효성 확인 후 접근가능
- 회원 정보 수정 접근가능

모든 회원의 모든 정보 출력
- 정렬 (ID & 이름 & 닉네임 & Status)

5-4-1] 회원강퇴
- 관리자 : 비밀번호 유효성 검사 후 페이지 접근
- 정말 강퇴하겠냐고 한번더 묻고(checkbox) true시
강퇴 처리(Status 2 부여)



6] Game 후보 3종

6-1] 월드컵

32강부터 시작 랜덤으로 포켓몬 32마리 데려와서(중복X) 순서대로 1:1 대결 구도로 출력해 좋아하는 포켓몬 이미지 클릭해 선택 후 최종으로 남는 1마리 우승

6-2] 퀴즈(주관식)

도감 상세조회에서 따와서 랜덤으로 이미지 보여주고 이름 String값 입력받아서 일치하나 확인

6-3] 포켓몬 부화 - 객체값+이로치 랜덤 뽑기

포켓몬 알 부화시켜서 객체값 + 이로치 요소 등등 랜덤으로 결정
