# GIT 가이드

GIT 가이드 및 활용법

GIT을 사용하는 방법과 유용한 링크에 대해서 기술한 가이드 입니다.

# GIT 이란?

깃이란 컴퓨터 파일의 변경사항을 추적하고 여려 명의 사용자들 간에 해당 파딜들의 작업을 조율하기 위한 분산 버전 관리 시스템이다. ( 위키백과 )

간단하게 분산버전 관리 시스템을 설명하면, 여러명의 개발자가 특정 프로젝트를 협업하여 개발하고 통합하고 버전관리를 할 수 있는 시스템을 말합니다.

### 1. **사용하는 이유**

git을 왜 사용할까? 

- 효과적인 협업
- 손쉬운 개발 및 테스트 환경 구축
- 효율적인 배포관리

### 2. GIT 용어 정리

- 브랜치 ( Branch )

      브랜치란 독립적으로 어떤 작업을 진행하기 위한 개념입니다. 필요에 의해 만들어지는 각각의 

      브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행할 수 있습니다.

      또한 이렇게 생성한 브랜치는 다른 브랜치와 병합함으로써, 작업한 내용을 다시 새로운 하나의   

      브랜치로 모을 수 있습니다.

![https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FcRPkVU%2FbtquUBRb7GK%2FbGy8lytovCtjsoP9SZKTJ0%2Fimg.jpg](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FcRPkVU%2FbtquUBRb7GK%2FbGy8lytovCtjsoP9SZKTJ0%2Fimg.jpg)

- 체크아웃 ( Checkout )

      Git에서 내가 사용할 브랜치를 지정하는 것을 의미합니다.  

- 커밋 ( Commit )

       파일 및 폴더의 추가 / 변경사항을 저장소에 기록할 수 있습니다.  또한 커밋을 하면 

       이전 커밋상태부터 현재 상태까지의 변경 이력이 기록된 커밋(리비전)이 만들어 집니다.

- 패스트 포워드 ( Fast-forward )

      패스트 포워드란 merge할 브랜치( 대상 브랜치 )의 commit이 현재 기준으로 합쳐야 할 branch

      ( master 브랜치 )의 commit보다 앞서가 있기 때문에, 기준 브랜치의 커밋을 대상 브랜치 commit      

      으로 이동하는 의미입니다.

![https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile4.uf.tistory.com%2Fimage%2F99F2C13D5B8915132D814A](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile4.uf.tistory.com%2Fimage%2F99F2C13D5B8915132D814A)

- 페치 ( fetch )

      pull을 실행하면, 원격 저장소의 내용을 가져와 자동으로 병합작업을 실행하게 됩니다. 그러나 

      단순히 원격 저장소의 내용을 확인만하고 로컬 데이터와 병합을 하고 싶지 않은 경우에는 fetch   

      명령어를 사용할 수 있습니다. fetch를 실행하면 원격 저장소의 최신 이력을 확인할 수 있습니다.

- 헤드 ( head )

      브랜치의 제일 앞에 있는 커밋을 가르키는 레퍼런스를 불느느 이름입니다. 헤드는 각 레포짓토리      

      의 폴더에 저장되어 있습니다.

- 헤드 ( HEAD )

      현재 작업중인 브랜치를 말합니다. HEAD는 항상 작업트리의 가장 최근 커밋을 가리킵니다. 작업

      트리에 변화를 주는 git 명령어들은 대부분 HEAD를 변경하는 것으로 시작합니다.

- 풀 ( pull )

      브랜치를 풀 하는 것은 브랜치의 내용을 패치를 통해서 최신 이력을 가져온 후, 현재 체크아웃된 

      브랜치와 합치는 것을 뜻합니다.

- 푸시 ( push )

      로컬의 수정 데이터를 원격 저장소에 저장하는 것을 말합니다.  로컬 저장소에서 원격 저장소로 

      push 할 때에는 push 한 브랜치가 fast-forward 병합 방식을 처리 되도록 지정해둘 필요가 있습니다.

- 머지 ( merge )

       머지는 각각 분기된 커밋을 하나의 커밋으로 다시 합치고 싶을 때 사용하는 명령어다.

       만약 A 팀원과 B 팀원이 작업을 했으면, Master 브랜치에는 두명의 수정사항이 모두 반영되야 

       합니다. 이럴 때 merge를 통해서 커밋을 합쳐서 반영할 수 있습니다.

- 리베이스 ( rebase )

       리베이스는 말그대로 베이스를 재배치 하는 뜻입니다. merge를 사용하면 히스토리를 볼 때 갈      

       래가 여러개로 나뉘어서 히스토리를 찾아갈 떄 보기가 어렵습니다. rebase는 커밋의 시작점을     

       변경해서, 커밋 히스토리를 깔끔하게 작성 할 수 있습니다.

