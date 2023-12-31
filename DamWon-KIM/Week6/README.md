#### [github actions] [생활코딩] 강의

### action이란?

actions 안에 들어가면 list가 나오게 되는데, CI라고 적힌 것이 글쓴이가 만든 action이다.
사용자가 push와 같은 작업을 했을 때, 컴퓨터가 새로 생성되고,
생성된 컴퓨터에서 업무일지를 작성하는 서비스인 air table이라는 서비스로 자동으로 작업을 적어주는 action이다.

git commit -am "add multiply 1h"
git push
로 업로드 시작이 되면
Actions를 리로드하면 커밋이 등록되어있고 지금 구동중이라는 것이 화면에 보인다.
작업이 끝나게 되면 커밋한 내용이 깃허브액션의 runner라는 가상머신에서 구동되서 누가 작업했고, 어떤 작업이었고, 몇시간 일했고 그 업무는 어떤 내용에 대한 것인지 커밋과 
그것에 대한 근거자료에 대한 깃허브 링크가 자동으로 업로드 되는 것을 볼 수 있다.

업무에 방해가 되지 않게 개발자들이 하는 일에 대한 업무를 추적하는데 굉장히 큰 도움을 받을 수 있다.

### 어떻게 action을 사용하는 가

  Create a new reposiotory </br>
  action-tutorials : Repository name </br>
  Public </br>


  Actions 탭으로 들어가면 깃허브에서 제공하는 미리 만들어진 템플릿 action들을 선택할 수 있다. </br>
  Set up a workflow yourself </br>

  action-tutorials/.github/workflows/main.yml : action의 실체이다. </br>

```
name : Hello World :action name"

on : [push] "사용자가 commit했을 때 및의 코드들이 실행이 된다" "[push, pull_request]"

jobs:
  build:

    runs-on: ubuntu-latest "action이 실행됬을 때 구분되는 컴퓨터가 ubuntu였으면 좋겠다"

    steps:
    #- uses: actions/checkout@v2 "#은 해당 줄이 구동되지 않게 주석처리"
    - name: Run pwd "우분투 - 현재 사용위치 알려주는 명령어 run에 대한 step의 이름"
      run: pwd
    - name: Run ls -al
      run: ls-al

```

start commit을 누르면 Create main.yml이 만들어짐 </br>
Commit new file </br>

저장소 안에 </br>
.github/workflows 폴더 안에 main.yml 파일이 위치하게 된다. </br>

yml이라는 확장자를 가지고 있는 설정파일을 만드는 작업을 한 것 </br>

Clone or download : git clone해서 저장소 복제 한 후 폴더 안에 들어가보면 파일 안에 파일들이 생성된 것을 확인할 수 있다. </br>

<버전 수정 후 commit, push 해 보기> </br>

vim main.html
```
<html>
    <body>hi</body>
</html>
</html>
```
git commit -am "hi"
git push

Actions에서 일어나는 일

```
Run pwd "step에서"
/home/runner/work/action-tutorials/action-tutorials  "이런 디렉토리 구조를 가지는 컴퓨터를 우리에게 빌려주었다는 뜻"
```

push, pull request, issue작성 여러가지 사건들이 일어났을 때 github에게 우리가 컴퓨터를 빌려서 자동으로 처리할 수 있다는 것을 보여준다. </br>

Run ls-al 은 아무것도 없는 깡통 컴퓨터 </br>

### github가 runner를 빌려줄 때 컴퓨터 안에 action이 실행한 저장소의 github 소스코드가 체크아웃이 되게 하는 방법
New workflow 클릭 </br>
Set up a workflow yourself 클릭 </br>
github-checkout.yml </br>

```
name: github checkout

on: [push]

jobs:
  build:

  runs-on: ubuntu-latest

  steps:
  - uses: actions/checkcout@v2 "주석처리 해제" "다른 사람이 만든 action을 실행하고 싶을때, uses란 키워드를 사용"
   "github.com/actions/checkout 이 저장소가 checkout이라하는 action의 저장소이고, github에서 만든 것" 
  - name: Run a one-line script
    run: pwd
  - name: Run ls -al
    run: ls -al

```

오른쪽 Marketplace에 todo라고 검색 시, todo-actions </br>
* TODO : 지금은 못하지만 언젠가 해야 한다고 표시를 하는 것으로, 저장소에 도착하게 되면 자동으로 이슈를 발급해줌 </br>
* TODO 주석을 삭제시, 이슈를 클로즈 시켜주는 기능을 가지는 action이다. </br>

* actions/checktout - runner를 만들 시 기본적으로 깡통인 것을, action이 실행되고 있는 저장소를 클론하고 체크아웃해서 </br>
  다음에 나오는 명령어들에서 사용할 수 있도록 해주는 action이다. </br>


Start commit </br>
Commit Changes </br>
git pull -> 지금 생성된 github checkout yml 파일이 다운된다 </br>

vim main.html </br>
hi 입력하고 </br>
git commit -am "update hi checkout" </br>

Run ls -al에서 </br>
.git, .github, main.html으로 이전과는 다르게 현재 우리가 보고 있는 저장소가 runner에 checkout 되었음을 볼 수 있다. </br>

  ** runner에 있는 저장소를 이용해서 여러가지 작업을 처리할 수 있게 된 것 </br>

  runner가 구동된 시점에서 여러가지 상태정보 </br>
  어떤 맥락, 문맥에서 실행됬는지 알게 해 준다 - context, 환경변수라 한다. </br>

## github action variable context
Contexts and expression syntax for GitHub Actions </br>
github에서 제공하는 여러가지 환경변수들 </br>
어떤 버전으로 인해서 이루어졌는가 </br>
github.actor </br>
github.repository </br>
github.sha </br>

New workflow </br>
action-tutorials/.github/workflows/main.yml </br>

### 환경변수 주입시 env

```
name: CI

on: [push]
 
jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - name: "context"
      env:
        CMMIIT_ID: ${{ github.sha }}
      run: echo "Commit id ==> $COMMIT_ID"
```

runner를 동작시킬 때, context를 잘 활용해서 여러가지 복잡한 작업을 처리할 수 있다.

### secret 정보
password 정보를 action에 넣으면 소스코드에 노출되어 안된다.
그런면에서 필요한 것이, secret

Settings - Secrets 들어가면
Add a new secret
Name : ASSWORD
Add Secret

action으로 가서 New workflow 생성 시 

```
name: CI

on: [push]

jobs:
  build:

  runs-on: ubuntu-latest

  steps:
  -name: Print Password
   env:
      MY_PASSWORD: ${{secrets.PASSWORD}}
   run: echo My password is $MY_PASSWORD
```

password.yml
commit new file
action이 동작한 것을 찾아서 Actions-CI - Create password.yml- build 부분 Print Password 볼 시, 아까 짠 코드에 의해서
비밀번호가 ***로 출력이 된다.
보안에 이슈가 생기는 것을 방지할 수 있다.

이후로 action에 어떤 event들이 있는지, 어떤 환경변수들 "variables"이 제공되는지, action이 시작되었을 때,
어떻게 하면 node.js와 python에서 복잡한 일을 처리할 수 있는지 찾아보면 좋다.
나만의 action 뿐 아니라, 다른 사람들도 사용할 수 있는 보편적인 action을 만들어서 조직을 위해 공개를 하는 것도 좋겠다.
