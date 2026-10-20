# CANB English Speech Contest 코칭 신청 사이트

파일: index.html (사이트 전체) · logo.png · firestore.rules · firebase.json

## 1. Firebase 준비 (한 번만)
1. https://console.firebase.google.com 에서 프로젝트 생성
2. 빌드 > **Firestore Database** > 데이터베이스 만들기 (프로덕션 모드, 서울 asia-northeast3 권장)
3. 빌드 > **Authentication** > 시작하기 > 로그인 방법 > **이메일/비밀번호** 사용 설정
4. Authentication > 사용자 > 사용자 추가: 이메일 `admin@canb-english.com`, 비밀번호 = 관리자 비밀번호
   (다른 이메일을 쓰려면 index.html 의 `ADMIN_EMAIL` 과 firestore.rules 의 `isAdmin()` 이메일을 같이 변경)
5. 프로젝트 설정 > 내 앱 > 웹 앱(</>) 추가 > 표시되는 `firebaseConfig` 값을 index.html 의 `FIREBASE_CONFIG` 에 붙여넣기
6. Firestore > 규칙 탭에 `firestore.rules` 내용을 붙여넣고 **게시**
7. Authentication > 설정 > 승인된 도메인에 배포 주소(예: `계정명.github.io`) 추가

## 2-A. GitHub Pages로 배포
저장소 생성 후 index.html, logo.png 업로드 > Settings > Pages > Branch: main / root > Save
→ `https://계정명.github.io/저장소명/` 이 학생용 링크

## 2-B. Firebase Hosting으로 배포
`npm i -g firebase-tools` > `firebase login` > `firebase init`(Hosting, Firestore, 기존 파일 유지) > `firebase deploy`

## 일정/정원 수정
index.html 의 `SLOTS`, `TEACHERS`(정원 cap) 수정 + firestore.rules 의 `capOf`, `validSlot` 도 동일하게 수정
