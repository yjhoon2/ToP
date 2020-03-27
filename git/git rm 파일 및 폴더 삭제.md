## git rm : 파일 및 폴더 삭제



```
git rm 파일위치/파일명
```

- local 디렉토리와 git 모두 삭제

```
git rm --cahed 파일위치/파일명
```

- local 디렉토리에서는 유지하고 git에서만 삭제

```
git rm -f 파일위치/ 파일명
```

- 변경사항을 commit하지 않았을 경우 강제로 삭제

```
git rm -r 파일위치/파일명
```

- 디렉토리 삭제

```
git rm -r --cached 디렉토리(폴더)명/
```

- git에 있는 디렉토리만 지우고 local 디렉토리는 남겨둠

```
git rm --cached -r .폴더명/
```

- 폴더 하위의 모든 파일 삭제



#### 수정한 파일 또는 staged 상태인 파일을 삭제하는 경우

```
# 워킹 디렉터리에서 파일 수정 직후 삭제하려는 경우
$ git rm testFile
error: the following file has local modifications:
    testFile

# 워킹 디렉터리에서 파일 수정 후 git add 하고 커밋 직전에 삭제하려는 경우 오류내용$ git rm testFile
error: the following file has changes staged in the index:
    testFile
```

- solution

  ```
  git rm -f testFile
  ```



```
git rm log/\*.log  # log/디렉토리의 확장명이 log인 파일 모두 삭제
git rm \*.~  # ~로 끝나는 파일 모두 삭제
```







## git 상태에 대해서

* [참고사이트1]([https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0](https://git-scm.com/book/ko/v2/Git의-기초-수정하고-저장소에-저장하기))

* [참고사이트2](https://dololak.tistory.com/304)

  

![2 1](https://user-images.githubusercontent.com/59239352/77612042-65998d80-6f6a-11ea-8a48-26cdf140875d.png)

> 처음 디렉토리에 만든 파일은 **Untracked**
>
> *git add*나 *git commit*을 한 순간부터 쭉 **Tracked**
>
> > 



![2 2](https://user-images.githubusercontent.com/59239352/77613251-8f07e880-6f6d-11ea-829a-63eab95fc3b3.png)

##### Untracked와 Tracked 상태

-  워킹 디렉터리(local directory)에 있지만 git add나 commit 하지 않은 파일은 Untracked 상태, git add나 commit 했던 적이 있는 파일들은 Tracked 상태입니다.

- Tracked 상태인 파일들은 Git이 저장 및 관리하며, Untracked 파일은 Git이 신경쓰지 않습니다.



##### Unmodified와 Modified 상태

- 파일의 변경 여부에 따라 **Modified(변경 발생)**과 **Unmodifed(변경 없음)** 상태로 나눌 수 있습니다.

- 변경 발생 기준은 '파일이 **Staged** 또는 **Commit**된 시점 이후로 변경 되었는가' 입니다.

  - **Staged**는 _git add_ 명령어를 통해 Staging Area에 내역을 추가한 상태
  - git commit 명령을 통해한 Commit한 경우 **Committed** 상태입니다.

  