![https://media.vlpt.us/post-images/godori/b9224b40-b160-11e9-9a9a-0f3d00cfbaf3/image.png](https://media.vlpt.us/post-images/godori/b9224b40-b160-11e9-9a9a-0f3d00cfbaf3/image.png)

- 충돌 ( Conflict )

       git 에서 변경한 부분을 자동으로 통합해주는 기능입니다.  그러나 경우에 따라서 자동으로 병합

      할 수 없는 경우도 있습니다. 이럴 경우 충돌이 발생한 경우 변경 내용 중 어느쪽을 저장할 것인지    

      자동으로 판단할 수 없기 때문에 사용자가 직접 수정해줘야 합니다.

### 3. 기본 명령어 / 자주 쓰는 명령어

- 저장소 생성

```jsx
git init
```

- 원격 저장소로부터 복제

```jsx
git clone {url}
git clone https://github.com/conventional-commits/conventionalcommits.org
```

- **변경 사항 체크**

```jsx
// 브랜치 정보와 stage에 올라온 변경사항을 알수있다
git status
```

- **파일 스테이징**

```jsx
// 특정파일 스테이징
$ git add 파일명
$ git add src/main/resources/egovframework/properties/system.properties

// 변경된 모든 파일 스테이징
$ git add * or git add .

// 전체파일 add 취소
$ git reset 

// 특정 파일 add 취소
$ git reset HEAD 파일명.확장자 
```

- **원격으로 보내기**

```jsx
$ git push origin master
```

- **원격저장소**

```jsx
// origin 원격저장소 추가
$ git remote add origin 주소
$ git remote add origin https://github.com/choiwono/git-guide

// 원격저장소 origin 삭제
$ git remote rm origin

// 원격저장소 확인
$ git remote

// 원격저장소 상세정보
$ git remote -v
```

- **Commit**

```jsx
// 커밋 합치기
$ git rebase -i HEAD~4 

// 커밋 메시지 수정
$ git commit --amend

// 간단한 commit 방법
$ git add 변경한 파일명
$ git commit -m "변경 내용"
```

- **Commit 이력확인**

```jsx
// 커밋 이력 확인
// 모든 커밋로그 확인
$ git log 

// 최근 3개 커밋로그 확인
$ git log -3

// 각 커밋을 한 줄로 표시
$ git log --pretty=oneline

// reset 혹은 rebase로 없어진 과거의 커밋 이력 확인
$ git reflog
```

- **Commit 취소**

```jsx
// 마지막 커밋 삭제
$ git reset HEAD^

// 마지막 2개의 Commit을 취소
$ git reset HEAD~2

// 마지막 커밋 상태로 되돌림
$ git reset --hard HEAD

// 스테이징을 언스테이지응로 변경, ref
$ git reset HEAD *
```

- **Branch**

```jsx
// 현재 브랜치 + 대상브랜치를 병합시킴
$ git merge 대상브랜치이름

// 브랜치 목록
$ git branch ( 로컬 )
$ git branch -r ( 리모트 )
$ git branch -a ( all )

// 브랜치 생성 ( master -> new 브랜치 )
$ git branch new master

// new 브랜치를 리모트로 보내기
$ git push origin new

// 빈 브랜치 생성
$ git checkout --orphan new-branch ( 커밋과 동시에 새로운 브랜치생성 )
$ git commit -a ( 커밋을 먼저 해야 브랜치를 생성할 수 있다 )
$ git checkout -b new-branch ( 브랜치 생성과 동시에 체크아웃 )

// 리모트 브랜치 가져오기
$ git checkout -t origin/가져올 브랜치명

// 브랜치 이름 변경
$ git branch -m 새이름
```

### 4. 브랜치 전략

1. Git flow 전략

      -

### 5. 커밋 히스토리의 중요성, 태그 사용해보기

### 6. 커밋 메시지 가이드

#### ✉️ Commit Message

commit 메시지를 어떻게 쓸것인가에 대한 간단한 가이드

#### 커밋 메시지가 중요한가요?

- 코드 리뷰 시간을 단축하고 능률적으로 처리하기 위함
- 변경 사항을 이해하는데 도움을 주려고
- 코드만으로 설명이 어려운 how to를 설명하기 위해서

#### 어떻게 커밋을 작성하는게 좋을까요?

**모두가 동일한 규칙을 지킨다**

이슈관리 툴은 어떤걸 사용해도 상관없습니다  ( Jira, GitLab 등등 )

- 작업을 시작하기전에 미리 이슈등록을 합니다
- 하나의 이슈에 대해서 되도록 하나의 커밋으로 처리합니다.
- 자신의 Pull Request는 스스로 merge 합니다.

**명확한 어투 사용**

```jsx
🥰 좋음!

Refactor() 함수을 사용하여, 기존에 중복되었던 
코드를 리팩토링 처리합니다

😭 나쁨!
Refactor() 함수을 사용하여, 기존에 중복되었던 
코드를 리팩토링 처리했습니다
    
```

**소스코드를 보지 않고 변경사항을 알 수 있도록 하기**

```jsx
🥰 좋음!

텍스트 상자와 레이아웃 프레임 사이 왼쪽 간격 늘림
학습모델 상세팝업 화면을 MediaQuery를 사용하여, 반응형 처리

😭 나쁨!

CSS 조정**
학습모델 상세화면 개선
```

**커밋 메시지 본문으로 "왜", "무엇", "어떻게" 변경했는지, 상세 내용 추가 설명하기**

```jsx
🥰 좋음!

알림창 라이브러리(sweetAlert) 버전 업그레이드

sweetAlert 1 최신 버전 적용 ( 1.2.1 )
- 버전 문제로 인하여 동기화 문제가 있었음 
- 새로운 버전은 Promise 패턴과 async await 패턴 적용 가능

```

**맥락없는** **메시지 사용 자제하기**

```jsx
😭 나쁨!

이거 고침, 저거 고침
버그 수정
버전 업그레이드
요렇게 수정함, 저렇게 수정함
```

**행과 글자수 제한하기**

제목은 50자, 본문은 72자로 한줄에 들어갈 수 있는 글자 수를 제한하는것이 권장됩니다.

제목으로 어떠한 작업을 했는지 유추가 가능해야 합니다.

#### 🎲 Conventional Commits을 적용해보자!

Conventional Commit 스펙은 명확한 커밋 히스토리를 생성하기 위한 간단한 규칙을 제공하기 위해서 만들어진 규칙입니다.

```jsx
<타입>[적용 범위(선택 사항)]: <설명>

[본문(선택 사항)]

[꼬리말(선택 사항)]
```

💡 **Commit Type**

커밋 메시지 제목에 접두사로 의도를 파악할 수 있습니다.

- fix : 버그 패치
- feat : 새로운 기능 추가
- refactor! : 리팩토링
- docs : 문서파일 수정 ex) Readme.md
- style : 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우
- test : 테스트 코드, 리팩토링 테스트 코드 추가
- chore : 빌드 업무 수정, 패키지 매니저 수정

