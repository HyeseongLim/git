# Git
자주 사용하는 명령어에 대한 설명과 예시 및 이미지를 보여줍니다.
잘못된 설명이 있거나 보완점 및 추가할 정보가 있다면 알려주시면 감사하겠습니다.

## 주의사항
1. Git의 모든 명령어는 Case-Insensitivity이고 옵션의 경우 Case-Sensitivity입니다.
2. Git Local-Repository의 Configuration은 Directory기반입니다. 현재 Directory를 확인해주세요.
3. 

## Help
모든 명령어에서 동작하는 옵션입니다.
해당 명령어의 설명과 용법이 간략하게 기록되어있습니다.
```
git add --help 
git --help
```

## Auth
GitHub, GitLab 등 Git과 관련된 서비스에서 여러가지 사용자 인증방법이 있습니다.
다만 조금씩 인증방식이 조금씩 다르기 때문에 모든 서비스에서 지원하는 방식인 아래 두 가지만 기술하겠습니다.
1. SSH Key
2. ID / Password

## Shell
대부분의 운영체제에서 기본적으로 사용되는 것은 Bash Shell입니다.
다만 Linux 환경에서 동작하는 Z Shell의 Plug-in 중 `Oh-My-ZSH`이 현재 Git Repository의 Branch를 표기해주기 때문에 조금 더 직관적으로 Branch관리가 가능해집니다. 추가적으로 컬러 커스터마이징도 지원하고 있습니다.

![enter image description here](https://github.com/HyeseongLim/images/blob/master/ohmyzsh_image.png?raw=true)

## Command
1. add

	move changed files and a folder to staging area
	```
	// add all changed files
	git add .
	git add -all
	git add -A
	
	// add a file and a folder
	git add ./filename.extension
	git add ./foldername/
	```
2. commit

	register a log that all change files in staging area to local repository
	```	
	// commit with message
	// require a pair of double quote
	git commit -m "message"
	```
3. remote
set or arrange url for connect to remote repository
	```
	// show all remotes
	git remote
	
	// add remote 
	// require alias
	git remote add {url} {alias}
	
	// rename remote
	git remote rename {origin} {to change}
	
	// delete remote
	git remote rm(or remove) {target}
	
	// get or set remote url
	git remote get-url(or set-url) {target}
	```
4. push
push commit log and committed files to remote repository
	```
	git push [-u] {remote alias} {branch}
	// -u (upstream): set stream connection 
	// after use at least one, no more require remote and branch name
	```
5. fetch
	
	원격저장소에 있는 Commit들을 로컬저장소로 가져옵니다.
	데이터는 FETCH_HEAD 라고 명명된 브랜치로 생성되고 merge 또는 변경사항을 확인하시면 됩니다.
6. merge
7. pull
	
	fetch와 merge를 동시에 진행합니다.
9. branch
10. reset
`git reset HEAD^` 
undo recent commit and committed files are unstaged
`git reset --hard commit_id`
cancle before commit id, all committed files are unstaged
11. revert

12. status
show changed files(not staging) and staged files
	```
	git status
	```
13. log
 
