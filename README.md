# git
웹스타일 깃 허브 브랜치 관리(목표)

(팀장)
git init -> 최초에 초기화 시킴
git add .
git commit -m "first commit" -> 설명을 달아서 커밋
git branch -M main -> 브랜치 이름을 강제로 main으로 변경
git remote add origin https://github.com/leedongjin9705/study_git.git -> 내 깃허브 주소와 연동
git push -u origin main -> main이라는 브랜치에 푸시


(팀원)
git clone git@github.com: + 프로젝트 주소 -> 해당 주소 프로젝트를 복사해옴
(코드수정 후)
git add . -> .은 전부를 뜻함, 즉 전부 깃에 올리겠다는 뜻 (git add 경로/파일명 -> 해당 파일만 올림)
git commit -m "first commit" -> 설명을 달아서 커밋
git checkout -b freshman -> freshman이라는 새로운 브랜치를 만듬 (-b로 없던 브랜치를 생성하고 그곳으로 이동)


Author
(팀원)
깃허브 들어와서
Compare & pull request 클릭
팀장에게 메세지를 남김.(해당 코드에 대한 설명)
Create pull request 클릭


(팀장)
깃허브 들어와서
Pull requests 메뉴에 알림 확인
메세지 및 코드 확인
Merge pull request 클릭
보라색이 뜨면 성공


(팀장)
이미 팀원의 코드가 마스터로 올라간 상태. 이후 같은 페이지 내에서 동시에 작업했을 때
git add .
git commit -m "second commit" -> 커밋까지만 함
git pull origin master -> master 브랜치로부터 새로운 코드를 받아옴
git push origin master -> master로 올림


(팀원)
pull 이후 작업 시작


추가 명령어
git merge --abort -> 충돌시 병합 전으로 되돌림.


만약 같은 파일 내에서 어떤 내용은 먼저 반영하고, 어떤 내용은 나중에 반영해야 할 때(1)

일단 머지하는 법(main이 기준일 때)
git checkout main (main으로 브랜치 이동)
git pull origin main (최신상태 갱신)
git merge 머지할 브랜치명
if(충돌이 없다면)
git push origin main

else(충돌이 있다면) 2가지 방법이 있음

git merge —abort -> merge 이전 상태로 돌아감
충돌이 난 파일을 열어 <<<<<<<, =======, >>>>>>> 표시된 부분을 수동으로 수정
git add .
git commit
git push origin main
finally
git branch -d 삭제할 브랜치명 # 로컬 브랜치 삭제
git push origin --delete 삭제할 브랜치명 # 원격 브랜치 삭제


<<<<<<<, =======, >>>>>>> 에 대하여

<<<<<<< HEAD -> 내 브랜치 코드 시작
코드
======= -> 두 코드의 경계
코드

브랜치명 -> 병합 대상 브랜치


인텔리제이에서 충돌시
충돌 발생시 충돌 파일을 더블클릭하면 3-way merge tool이 열림

[왼쪽] = 내 브랜치(HEAD)
[중앙] = 최종 결과
[오른쪽] = 병합할 브랜치

화면 오른쪽 위에 Apply 클릭 (또는 Apply and Close)
IntelliJ가 자동으로 git add 처리함
터미널에서 커밋하기

git commit
git push origin main


만약 같은 파일 내에서 어떤 내용은 먼저 반영하고, 어떤 내용은 나중에 반영해야 할 때(2)

상황 = main 브랜치, error가 있는 브랜치, 반영해야하는 로컬 브랜치

반영해야하는 로컬 브랜치 반영시
git checkout main (main으로 브랜치 이동)
git pull origin main (최신상태 갱신)
git merge 머지할 브랜치명
git push origin main
git branch -d 삭제할 브랜치명 -> # 로컬 브랜치 삭제
git push origin --delete 삭제할 브랜치명 -> # 원격 브랜치 삭제

이후

