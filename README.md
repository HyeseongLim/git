# Git
자주 사용하는 명령어에 대한 설명과 예시 및 이미지를 보여줍니다.
잘못된 설명이 있거나 보완점 및 추가할 정보가 있다면 수정해주세요.

## 주의사항
1. Git의 모든 명령어는 Case-Insensitivity이고 옵션의 경우 Case-Sensitivity입니다.

2. Git Local-Repository의 Configuration은 Directory기반입니다. 현재 Directory를 확인해주세요.

3. README를 지속적으로 갱신해주세요.

4. Command 사용 후 정보의 출력이나 입력, 삭제 등 동작이 필요할때 단축키는 VI, VIM 등 에디터와 대부분 같습니다.

5. 해당 자료에서 중괄호 {keyword} 는 입력해야할 정보, 대괄호 [-d, keyword]는 선택사항으로 표기합니다.

6. Commad의 option은 여러개를 같이 사용할 수 있습니다

   ```
   ex) git commit -am "message" === git commit -a -m "message"
   
   ```

   

## Keywords
필요한 개념, 키워드 등의 설명을 적어주세요.



`Repository`
코드 및 파일이 저장되는 저장소를 뜻합니다. Remote (원격) / Local  두 가지로 나뉩니다.

`Staging / Add`
변경사항을 저장하는 행위를 뜻합니다. 저장된 변경사항을 기록(Commit)하기 위함이며 변경사항에는 파일의 삭제 및 추가, 수정 등 모든 작업에 해당합니다.

`Index / Staging area`
Add 한 파일들이 저장되는 공간입니다. 

`README`
프로젝트에 대한 개요와 설명을 작성하는 파일입니다. Markdown 문법을 사용합니다.

`Fork`
해당 프로젝트를 내 프로젝트로 복제합니다.

`HEAD`
현재 작업중인 위치를 뜻합니다.

`Branch`
작업 공간을 의미합니다. 크고 작은 Branch를 병합하는 방식으로 프로젝트를 진행합니다.

## Help
모든 명령어에서 동작하는 옵션입니다.
해당 명령어의 설명과 용법이 간략하게 기록되어있습니다.
```
git add --help 
git --help
```

## Auth
GitHub, GitLab 등 Git과 관련된 서비스에서 여러가지 사용자 인증방법이 있습니다.

1. SSH Key
2. Access Token
3. ID / Password
	
	권장되지 않은 접근방식입니다.
	Gitlab에서는 허용되고 Github에서는 보안상 접근이 제한됩니다.
	Gitlab / Github의 로그인 ID / PW를 사용하여 접근합니다.

## Shell

대부분의 운영체제에서 기본적으로 사용되는 것은 Bash Shell입니다. 
Windows에서 Git 설치 시 Git Bash가 같이 설치되고 Mac에서는 Z Shell, 그 외 Linux기반에서는 Bash Shell이 Default입니다.
다만 Linux 환경에서 동작하는 Z Shell의 Plug-in 중 `Oh-My-ZSH`이 현재 Git Repository의 Branch를 표기해주기 때문에 조금 더 직관적으로 Branch관리가 가능해집니다. 추가적으로 컬러 커스터마이징도 지원하고 있습니다.

