# github 주요 명령어

1. 원격 저장소에서 로컬 저장소로 끌고 오기
```bash
git remote add origin remote_repo_url
```

2. 원격 저장소에 로컬 저장소의 commit 내용 보내기
```bash
git push origin master
```
> 항상 ***add -> commit -> push*** 순으로 진행해야 한다!

>[!TIP]
>conflict가 일어나는 경우
>git을 통해 협업을 하다보면 어떤 사람이 commit을 꾸준히 하지 않아 두 브랜치의 같은 파일에 상반된 내용이 들어가 충돌이 일어나는 경우가 발생한다.
>```
> <<<<< HEAD
> Good Morning!
> =======
> Good Afternoon!
> >>>>> [브랜치 이름]
>```
>이런 경우 여러 선택지가 주어지는데,  
>(1) HEAD 내용으로 수정  
>(2) [브랜치 이름] 내용을 수정  
>(3) 아예 새로운 내용으로 수정  
>선택 후 다시 `git add [변경 파일]` 후 `git commit` -> `git push` 진행
  

3. 원격 저장소에서 로컬 저장소로 commit 내용 가져오기
```bash
git pull origin master
```

4. 원격 저장소 전체 복제 (다운로드)
```bash
git clone remote_repo_url
```

# gitignore
Git에서 특정 파일이나 디렉토리를 추적하지 못하도록 설정하는데 사용되는 텍스트 파일
```bash
.gitignore # 이 텍스트 파일 안에 추적을 원하지 않는 파일명을 적으면 된다.
```
[gitignore.io](https://gitignore.io) -> gitignore에 필요한 파일이나 디렉토리를 미리 만들어주는 사이트

> 단, 파일이 이미 git에 등록이 되어 있는 경우 gitignore에 넣어도 추적이 된다. -> git이 이미 추적을 하고 있기 때문에 나중에 넣어도 소용이 없다.

> gitignore은 프로젝트 시작 시에 설정하는 것이 좋다.
