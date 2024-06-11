

1) Github 에서 repository 만들기

 Github 은 기본적으로 리포지터리 생성에 별다른 제약이 없다.  심지어 별도 용량제한도 없기 때문에 단순히 new repository를 클릭하는 것 만으로도 생성 가능! 여기서 github desktop을 사용하면 좀 더 편하게 obsidian folder 를 불러와서 바로 repository로 만들 수 있지만, 굳이 desktop 을 설치하고 싶지 않다면 아래와 같은 방법으로 진행하면 된다. (만약 desktop 설치 후 local folder 를 가져오기로 한다면 2)번은 생략 가능)

![[Pasted image 20240611134738.png]]



2) obsidian vault 디렉토리에서 git 설정하기

cmd 창을 열어서 obisidian 보관소 폴더로 이동한다. 
차례로 
- 레포지토리 생성 
- 사용자 계정 셋업

```bash
cd d:\obisidan
git init
git config --local user.name mgsong83
git config --local user.email mgsong83@gmail.com
```

이후 .gitignore 파일까지 생성한다. (특히 윈도우-맥을 혼합해서 사용할 예정이라면 운영체제에서 자동으로 생성하는 파일과 obsidian 설정 파일을 ignore 에 포함시켜줄 필요가 있다.)

```git
.obsidian/

.obsidian/workspace-mobile.json
.obsidian/workspace.json
.obsidian/app.json

.trash/
.DS_Store
```


이제  l








3) 푸쉬하기
4) 
5) 