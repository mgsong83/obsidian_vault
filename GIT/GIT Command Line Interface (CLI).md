

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


mixed reset -> 커밋한 변경사항이 다시 unstaging area로 돌아감. (파일은 수정되었으나 반영하지는 않는 상태)

hard reset -> 파일자체를 수정(삭제) -> 그 당시 상태로 완전히 돌아감.


reset을 해서 origin  과 local 이 다른 경우 

`git pull origin master`  을 한 경우 코드 충돌이 나기 때문에 conflict 를 풀어주고 커밋한 뒤에 푸쉬를 해야함




