error가 있는 브랜치 반영시
git checkout main (main으로 브랜치 이동)
git pull origin main (최신상태 갱신)
git merge 머지할 브랜치명
충돌이 난 파일을 열어 <<<<<<<, =======, >>>>>>> 표시된 부분을 수동으로 수정
git add .
git commit -m "메세지"
git push origin main
git branch -d 삭제할 브랜치명 -> # 로컬 브랜치 삭제
git push origin --delete 삭제할 브랜치명 -> # 원격 브랜치 삭제


병합충돌 해결 관련 사이트
https://www.freecodecamp.org/korean/news/how-to-resolve-merge-conflicts-in-git/


같은 파일을 작업하며, 한명은 파일을 삭제, 한명은 파일을 수정했을 때

git add 파일명 -> 파일 추가
git rm 파일명 -> 파일 삭제
git commit -m "Message"
git push


git branch -> 현재 브랜치 확인법


[깃 브챈치 사용법]

인텔리제이 기준으로 작성하였습니다.

현재 페이지에서 master이라고 표현한 브랜치는 최근 main이라는 이름으로 많이 사용하고 있다고 합니다.

(master/slave 관계가 인종 차별을 떠올리게 해서 그렇다고 함)

[git 명령어 정리]

`git branch -> 현재 브랜치 확인법
git branch 이름 -> 브랜치 생성
git checkout 이름 -> 브랜치 이동
git pull origin master -> 최신상태 갱신
git merge 이름 -> 병합
git branch -d 이름 -> 로컬 브랜치 정리
git push origin --delete 이름 -> 원격 브랜치 정리
git merge --abort -> merge 이전 상태로 되돌림

git init -> 최초에 초기화 시킴
git add . -> 커밋할 파일 준비
git commit -m "first commit" -> 설명을 달아서 커밋
git branch -M main -> 브랜치 이름을 강제로 main으로 변경
git remote add origin 주소 -> 내 깃허브 주소와 연동
git push -u origin main -> main이라는 브랜치에 푸시(-u를 달면 이후에는 git push, git pull만으로 푸시 풀 가능)`

[git branch 사용법]

브랜치 생성시 checkout 되어있는 브랜치 기준으로 브랜치가 따집니다.

지금은 대부분 master branch에서 작업을 하니 아래 상황으로 보여드리겠습니다.

(상황 - master 브랜치에서 수정중 같은 페이지 내의 다른 내용을 현재 수정중인 부분보다 먼저 반영해야한다.)

해당 프로젝트 경로로 이동 (workspace에서 생성시 workspace에만 branch가 생성됨) (추가, 수정, 충돌 하나씩 만들어두기)

새로운 브랜치를 만든다.
git branch test/1
git checkout test/1
git add .
git commit -m “message1“
git push origin test/1

git checkout master (마스터 브랜치로 이동)-> test/1에 푸시한 내용이 보이지 않음.

git pull origin master → 최신상태 갱신
git branch test/2
git checkout test/2

test/2를 수정
git checkout test/1
git add .
git commit -m “message2“
git push origin test/2

test/2의 내용을 먼저 반영해보자
git checkout master (반영할 브랜치로 이동)
git merge test/2
git push origin master

병합충돌 예시
git merge test/1

병합충돌 발생 → 충돌 발생시 3-way merge tool 사용/

녹색: 추가된 코드

파란색: 수정된 코드

빨간색: 충돌난 코드

처리 후
git commit -m “최종“
git push origin master

(관리 측면에서 사용이 끝난 브랜치는 정리하는 게 맞으나, 정책에 따라 유지할 수도 있습니다.)
git branch -d test/1 → 로컬 브랜치 정리
git push origin --delete test/1 → 원격 브랜치 정리

우리 회사는 유지보수가 많은데, 브랜치를 어떻게 관리해서 유지보수시에 사용할지 이야기해보면 좋겠습니다

혼자: 로컬 브랜치 따서 작업

협업: 도움이 필요하면, 브랜치를 원격 저장소에 올려서, 하나의 브랜치를 두명이 작업

브랜치 명명규칙: 지라 이슈코드
