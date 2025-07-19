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
>(2) [브랜치 이름] 내용으로 수정  
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
# git revert/reset

1. git revert  
git에 `commit`한 내용을 삭제하는 것이 아닌 기존 `commit`을 유지하되 이전의 상태로 되돌리는 명령어
```bash
git revert <commit_id>
```
사용한 경우 이전 커밋 내용은 남아있고 `revert commit_내용`으로 다시 새로운 커밋이 형성

2. git reset  
git에 `commit`한 내용을 지우는 명령어 (프로젝트를 진행할 때에는 자주 사용하지 않는 것이 좋음!)
- git reset의 3가지 종류
```bash
git reset --soft <commit_id>
```
git에 커밋한 내용을 staging area로 되돌리는 `reset`
```bash
git reset --mixed <commit_id>
```
git에 커밋한 내용을 working directory로 되돌리는 `reset`
```bash
git reset --hard <commit_id>
```
git에 커밋한 내용을 삭제하는 `reset`
# gitignore
Git에서 특정 파일이나 디렉토리를 추적하지 못하도록 설정하는데 사용되는 텍스트 파일
```bash
.gitignore # 이 텍스트 파일 안에 추적을 원하지 않는 파일명을 적으면 된다.
```
[gitignore.io](https://gitignore.io) -> gitignore에 필요한 파일이나 디렉토리를 미리 만들어주는 사이트

> 단, 파일이 이미 git에 등록이 되어 있는 경우 gitignore에 넣어도 추적이 된다. -> git이 이미 추적을 하고 있기 때문에 나중에 넣어도 소용이 없다.

> gitignore은 프로젝트 시작 시에 설정하는 것이 좋다.