**Example**

```jsx
fix : swal 알림창 버전 문제로 인한 코드 수정

기존 코드 A에서 코드 B로 변경

// 코드리뷰가 필요한 경우
Revieweb-by : @javapark

// 이슈번호 참조
Refs #32 
```

#### 😊 Emoji를 활용해보자

commit 타입을 붙이지 않고, Emoji를 통해서 커밋 타입을 분류할 수 있습니다.

[Emoji CheatSheet](https://www.notion.so/ca168a7bbff54ef4be8e2514823ac9e8)

**Example**

```jsx
// raw 코드를 입력하면 emoji를 지원하는 경우 자동으로 아이콘으로 변경됩니다

🔥 사용하지 않는 v2버전 jsp 파일 제거

- 현재 UI 버전에서 v2 관련 폴더는 사용하지 않으므로 제거함 

Refs #33
```

#### 🎲 Gitlab 에서 커밋과 같이 issue를 닫아보자

**종료 Keyword**

- close
- closes
- closed
- fix
- fixes
- fixed
- resolve
- resolves
- resolved

Commit 메시지에 키워드를 지정하게 되면 이슈넘버 ( #33), closed( 종료 키워드) 가 있기 때문에 

push할 경우 #33번 이슈가 종료되고 push가 완료됩니다.

**Example**

```jsx
🔥 사용하지 않는 v2버전 jsp 파일 제거

현재 UI 버전에서 v2 관련 폴더는 사용하지 않으므로 제거함 

closed #33

Refs #33
```

또한 한 커밋에 여러개의 이슈 넘버가 있는 경우 같이 종료 할 수 있습니다. 

( rebase로 커밋을 합친경우 )

**Example**

```jsx
🔥 사용하지 않는 v2버전 jsp 파일 제거

현재 UI 버전에서 v2 관련 폴더는 사용하지 않으므로 제거함 

closed #33, #34, #35

Refs #33
```

#### **출처**

[https://doublesprogramming.tistory.com/256](https://doublesprogramming.tistory.com/256)

[https://www.conventionalcommits.org/ko/v1.0.0/](https://www.conventionalcommits.org/ko/v1.0.0/)

[https://www.hahwul.com/2018/07/closing-git-issue-with-commit.html](https://www.hahwul.com/2018/07/closing-git-issue-with-commit.html)

[https://github.com/carloscuesta/gitmoji-cli](https://github.com/carloscuesta/gitmoji-cli)


### 7. Rebase vs Merge 전략

### 8. 배포 전략

### 9. 유용한 사이트, 참고 링크
