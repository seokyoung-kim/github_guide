# Github 정리
## Git이란?
버전 관리 시스템

## Github란?
자신이 작성한 코드를 공개하는 툴. 기업에서는 그 회사 안에서만 공개하고, 보안상의 문제가 없는지 등을 다른 사원이 확인하고 리뷰해주기도 한다.

## 용어 설명
먼저, 알기 어려운 용어의 설명부터 알아본다.

#### index
지금부터 등록하는 파일이 이전과 어떻게 바뀐지를 등록하는 일시적인 장소
#### repository
저장고. 데이터 등을 보존해두는 장소
#### remote repository
Github 상의 데이터를 보존해두는 장소를 가리킨다.
#### local repository
Github에 송신하는 데이터를 등록해두고, 자신의 PC 상의 장소를 가리킨다.
#### commit
Github에서는 Github에 데이터를 송신하기 전에 일시적인 로컬환경에 데이터를 등록하고, 그 후 한번에 Github상으로 송신한다. 그 로컬 환경에 데이터를 등록하는 것을 **commit**이라고 한다.
#### push
로컬 환경에 등록해둔(커밋해둔) 데이터를 Github에 송신 및 공개하는 것을 말한다.

## Github의 흐름
여기에서는 Github에 데이터를 송신하기까지의 흐름을 설명한다.
1. 본인의 PC에서 개발한 것을, local repository의 index에 추가(add) 한다.
2. 본인의 PC에서 개발한 것을, local repository에 등록(commit) 한다.
3. 전부 등록이 끝난 후에, 그것들을 Github에 송신(push) 한다.

## Github 사용법

### 1. Github에 repository 만들기 (remote repository)
먼저, Github상에 repository를 만든다. New Repository를 누른다.
다음으로 항목들을 채우고 Create Repository를 누른다. 이것으로 repository의 작성이 완료되었다.
표시된 페이지의 URI를 사용해야 하므로 기억해둔다.

<br/>

### 2. local 환경에 repository 만들기(local repository)
다음으로 local repository를 작성한다. 만드는 장소는 어디든 상관없다. 이후 터미널 창에서 만든 폴더로 이동 후 ```git init```을 입력하여 local repository를 만든다.

<br/>

### 3. 파일을 local repository에 등록(commit)
실제로 파일을 local repository에 등록시켜본다.
적당한 텍스트 파일을 작성한다.
```
text.txt

hello git
```
여기에서는 ```C:\git```의 위치에 저장하였다.

다음으로 데이터의 변경점을 추가한다.
이번 경우에는 신규작성이 되겠다.
이것들을 git 커맨드로 전부 추가한다.

```git add test.txt```

위의 커맨드를 입력하면 변경점을 index에 추가해준다.

만약 ```fatal: Not a git repository (or any of the parent directories): .git```가 표시된다면, ```git init```이 실패한것(local repository가 작성되어있지 않은 것)이다.

index에 데이터를 추가했으면 등록(commit) 한다.

```git commit -m "메시지"```

이 커맨드로 인덱스의 내용이 전부 local repository에 등록되었다.

이 시점에서는 **local** repository이기 때문에 Github상에는 반영되지 않는다.

<br/>

### 4. Github에 데이터를 송신(remote repository에 데이터를 push)
Github에 데이터를 공개해본다.
아까의 URI를 사용한다.

먼저 index(파일의 변경점 등의 리스트)를 Github에 작성한다.

```git remote add origin https://github.com/유저ID/repository이름.git```

commit한 데이터를 Github에 송신(push)한다.
```git push origin master```

여기까지 에러 없이 진행되면, Github에 데이터가 등록된다.

<br/>

