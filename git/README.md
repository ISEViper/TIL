# Git 기본 명령어

1. git 저장소로 초기화
```bash
git init
```

2. git에 파일을 추가할 준비 (staging area로 이동)
```bash
git add "파일명"
```

3. staging에 있는 내용 기록
```bash
git commit -m "메시지"
```

4. 현재 변경사항 내역 + staging area 표시
```bash
git status
```

5. 현재까지 변경사항 확인
```bash
git log  
git log --oneline #만약에 간단하게 보고 싶은 경우
```

6. git global 설정 상황 보기
```bash
git config --global -l
```

7. git commit 내용 중 수정 사항이 있는 경우 (권장하지는 않음)
```bash
git commit --amend
```
