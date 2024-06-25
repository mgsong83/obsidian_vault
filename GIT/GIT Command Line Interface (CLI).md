

`git commit`  : 로컬 리포지터리에 change 를 저장
`git commit -m "message"` : 메세지를 포함해서 commit 진행 


`git log` : log 보기
`git push origin master` : **origin**(repository) 의 **master**(branch)에 '**현재**'상태를 push 함


`git add filename` : filename을 staging area 에 추가 (추적 시작)
`git add .`  :  현재 dir 의 모든 파일을 staging area 에 추가


----

다른 version으로 돌아가고 싶을 때
(HEAD) --> 현재 내가 보고있는 파일

`git checkout version-hash`  다른 버전으로 가기

과거 커밋으로 가면, 그 당시 상태가 되기 때문에 그 이후가 보이지 않음, 다시 top으로 돌아오고 싶으면 

`git checkout master` 

로 돌아올 수 있음



그럼 최신 버전을 지우고 전 버전으로 돌아가는 방법?

1) git reset 을 사용 

`git reset --hard HEAD`

`git reset --hard HEAD^`  과거 1개 전으로 돌아감

`git reset --hard HEAD^^` 과거 2개 전으로 돌아감


이렇게 하면 본인의 로컬에서는 과거 2개전으로 돌아가지만, origin 에서는 최신 버전까지 남아있는 상태이기 때문에 다음의 명령어를 사용해서 강제로 푸쉬해야함

`git push origin master --force`


만약 hard option 을 사용하지 않는 경우 (soft reset)

`git reset --soft HEAD^`  이렇게 하면 soft reset 

`git reset HEAD^` 이렇게 하면 mixed reset 임


mixed reset -> 커밋 한 변경사항이 다시 unstaging area로 돌아감. (파일은 수정되었으나 반영하지는 않는 상태)

hard reset -> 파일 자체를 수정(삭제) -> 그 당시 상태로 완전히 돌아감.


reset을 해서 origin  과 local 이 다른 경우 

`git pull origin master`  을 한 경우 코드 충돌이 나기 때문에 conflict 를 풀어주고 커밋한 뒤에 푸쉬를 해야함


`git reset HEAD^^ --soft`  : 섞이지 않고 리셋하고 싶을 때 사용


**정리 

hard - 파일을 삭제 
soft - 파일을 남김
mixed - 파일을 삭제하진 않지만 unstage 시킴 (일방적으로 선호됨)


 
---- 

`git log` 에서 돌아가고 싶은 상태의 hash를 기억하고 다음의 명령어를 사용해서 돌아갈 수 있음

`git checkout #hash#`

단 이렇게 돌아가면 detached HEAD 상태가 됨(여기서 무언가를 고쳐도 미래가 영향받지 않게 하기 위해서..) 다시 돌아가기 위해서는

`git checkout master `

로 돌아갈 수 있음


`git checkout -b NAME` : branch 를 만들기


`git branch` 로 만들어진 branch 확인 가능

----

따라서 과거로 돌아가서 새로운 브랜치를 따고 싶다면

1. `git log` 로 과거로 돌아가고 싶은 시점 확인
2. `git checkout ###` 으로 돌아가기 (Detach 됨)
3. `git checkout -b new-branch-name` 으로 새 브런치 따기 (새로운 브랜치에 합류)


이걸 간단하게 한줄로

`git checkout #### -b NAME`  으로 할 수 도 있음


----


브랜치 삭제

`git branch -d NAME`




----

이미 올린 커밋 수정하는 방법 (파일을 추가해야하거나, 메세지 수정해야할 때)


1. `git add .`
2. `git commit -m 'wrong version'`
3. `git push origin master`

와 같이 이미 커밋 후 푸쉬까지 한 경우 수정이 필요한 경우

amend 를 할 수 있다 :

`amend` : **가장 마지막 커밋**을 수정
\

`git commit --amend --no-edit`  : 메세지 없이 수정 사항만 반영


----

`git status` : git 관리중인 파일들의 stage 레벨에서 차이를 확인

`git remote -v` : 외부 저장소 리스트로 보기

`git removte add qq urls `

이러면 urls 에 해당하는 저장소가 qq 라는 이름으로 추가된다.

`git remote remove qq`  하면 qq 가 지워진다.

`git push "remote name" "branch name"`  이게 푸쉬 하는 기본적인 문법이다.





























