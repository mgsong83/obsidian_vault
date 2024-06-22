

 .gitignore 파일이 git 으로 관리되는 파일에 있을 경우
그 안에 명시되어 있는 파일들은 git 에 추가되지 않음


문법

```bash 
test.txt  #파일
/images  #폴더
```


만약 이미 파일이 올라 가버린 경우에 삭제할 때에는


`git rm -r image/ --cached`

처럼 cached 된 것 까지 지워야 싹 사라짐.