![Oh_My_ZSH](https://github.com/HyeseongLim/images/blob/master/ohmyzsh_image.png?raw=true)



## 1. clone 

Remote Repository의 프로젝트를 복사합니다.

```bash
// folder_name 을 입력하지 않으면 해당 프로젝트의 이름으로 생성됩니다.
git clone {url} [folder_name]
```

## 2. add

변경사항이 있는 파일들을 staging 합니다.

만약 새로운 파일이라면 변경사항을 추적하도록 합니다.

```bash
// add all changed files
// under all files in current directory
git add .
git add -all
git add -A

// add a file and folder
git add ./filename.extension
git add ./foldername/
ex) git add ./text.java
ex) git add ./Controller/UserController.java
```

## 3. commit

register a log that all change files in staging area to local repository

-a : 추적상태인 파일들을 모두 staging area에 이동시킨 후 commit 합니다. 새로 생성한 파일의 경우 추적상태가 아니라면 반영되지 않습니다.

  ```	
  // commit with message
  // require a pair of double quote
  git commit [-a, -m] "message"
  ex) git commit -am "commit"
  ```



## 4. remote

  Remote Repository의 주소를 저장(Alias)합니다.

  Token 및 ID / PW 인증의 경우 URL을 `HTTPS`로 SSH KEY를 통한 인증의 경우 `SSH`로 등록하여야 합니다.

  ```
  // show all remotes
  git remote
  
  // add remote 
  git remote add {alias} {url} 
  ex) git remote add origin https://github.com/HyeseongLim/git
  
  // rename remote
  git remote rename {origin_name} {to_change}
  
  // delete remote
  git remote rm(or remove) {remote_name}
  
  // get or set remote url
  git remote get-url(or set-url) {target}
  ```

## 5. push

  현재 Branch의 Commit을 Remote Repository에 Push(저장)합니다.

-u : 스트림을 연결합니다. 한 번 연결되었으면 remote name과 branch name을 생략할 수 있습니다.

  ```
  // -u (upstream): set stream connection -u : 스트림을 연결합니다. 한 번 연결되었으면 remote name과 branch name을 생략할 수 있습니다.
  git push [-u] {remote alias} {branch}
  ex) git push -u origin master
  
  // delete branch at Remote Repository
  git push origin --delete {branch_name}
  ```



## 6. fetch

Remote Repository에 있는 Commit된 Data를 Local Repository로 가져옵니다.

데이터는 `FETCH_HEAD` 라고 명명된 Branch에 저장됩니다.

저장되는 Branch의 이름은 다를 수 있으니 Log를 확인하여 사용해주세요.

아래 이미지에서는 Commit ID가 35dc93d .. 로 시작하는 origin/master 로 저장되었습니다.

  ```
  git fetch {remote_name}
  ex) git fetch origin
  ```
  ![enter image description here](https://github.com/HyeseongLim/images/blob/master/git_fetch.png?raw=true)

## 7. merge

  서로 다른 Branch를 현재 HEAD를 기준으로 Merge(병합)합니다.

  병합의 결과는 새로운 Commit으로 생성됩니다.

  ```
  git merge {branch_name}-u : 스트림을 연결합니다. 한 번 연결되었으면 remote name과 branch name을 생략할 수 있습니다.
  ```
  **// 자세한 설명 추가**

## 8. pull

  fetch와 merge를 동시에 진행합니다.

  Remote Repository에서 변경사항을 새로운 Branch로 받아와 해당 Branch로 Merge 합니다

  ```bash
  git pull origin master
  ```

## 9. branch

  Branch를 관리합니다.
  ```
  // show all branchs
  git branch
  // create a new branch
  git branch {branch_name}
  // delete a branch  
  git branch -D {branch_name}-u : 스트림을 연결합니다. 한 번 연결되었으면 remote name과 branch name을 생략할 수 있습니다.
  ```

## 10. checkout

  작업할 Branch를 변경하고 특정시점의 Commit으로 이동할 수 있습니다.

  HEAD를 이동하기 때문에 과거의 Commit으로 이동하여도 Commit은 삭제되지 않고 다시 돌아갈 수 있습니다.

  ```
  git checkout {branch_name}
  git checkout {commit_ID}
  ```
  - Branch 이동과 Commit ID를 사용한 Commit 이동 
    ![enter image description here](https://github.com/HyeseongLim/images/blob/master/git_checkout_1.png?raw=true)

  - Commit 이동 후 복귀 
    ![enter image description here](https://github.com/HyeseongLim/images/blob/master/git_checkout_4.png?raw=true)

## 11. reset

`git reset HEAD^` 
undo recent commit and committed files are unstaged

`git reset --hard commit_id`
cancle before commit id, all committed files are unstaged

## 12. revert

## 13. status

Commit되지 않은 File들의 상태를 출력합니다.

세 가지 영역 Staged, Unstaged, UnTracked 으로 나뉘며 해당 파일의 상태(new file, modified, deleted, etc..)또한 같이 표기됩니다.

-s : 파일들의 상태를 간략하게 출력합니다.

```
git status
```
![enter image description here](https://github.com/HyeseongLim/images/blob/master/git_status.png?raw=true)

## 14. log

프로젝트의 모든 Commit의 정보를 보여줍니다. 출력되는 기본 정보는 아래와 같습니다.
- Commit ID
- Branch HEAD
- Author
- Commited Date
- Commit Message

```
git log
```


![enter image description here](https://github.com/HyeseongLim/images/blob/master/git_log.png?raw=true)

## 15. cherry-pick

## 16. cache

## 17. diff

변경된 파일의 내용을 비교합니다.

수정했지만 아직 staged되지 않은 파일과 staged 파일과 비교합니다.

--staged : Commit 된 파일과 staged 파일과 비교합니다.

```
git diff
```

## 18. rm

## 19.

## 20.

## 21.

## 22.





## Pull Request / Merge Request

Github에서는 Pull, Gitlab에서는 Merge Request라고 표현합니다.

본인이 작업한 결과 ( Branch A )를 특정 Branch ( Branch B )에 병합요청을 보냅니다.

요청의 승인은 권한이 있는 사용자만 허가할 수 있습니다.

일반적으로 기능개발자에게 Merge와 Push 권한을 부여하지 않고 프로젝트 관리자가 Pull Request를 허가하는 방식으로 프로젝트를 진행합니다.

대략적인 진행사항은 아래와 같습니다.

1. 진행할 프로젝트를 Fork합니다.
2. 복제된 프로젝트를 수정하고 복제된 내용을 Add / Commit / Push 합니다.
3. 2.의 Branch를 메인 프로젝트의 저장소의 특정 Branch로 병합 요청을 합니다. 이 때 변경사항에 대해 자세한 설명을 남깁니다.
4. 프로젝트의 관리자가 병합요청을 리뷰하고 승인 / 거절합니다.



## .gitignore

프로젝트 내 최상위 Directory, 즉 Git이 설정된 곳에 위치합니다.

환경설정 및 Key, Password, API 등 외부에 공개하면 안되는 파일들을 등록할 수 있고, 등록된 파일들은 Git Command의 대상에서 제외됩니다.

작성 규칙은 아래와 같습니다.

- 아무것도 없는 라인이나, `#`로 시작하는 라인은 무시한다.
- 표준 Glob 패턴을 사용한다. 이는 프로젝트 전체에 적용된다.
- 슬래시(`/`)로 시작하면 하위 디렉토리에 적용되지(Recursivity) 않는다.
- 디렉토리는 슬래시(`/`)를 끝에 사용하는 것으로 표현한다.
- 느낌표(`!`)로 시작하는 패턴의 파일은 무시하지 않는다.
