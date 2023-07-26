# Repository

## 목차

## 1. Repository

- Type of Git Respository
  - Local Respository : 내 PC에 파일이 저장되는 개인 전용 저장소
    - 서버에 반영하기 위해서 local에서 작업한 것은 remote & push 해줘야 함
  - Remote repository : 코드와 버전 관리 이력을 온라인 상의 특정 위치에 저장하여 여러 개발자가 협업하고 코드를 공유할 수 있는 저장 공간
    - 다양한 원격 저장소 서비스 : gitlab, github, bitbucket
    - 그 중, github이 압도적인 점유율을 보유하고 있다.

  - git remote add origin http://원격저장소url : 로컬 저장소에 원격 저장소의 주소를 추가하는 방법
    - 첫 번째로 원격 저장소를 추가할 경우에는 origin으로 저장하자고 약속
    - git remote -v : 제대로 remote 되어있는지 확인
    - 주의사항 : remote라는 것은 "연결"되었다는 것이 아닌, 주소를 등록하는 개념이다!(각 주소들을 별명으로 구분한다.)
    - 등록하는 원격 저장소의 개수는 제한이 없다.

2. Git & Github
- 충격주의 : 둘은 사실 아무 연관성이 없다....

- How to make github repository? : 깃헙에서 commit 창고 생성법
  - github -> 내 계정 클릭 -> Your profile -> (+)버튼 -> New repository -> Add a README file(README.md : repository에 대한 명세서)
  - 처음 rep를 만드는 경우 :
    - git init
    - git add README.md
    - git commit -m "first commit"
    - git remote add origin https:// ~~~~

  - 기존에 깃허브를 썼던 경우 :
    - git remote add origin https:// ~~~~

## 3. Push, Pull & Clone
- Push : 원격 저장소에 commit 목록을 업로드하는 것
  - 즉, 내 github에 local repo에서 commit한 내용을 업로드하는 것
  - git push origin master이라는 명령어 사용
    - git아 origin이라는 별명의 원격 저장소에 master(branch)를 push해
  - 결국 commit한 이력(git log 내용)이 없다면 push 할 수 없다.

- Clone : 원격 저장소에 있는 것을 통째로 복제하는 것
  - git clone http://원격저장소url 이라는 명령어 사용
    - git아 원격 저장소에 있는 모든 내용을 그대로 복제해 와줘!
  - Clone같은 경우는 이미 기존에 원격 저장소와 remote한 로컬 저장소에서 git init을 했기 때문에, 할 필요가 없음

- Pull : Clone 이후에 변경된 commit들을 가져오는 것
  - git pull origin master이라는 명령어 사용

- Push, Pull, Clone 과정 예시
  - ex. 두 Local A와 B가 협업을 할 것이다. A는 1과 2라는 Commit을 Github에 Push할 예정이다.
    - A_computer에서 gitbash -> git init
    - git add .(1)
    - git add .(2)
    - git commit -m "first commit"
    - git remote add origin 깃허브주소
    - git remote -v
  - 현재 A의 local repository에 있는 commit을 모두 나의 깃허브(remote repository)로 옮겼음
    - 이제 B가 이것을 복제할 차례