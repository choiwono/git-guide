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

      push 할 때에는 push 한 브랜치가 fast-forward 병합 방식을 처리 되도록 지정해둘 필요가 

     있습니 다.

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

### 7. Rebase vs Merge 전략

### 8. 배포 전략

### 9. 유용한 사이트, 참고 링크
