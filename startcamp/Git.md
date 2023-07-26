# 3. Git

## Git : 분산 버전 관리 시스템

### 1. 버전(version)이란?

버전 : 이전 버전으로부터의 변경 사항을 기록하는 것
- 버전 관리 : 변화를 기록하고 추적하는 것
  - Git에서는 버전 대신 commit이라는 용어 사용
  - Git은 CLI에서 명령어를 통해 버전 관리를 시행함
  - Git은 용량의 효율성을 위해 마지막 파일만 저장 / 그 전들의 버전들을 저장(저장 = ver 1 + ver 2 + ver 3 + …)
  - ex. 기존 방식 vs 개선 방식
            
 ![기존vs개선.PNG](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75ae25ac-3777-4db7-9c6d-ebc236393854/%EA%B8%B0%EC%A1%B4vs%EA%B0%9C%EC%84%A0.png)
            
  - 버전 관리 예시 : google docs
  
### 2. 중앙 집중식 vs 분산식
       
중앙 집중 식 : 버전을 중앙 서버에 저장하고, 중앙 서버에서 파일을 가져와 다시 중앙에 업로드
    
분산 식 : 버전을 여러 개의 복제된 저장소에 저장 및 관리
    
분산 구조의 장점
- 중앙 서버에 의존 X → 다양한 작업 수행 동시에 가능(개발자들이 팀 프로젝트를 할 수 있는 이유)
- 개발자들 간의 작업 충돌 감소
- 개발 생산성 향상
- 중앙 서버의 장애나 손실에 대비한 백업에 용이
- 인터넷에 연결되지 않은 환경에서도 작업 가능
- 변경 이력과 코드를 로컬 저장소에 기록하고, 나중에 중앙 서버와 동기화

### 3. git의 역할
- 코드의 버전 관리(개발되어 온 과정을 쉽게 파악 가능)
- 이전 버전과의 변경 사항 비교

### 4. git의 영역
    
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e1bd9f8-21a2-49f8-99a9-164b718c90e3/Untitled.png)
    
Working Directory(WD) : 실제 작업 중인 파일들이 위치하는 영역 

Staging Area : WD에서 변경된 파일 중 다음 버전에 포함 시킬 파일들을 선택적으로 추가하거나 삭제할 수 있는 중간 준비 영역
- 즉, 버전을 만들 애들의 대기실 느낌(버전을 만들까 말까?)
- 명령어로 확인 할 수 있는 영역(처음에는 헷갈릴수동)
- 아직은 기록이 안됨

Repository : 버전 이력과 파일들이 영구적으로 저장되는 영역
- 모든 버전과 변경 이력이 기록됨
- Staging Area에 있는 버전들 중 Snapshot을 찍은 버전들이 Repository에 쌓임
- WD에서 바로 Repository에 직행으로 갈 수는 없다

WD → SA —(snapshot)—> RP
            
++ What is commit? 
- Commit(version of  Git)
  
### 5. Git의 동작순서

git init : 로컬 저장소(local repository) 초기화  
- git의 버전 관리를 시작합니다.
- git의 버전 관리를 시작하는 dir에서 맨 처음 시행하는 명령어
- 맨 끝에 (master)가 붙어있다면, 현재 영역이 git 영역임을 알 수 있음
- 해당 dir에 있는 폴더 안에서만 버전관리 시행(밖의 폴더들에는 영향 X)
- git init 주의사항 : git 로컬 저장소 내에 또다른 git 로컬 저장소를 만들지 말 것
  - 최상위폴더에서 git 로컬 저장소를 만들어낼 경우, 하위폴더도 git 영역에 이미 포함되기 때문
  - 만약, 이러한 실수를 저질렀다면, 잘못 git init을 실행한 곳에 가서 숨긴 항목(.git)을 제거하면 됨

git status : git 영역의 상태
- 항상 명령어 실행 후 꾸준히 확인해주기!

git add : 변경사항이 있는 파일을 staging area에 추가

git commit : staging area에 있는 파일들을 저장소에 기록
- 해당 시점의 버전 생성(옵션을 이용하여 버전 이름도 작성)하고 변경 이력을 남기는 것
- 첫 버전 기록시 git commit -m “first commit” 명령어 입력
- 그 이후로는 대충 git commit -m “버전기록내용” 으로 입력
- 첫 commit을 할 시에, global email과 name을 작성해야 함 : 한 컴퓨터에서 git 사용자는 한명이어야만 한다.(컴퓨터에서 git을 사용할 때 최초 1회만 작성)
  - git config —global user.email “본인 이메일(싸피이메일)”
  - git config —global user.name “본인 닉네임”
        
git log : 지금까지의 commit 내용 출력
- git log —oneline : 한번에 출력해줌(보기 편하게)
    
- git 실습해보기