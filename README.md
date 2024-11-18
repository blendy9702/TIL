# Git 셋팅

## 1. Git 관련

### 1.1. Git 프로그램 설치

- 프로그램 (https://git-scm.com/) : 64bit Window
- 설치된 버전 확인

```
윈도우 키 + R 키 입력후 cmd 입력
```

- 아래 입력 후 확인

```
git --version
```

### 1.2.VSCode 터미널 셋팅

- 터미널 환경을 git bash 창으로 설정을 진행

```
관리도구 버튼 > 설정 메뉴 > 입력창에 default:Windows 입력 후 Git Bas확인
```

- 터미널 환경을 더 편리하게 git bash 설정

```
터미널 입력창 자체 > 우측 + 버튼 옆의 v 모양의 펼침 선택 후 기본프로필 선택 클릭
검색 영역에 보여지는 항목 중 Git Bash 선택하여 완료
```

### 1.3. Git 코딩 환경 설정

- 터미널 입력 내용

```
버전 확인
 : git --version  엔터

기본 브랜치명 변경 (main)
: git config --global init.defaultBranch main

윈도우, 맥, 리눅스 환경에서 키보드 Enter 키 처리 동일하게
: git config --global core.autocrlf true  엔터

깃 명령어 입력시 Editor 를 VSCode 로 셋팅 (commit)
: git config --global core.editor "code --wait"  엔터

사용자 아이디를 저장해 둠
: git config --global user.name "아이디"   엔터

사용자 이메일을 저장해 둠
: git config --global user.email "아이디@gmail.com"   엔터

```

## 2. 깃허브 셋팅

- 사이트 (https://github.com)

### 2.1. 프로젝트 즉 레파지토리 (Repsitory - 저장소) 생성

```
생성시 private 와 public 중에 선택 유의
: private 는 개인 및 초청한 사용자만 접근 가능
: public 은 아무나 접근가능 (오픈소스)

설명글은 가능하면 작성을 해주는 것이 좋습니다.
: 프로젝트 목록에 출력됨.
```

## 3. 깃과 깃허브 연결하기(인증하기)

### 3.1. 깃허브 웹사이트에 로그인한 상태로 대기

### 3.2. PC의 '자격 증명 관리자' 를 실행 (찾기 > 자격 증명 입력)

```
항목 중 windwos 자격 증명 항목
: 기존에 github 있으면 삭제
```

### 3.3. VSCode 에 새로운 폴더 생성 및 등록

#### 3.3.1. 프로젝트 등록후 터미널 실행

```
Ctrl + `
터미널이 bash 인지 필수 확인
```

#### 3.3.2. 깃 초기화

```
git init
```

#### 3.3.3. README.md 파일 추가

```
이 파일은 루트폴더에 있어야함.
필요한 내용작성
```

#### 3.3.4. 수정된 작업 git 등록

```
git add .
```

#### 3.3.5. 수정내역 메모 작성

```
git commit
첫번째 줄은 제목              엔터
엔터키를 통해서 제목과 내용 구분용 공백 줄
세번째 줄에 한일 작성..
저장 후 닫기
```

#### 3.3.6. 깃허브 URL 연결하기 (최초 1번만)

```
git remote add 별칭 URL 작성함
git remote add origin https://github.com/아이디/프로젝트.git
```

#### 3.3.7. 깃허브 전송

```
git push 별칭 브랜치명
git push origin main

만약 자격 증명 관리에 없으면 자동으로 인증 되는 안내창 출력
```
