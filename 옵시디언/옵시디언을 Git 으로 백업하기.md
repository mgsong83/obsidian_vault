

옵시디언의 가장 큰 장점중 하나는 오프라인에 설치해서 사용하는 종류의 노트 툴이기 때문에 매우 빠르고, 인터넷 연결이 없어도 사용이 가능하며 몹시 personalize 가 가능하다는 점이다. 반면에 단점도 명확한데, 그 중 하나가 동기화가 어렵다는 점.

이를 위해서 Obsidian Sync 를 제공하고 있기는 하나, 이는 유료서비스이기 때문에 많은 사람들이 클라우드 서비스 (대표적으로 [[구글드라이브]], [[Dropbox]]) 를 사용하고 있다. 

하지만 꼭 이런 클라우드 서비스가 아니더라도 쉽게 동기화 가능하며, 플러그인을 제공하는 방법이 있는데 그 중 하나가 [[Git & Git Hub]] 을 활용한 동기화이다. 


처음 셋팅만 할 수 있다면 굉장히 간단하고 자동으로 백업을 해주므로 한 번 도전해보는 걸 추천 

----



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


3) github 과 연결하기

이제  local git 을 remote 와 동기화 시켜주면 된다.

```git
git remote add origin https://~~~~ 
```

저 물결은 github 에서 제공하는 repository 주소로 https 나 ssh 어떤 걸 사용해도 상관없다. 



4) push 하기

branch 이름을 정하고, 커밋한 뒤에 리모트에 푸쉬를 진행한다.

```git
git add .
git commit -m "first commit"
git branch -M main
git push -u origin main --force
```

여기서 push 에서의 -u 옵션을 쓰면 앞으로 push 는 계속해서 origin 을 의미한다는 뜻으로(upstream의 u) 원격 저장소의 변경이력을 자동으로 연결해주는 옵션이다. 



5) Obisidian Git 플러그인 설정

이 부분은 별거 없다.  단순히 설정에 들어가서  커뮤니티 플러그인 중 Git 을 설치 & 활성화하면 끝

Config 에서 몇 분마다 자동 저장을 할 지만 결정하면 된다. (위에서 이미 git user 설정 등을 해놨기 때문에 자동으로 불러와진다.)

