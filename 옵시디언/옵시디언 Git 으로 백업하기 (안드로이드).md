


[[옵시디언을 Git 으로 백업하기(데스크탑)]]에서 이어짐


다만 모바일에서의 옵시디언 Git 사용은 매우 불안정하며, 추천하지 않는다는 개발자의 말이 있으므로, 가급적이면 하지 않는 것을 추천

https://github.com/denolehov/obsidian-git 개발자 리포지토리에서 아래 문구가 사라질 때 까지 기다리자. 
![[Pasted image 20240618174618.png]]


![[Pasted image 20240618174517.png]]


**핸드폰에서 Obisidan 동기화를 위해서는 다음의 것들이 필요하다!**

Step-by-Step 으로 따라올 것.


1. 먼저 git 설정을 위해 Termux 와 같이 안드로이드 폰 자체에서 Command line 사용이 가능한 터미널을 설치한다.


2. 패키지 업데이트와 업그레이드를 진행한다.

```
pkg update
pkg upgrade
```

3. termux 에서 안드로이드 내부 스토리지가 접속 가능하도록 설정한다. https://wiki.termux.com/wiki/Termux-setup-storage 

```
termux-setup-stroage
```
  
이후 안드로이드 버전에 따라서 권한설정을 해줘야 할 수 있음 


4. termux 의 다음의 위치로 가서 git repo 공간을 만들기

``` 
cd ~/storage/shared/<원하는 디렉토리>
git clone <내 Repo 이름>
```


단, 현재 버전에서는 아래와 같이 https auth 를 진행할 수 없기 때문에 (gh 로는 또 된다는 [포스트](https://forum.obsidian.md/t/guide-using-git-to-sync-your-obsidian-vault-on-android-devices/41887)도 있었으나, 해보지는 않음) 

![[Pasted image 20240618175020.png]]

 https 로 이루어진 git 프로토콜을 써야한다.
 
5. Git Hub 에서 personal token  을 발급한다. (인증을 위한 비밀번호)  

![[Pasted image 20240618170829.png]]
  프로필 -> 설정 -> 개발자설정 -> Create Token 에서 설정할 수 있다. 이후 토큰의 유효기간은 무제한으로 (기본으로는 30일), 그리고 repo에 대한 모든 권한을 준 다음에 발급하고 나오는 Key pharse 를 잘 적어두도록 하자. (token 유형은 classic 으로 해야한다!)


 6. 핸드폰에 obsidian 을 설치하고, 처음 시작시 open exisit folder 를 방금 clone 한 위치로 지정한다. 
 
 7. 커뮤니티 plug-in 을 사용함으로 바꾸고, Git 을 설치 & 사용함으로 설정
 
 8. 자동 백업항목에서 Commit / Push / Pull 시간을 각각 설정하고, Auth 항목에서 github 아이디와 token 정보를 입력한다. 