### 1차 정리
지금까지 나온 여러 커맨드를 정리해본다.
1. local repository에 작성  
```git init```
2. local repository에 파일의 변경점을 추가(index에 추가)    
```git add 파일명```
3. local repository에 index에 추가한 파일을 등록    
```git commit -m "코멘트"```
4. 추가한 index(파일의 변경점 등)을 Github에 작성   
```git remote add origin repository의 URI```
5. local repository의 파일을 Github의 repository에 송신     
```git push origin master```

<br/>

### 5. push한 데이터를 변경 및 갱신
Github상에 공개한 데이터를 변경해본다.
아까의 test.txt를 편집하고 push해보자.
1. 변경점을 index에 추가    
```
git add test.txt
```
2. 파일을 등록(commit)  
```
git commit -m "코멘트"
```
3. 데이터를 송신
```
git push origin master
```
에러 없이 진행했다면, 데이터가 변경되었을 것이다.

<br/>

## branch란?
branch를 나누고 병합한다는 말은 Git에서 자주 쓰이는 단어일 것이다.

### 용어 설명
#### merge
**통합한다**는 의미.
여러개로 분기된 것을 연결한다.
#### branch
단어 그대로 **가지**를 뜻한다.
버전을 업그레이드할 때, 실패 대비용으로 복사해둔 이미지.

## branch 사용법
### 1. branch를 만듦
```
git branch branch명
```   
위 명령어로 branch명이라는 이름의 branch가 작성된다.    
지금 존재하는 branch를 확인하기 위해서는
```git branch```라는 명령어로 확인한다.

<br/>

### 2. branch를 이동
```git branch```로 branch를 확인하면 master와 branch명으로 된 2개의 branch를 확인할 수 있다.    
지금은 master라는 branch에 __*__ 가 붙어 있다. 이것은 지금 push하면 master branch에 데이터가 들어간다는 의미가 된다.    
우리가 branch를 따로 만든 것은 실패 대비용으로 복사해둔 것이기 때문에 새로 만든 branch로 변경해보자.    
```
git checkout testbranch
```   
다시 한번 ```git branch``` 명령어로 확인해보면 __*__ 의 위치가 test branch로 이동한 것을 확인할 수 있다.

<br/>

### 3. 만든 branch에 데이터를 송신
새로 만든 branch에 데이터를 송신(push)해보자.
먼저 텍스트 파일을 수정한다.
```
test.txt

hello git!
Edit test!
branch test!
```
1. 인덱스에 변경점을 등록
```
git add test.txt
```
2. 파일을 local repository에 등록(commit)
```
git commit -m "코멘트"
```
3. Github에 local repository의 데이터를 송신(push)
```
git push origin branch명
```
이번에는 새로 만든 branch에 데이터를 송신하기 때문에
git push origin **branch명**이다.

이제 Github상에서 송신되었는지 확인해보자.
좌측 브랜치의 풀다운으로부터 branch를 변경한다.

그러면, 아까 push한 것이 반영되어 있는 것을 알 수 있다.

### 4. branch를 master에 통합
이제 merge를 해보자.    
새로 만든 branch를 master branch에 반영하는 것이다.
1. 먼저 넣어야 할 branch를 선택한다. 여기서는 master가 될 것이다.
```
git checkout master
```
2. master에 만들었던 branch를 merge한다.
```
git merge branch명
```
3. 마지막으로 병합된 정보를 Github에 보낸다(push)
```
git push origin master
```
이번에는 master branch에 데이터를 push했기 때문에 커맨드는 **master** 가 된다.

그럼 반영되었는지 확인해보자.

### 정리
지금까지 나온 커맨드를 정리해본다.
1. 새로운 branch를 만든다.
```
git branch branch명
```
2. 현재 존재하는 branch를 확인한다.
```
git branch
```
3. branch를 이동한다.
```
git checkout branch명
```
4. branch를 병합(merge)한다.
```git checkout```로 병합하고 싶은 branch로 이동하여
```
git merge 넣고 싶은 branch명
```

# TO DO
Github 상의 데이터를 local repository에 다운로드하는 pull
