# CL-UP: 동아리 통합 관리 시스템

CL-UP은 대학 동아리 홍보, 가입, 공지 관리 등을 위한 통합 웹 애플리케이션입니다.  
Firebase를 기반으로 사용자 인증 및 데이터베이스를 관리하며, HTML, CSS, JavaScript로 구성되어 있습니다.

---

### 프로젝트 구성

| 파일/폴더         | 설명                                    |
|------------------|----------------------------------------|
| `index.html`     | 메인 페이지                              |
| `login.html`     | 로그인 페이지                            |
| `signup.html`    | 회원가입 페이지                          |
| `dashboard.html` | 로그인 후 접근 가능한 사용자 대시보드       |
| `board_*.html`   | 동아리 모집글 작성/조회 페이지             |
| `notice_*.html`  | 공지사항 관련 페이지                      |
| `club_*.html`    | 동아리 가입/공지 기능 관련 페이지           |
| `user_*.html`    | 사용자 정보 수정, 관리자 기능 등           |
| `js/` 폴더        | 모든 JavaScript 기능 모듈화 파일들         |
| `firebase.js`    | Firebase 초기화 설정 파일                |

---

### 사용 기술

- HTML5  
- CSS3  
- JavaScript (ES6+)  
- Firebase (Authentication, Firestore)

---

### 실행 방법

#### 1. 프로젝트 다운로드
(1) clone
```bash 
git clone [저장소 주소] 

(2) ZIP 파일 다운로드 후 압축 해제


#### 2. Firebase 연동
Firebase Console에서 새 프로젝트 생성

Authentication > 이메일/비밀번호 로그인 활성화

Cloud Firestore > Database 생성

프로젝트 설정 > 일반 > Firebase SDK 설정 정보 복사

- firebase.js 예시
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
import { getAuth } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js";
import { getFirestore } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};

const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
export const db = getFirestore(app);


####3. 로컬 실행
크롬 브라우저로 index.html을 직접 열거나, Live Server를 이용하거나, 다음 명령어로 로컬 서버를 실행합니다.
npx serve public


#### 관리자 계정 안내
일부 기능(공지 작성, 회원 목록 조회 등)은 관리자 계정으로만 접근 가능합니다.
관리자 권한은 Firestore의 members 컬렉션에서 해당 문서의 admin 필드를 true로 수동 수정해야 합니다.