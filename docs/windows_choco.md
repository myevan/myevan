# 초코 따라하기

<https://chocolatey.org/>

초코렛티(이하 초코)는 윈도우용 패키지 매니저 입니다.

## 설치

<https://chocolatey.org/install>

관리자용 명령어 프롬프트(cmd.exe)에서 다음 스크립트를 실행합니다.

```bat
C:> @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

일반적인 프로그램과는 달리 `C:\Program Files`가 아닌 `C:\ProgramData`에 설치됩니다.

```bat
C:\> dir C:\ProgramData\chocolatey
```

다른 경로나 관리자 권한 없이도 설치할 수 있지만, 보안상의 이슈로 관리자 모드로 디폴트 경로 설치를 추천한다고 합니다.


## 패키지

<https://chocolatey.org/packages>

윈도우 패키지 설치를 그대로 사용하기 때문에 제어판에서 설치 내역을 볼 수 있습니다. 다만 choco 를 통해 설치한 프로그램을 제어판에서 직접 삭제하면 choco 에서 삭제를 인지하지 못 하는 이슈가 있습니다.

### python

python-3.x 버전이 디폴트 설치 버전입니다.

```bat
C:\> choco install python
```

python-2.x 는 python2 를 설치해야 합니다.

```bat
C:\> choco install python2
```

### neovim

윈도우 패키지가 존재하지 않아 `C:\tools\neovim\Neovim` 에 설치됩니다. 설치 위치를 변경하려면 환경 변수 `ChocolateyToolsLocation` 를 설정합니다.

```bat
C:\> choco install vim
```

## 제거 

<https://chocolatey.org/docs/uninstallation>

스크립트 제거를 지원하지만 깔끔한 제거를 보장하지는 않습니다.

### 폴더 삭제

* 초코 `C:\ProgramData\chocolatey`
* 도구들 `C:\tools`

### 시스템 환경 변수

* `ChocolateyInstall` 제거
* `PATH`: `C:\ProgramData\chocolatey\bin` 제거

### 사용자 환경 변수 

* `ChocolateyToolsLocation` 제거
* `ChocolateyLastPathUpdate` 제거