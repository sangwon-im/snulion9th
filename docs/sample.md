# 웹의 기초

by | 재은

pub date | 2020.11.07.Sat

[웹의 기초 슬라이드](https://drive.google.com/file/d/1Jz9U_Pg_qR-oNSTR3MyeX7_s-hg-z2PQ/view?usp=sharing)

# 개발환경 세팅

## 윈도우

### 1. 파이썬 설치

https://www.python.org/downloads/ 로 가서 파이썬을 다운받습니다. 현재 가장 안정된 버전은 `3.6.8`이지만, 멋사 세미나를 진행할 때는 최신 버전을 사용하셔도 무방합니다.

다운받은 설치 파일을 실행합니다.  설치하기 전에 *Add Python to PATH*에 체크해 주세요!

![image](https://user-images.githubusercontent.com/22510942/54581003-fd0dfb80-4a4d-11e9-93ad-1b38d70dc425.png)

설치가 완료되면 cmd(명령 프롬프트)를 켜서 다음 명령어를 입력해 봅시다. (`>`는 빼고!)

```cmd
> python --version
```

방금 설치한 파이썬의 버전이 뜨면 설치가 잘 완료된 거예요!  

### 2. 가상환경 세팅

파이썬은 웹 개발 말고도 기계학습 등 다양한 분야에서 널리 쓰이는 언어입니다. 한 컴퓨터에서 파이썬을 여러 다른 용도로 사용할 경우, 이를 위해 설치한 파이썬 패키지들이 서로 충돌하는 경우가 있습니다. 이를 위해 용도별로 가상환경을 만들어서 패키지들의 충돌을 막는 것이 좋습니다. 

`virtualenvwrapper-win`은 파이썬에 내장된 가상환경 패키지인 `venv` 와 달리, 만든 가상환경의 경로를 일일이 외우고 있지 않아도 알아서 현재 작업 디렉토리와 가상환경을 매핑해 주는 파이썬 패키지입니다. 

_주의: **cmd**에서만 가능합니다. powershell에서는 작동하지 않는다고 합니다..ㅜㅜ_ [(참고)](https://pypi.org/project/virtualenvwrapper-win/)

* [cmd와 리눅스 계열 쉘 명령어 비교](ftp://archive.download.redhat.com/pub/redhat/linux/9/en/doc/RH-DOCS/rhl-gsg-ko-9/ch-doslinux.html)
* [cmd 명령어 목록](https://zetawiki.com/wiki/%EC%9C%88%EB%8F%84%EC%9A%B0_CMD_%EB%AA%85%EB%A0%B9%EC%96%B4_%EB%AA%A9%EB%A1%9D) 

`virtualenvwrapper-win`을 설치해 줍시다. 

```cmd
> pip install virtualenvwrapper-win
```

`seminar`라는 이름의 가상환경을 만들어 봅시다. 다른 이름으로 만들어도 괜찮습니다. 

```cmd
> mkvirtualenv seminar
```

가상환경이 만들어지고 곧바로 방금 만든 가상환경 내에 들어오게 됩니다. 

```cmd
(seminar) > 
```

참고로 가상환경을 만들 때 아래처럼 파이썬 버전을 따로 지정해 줄 수도 있습니다. 단 이미 컴퓨터에 설치되어 있고 환경변수에 등록이 되어 있는 버전이어야 합니다. 

```cmd
> mkvirtualenv --python=3.7 myenv37
```

#### 자주 쓰는 명령어 목록

* `mkvirtualenv <ENVNAME>` 가상환경 생성
* `rmvirtualenv <ENVNAME>` 가상환경 삭제 
* `workon` 만들어진 가상환경 목록 확인
* `workon <ENVNAME>` 가상환경 활성화
* `deactivate` 가상환경 비활성화

참고: [가상 환경 소프트웨어 설치하기(MDN)](https://developer.mozilla.org/ko/docs/Learn/Server-side/Django/development_environment#가상_환경_소프트웨어_설치하기) 

### 3. Django 시작하기

방금 만든 가상환경이 활성화된 상태에서 다음 명령어를 입력합니다. 

> **`pip`란?** 파이썬 패키지 관리자입니다. pip라는 이름은 "Pip Installs Packages"를 의미합니다. 

```cmd
(seminar) > pip install Django
```

다음 명령어를 입력해서 Django가 설치되었는지 확인합시다. 

```cmd
(seminar) > pip list
```

Django 개발을 시작할 준비가 다 되었습니다! 첫 프로젝트를 생성해 봅시다.

```cmd
(seminar) > django-admin startproject myproject
```

서버를 켜서 확인해 봅시다.

```cmd
(seminar) > cd myproject
(seminar) > python manage.py runserver
```

서버가 켜지면 웹 브라우저에 들어가서 주소창에 `localhost:8000`을 입력해 봅시다.
![image](https://user-images.githubusercontent.com/37106318/54377063-bfb11300-46c7-11e9-9034-191fb392b0e5.png)
로켓이 보인다면 성공한 거예요!  🚀

서버를 끄고 싶다면 터미널에서 `ctrl + c`를 눌러 줍시다. 그리고 터미널에서 나가기 전에 가상환경도 비활성화해 줍시다! 

```cmd
(seminar) > deactivate 
```

### 4. Git 설치

> **Git이란?** https://git-scm.com/ 참고

https://git-scm.com/download/win 에서 자신의 컴퓨터에 맞는 Git for Windows를 다운받은 다음 설치합니다.

설치가 완료되면 cmd를 켜서 Git의 버전을 확인합니다.

```cmd
> git --version
```

## 맥

```
1. 패키지 관리자(Homebrew) 설치
2. Python 버전 관리자(pyenv) 설치
3. Python 설치 및 확인
4. 가상환경 플러그인(pyenv-virtualenv) 설치 및 가상환경 생성
5. Django 설치
6. Django 프로젝트 생성 및 확인
```

### 1. 패키지 관리자(Homebrew) 설치

`Homebrew`는 개발에 필요한 패키지들을 편리하게 설치하고 관리할 수 있어 널리 사용되고 있는 패키지 관리자입니다. 
Homebrew를 설치하기 위해서는 Xcode에 포함된 Command Line Tools(개발자용 명령어 라인 도구)가 필요합니다.
Xcode는 용량이 크기 때문에, 이미 Xcode가 설치되어 있는 것이 아니라면 아래 명령을 통해 Command Line Tools만 설치할 수도 있습니다.

```bash
$ xcode-select --install # $는 빼고 입력
```

이제 아래 명령어를 통해 Homebrew를 설치합시다. [출처](https://brew.sh/index_ko)

```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

설치가 잘 되었다면 아래 명령을 통해 Homebrew의 버전을 확인할 수 있습니다. 

```bash
$ brew -v
```

Homebrew가 관리하는 패키지 목록을 확인할 수 있습니다.

```bash
$ brew list
```

처음 설치한 경우, 아직 아무 것도 나타나지 않는 것이 정상입니다. 즉 터미널에 아무 것도 출력되지 않는 상황입니다.

### 2. Python 버전 관리자(pyenv) 설치

`pyenv`는 Python 버전 관리자입니다.

 파이썬은 크게 2.x 버전과 3.x 버전으로 양분되어 있는데, Mac OS에는 기본적으로 `2.7.10`이 설치되어 있습니다.하지만 우리가 사용할 Django는 Python 3 기반이기 때문에 3.x 버전, 그 중에서도 가장 안정된 버전인 `3.6.8`을 설치하겠습니다. 

```bash
$ brew install pyenv
```

pyenv를 설치하면 의존성(dependency)들도 함께 설치됩니다. 

설치가 제대로 되었는지 확인하기 위해 터미널에 `pyenv`를 입력하면 에러가 발생할 것입니다. 이는 터미널이 아직 pyenv라는 명령을 알아듣지 못하는 상황이기 때문입니다.

이를 해결하기 위해서 다음과 같은 명령어를 입력합니다. 

```bash
$ vim ~/.bash_profile
```

그러면 다른 창이 나타날 것입니다. 
아래에서 괄호를 제외한 부분을 입력해 주세요. 

```bash
(i를 누른다.)
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
(esc를 누른다.)
:wq
(enter를 누른다.)
```

다시 원래 보던 터미널이 나타날 것입니다.
위의 과정은 터미널에게 `pyenv` 명령을 알아듣도록 만든 것입니다.
마지막으로 터미널을 다시 load하는 과정이 필요하니 아래 명령을 입력하세요.

```bash
$ source ~/.bash_profile
```

***

만약 bash가 아닌 zsh 쉘을 사용하는 경우

```zsh
% vi ~/.zshrc
```

i를 누른후, 다음의 내용을 붙여넣기 합니다.

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

esc를 누르고, :wq 엔터를 눌러 빠져나옵니다.

터미널을 종료한 후 다시 실행합니다.

***


이제 아래 명령으로 Python 버전들을 확인할 수 있습니다.

```bash
$ pyenv versions
```

전에 따로 파이썬을 설치한 적이 없다면, `2.7.10`인 system만 나타날 것입니다.

### 3. Python 설치 및 Python 버전 관리

이제 Python 3.6.8을 설치합시다. 

```bash
$ pyenv install 3.6.8
```

이때 아래와 같은 에러가 발생할 수 있습니다.

```bash
zipimport.ZipImportError: can't decompress data; zlib not available
```

이는 Mac OS Mojave에서 설치에 필요한 경로를 찾지 못해서 발생하는 에러입니다.
아래 명령으로 해결할 수 있습니다.

```bash
$ sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
```

다시 파이썬을 설치해 줍니다. 

```bash
$ pyenv install 3.6.8
```

에러가 발생하지 않았다면 아래 명령으로 새로운 Python 버전이 설치되었는지 확인 봅시다. 

```bash
$ pyenv versions
```

Python 3을 기본 버전으로 설정합니다. 

```bash
$ pyenv global 3.6.8
```

### 4. pyenv-virtualenv 설치 및 가상환경 생성

파이썬은 웹 개발 이외에도 기계학습 등 다양한 분야에서 사용되는 언어입니다. `pyenv-virtualenv`라는 가상환경 플러그인을 설치해서 각각의 프로젝트가 사용하는 패키지들이 충돌하지 않도록 개발 환경을 분리하도록 하겠습니다. 

```bash
$ brew install pyenv-virtualenv
```

설치가 끝나면 아래 명령어를 입력해서 목록에 `pyenv-virtualenv`가 있는지 확인해 봅시다. 

```bash
$ brew list
```

이제 Python 3.6.8을 기반으로 하는, `seminar`라는 이름의 가상환경을 만들어 봅시다. 

```bash
$ pyenv virtualenv 3.6.8 seminar
```

아래 명령어를 입력했을 때 seminar라는 가상환경이 보인다면 가상환경이 잘 만들어진 것입니다. 

```bash
$ pyenv versions
```

이제 Django 가상환경을 활성해 봅시다. 

```bash
$ pyenv activate seminar
```

가상환경을 비활성화하는 명령어는 다음과 같습니다. 

```bash
$ pyenv deactivate
```

### 5. Django 설치

Django는 파이썬으로 만들어진 웹 프레임워크입니다. 

아래 명령으로 이미 설치되어 있는 Python 패키지를 확인할 수 있습니다.

> **`pip`란?** 파이썬에 내장되어 있는 패키지 관리자

```bash
$ pip list
```

![image](https://user-images.githubusercontent.com/37106318/54376824-3b5e9000-46c7-11e9-918e-0bfb14566015.png)

최신 버전이 아니라는 경고가 나타나면 아래 명령을 입력하면 됩니다.
반드시 할 필요는 없습니다!

```bash
$ pip install --upgrade pip
```

이제 Django를 설치해 봅시다. 

```bash
$ pip install django
```

Django가 제대로 설치되었는지 확인해 봅니다. 

```bash
$ pip list
```

### 6. Django 프로젝트 생성 및 확인

이제 터미널에서 원하는 디렉토리로 이동한 후 직접 Django 프로젝트를 만들어 봅시다. 

#### 참고) 기본적인 터미널 명령어들

* `cd` 'change directory'의 약어. 원하는 하위 디렉토리로 이동하는 명령 e.g. cd testForInstallation
* `./` 현재 디렉토리
* `../` 상위 디렉토리로 이동
* `mkdir` 'make directory'의 약어로 디렉토리를 생성 e.g. mkdir Django
* `ls` 현재 디렉토리 내 파일을 열람

먼저 `testForInstallation`이라는 이름의 Django 프로젝트를 생성합니다. 

```bash
$ django-admin startproject testForInstallation
```

프로젝트 디렉토리로 들어간 후 개발용 서버를 켜 줍시다.  

```bash
$ cd testForInstallation
$ python manage.py runserver
```

여기까지 한 후 터미널이 아래와 같이 보이면 서버가 켜진 것입니다. 
![image](https://user-images.githubusercontent.com/37106318/54376883-57fac800-46c7-11e9-9b0a-74be8633c57f.png)

이제 chrome 등 인터넷 브라우저에서 http://127.0.0.1:8000/ 으로 이동합니다.
![image](https://user-images.githubusercontent.com/37106318/54377063-bfb11300-46c7-11e9-9034-191fb392b0e5.png)

위와 같은 화면이 보이면 됩니다! 
서버를 닫고 싶다면 `control + c`를 누르면 됩니다.
이제 가상환경을 도로 비활성화합니다. 

```bash
$ pyenv deactivate
```

## VS Code 설치

> VSCode 말고 다른 에디터를 쓰셔도 되지만, VSCode를 추천합니다!

https://code.visualstudio.com/ 에 들어가서 자신의 운영체제에 맞는 VSCode를 다운받습니다.

'악성 소프트웨어가 있는지 확인할 수 없기 때문에 열 수 없습니다'라는 메세지가 뜨는 경우,
왼쪽상단 사과->시스템 환경설정->보안 및 개인 정보보호-> 일반 탭에서 '다음에서 다운로드한 앱 허용:' 밑에 '확인 없이 열기'를 클릭합니다.

다운받은 VS Code를 실행한 다음, 왼쪽의 '확장'탭을 클릭합니다.
파이썬과 Django 개발을 편리하게 해 주는 확장들을 몇 가지 설치합시다.

1. Python<br>
   ![image](https://user-images.githubusercontent.com/22510942/54586574-d3120480-4a60-11e9-8854-999a2ec82e73.png)
2. Django<br>
   ![image](https://user-images.githubusercontent.com/22510942/54586603-e45b1100-4a60-11e9-95d4-02fbda83e564.png)

파이썬과 관련된 것이 아니라도 개발을 편리하게 해 주는 여러 확장들이 많으니 이것저것 찾아서 써 보시면 좋을 것 같아요!