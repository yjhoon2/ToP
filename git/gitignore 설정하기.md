# [github] .gitignore 설정하기

- [.gitignore로 .ipynb_checkpoints 없애기](https://velog.io/@khnn/%EA%B9%83%ED%97%99-.ipynbcheckpoints-%EC%97%86%EC%95%A0%EA%B8%B0)
- [.gitignore 파일 안에 적용할 문법](https://nesoy.github.io/articles/2017-01/Git-Ignore)



### 1. ".gitignore" 파일을 생성한다.

- .git 이 있는 repository로 이동한다. (main branch)
- 터미널에서 `touch .gitignore` 를 입력한다.
- `la` 또는 `ls -a` 를 입력해서 정상적으로 파일이 생성되었는지 확인한다.



### 2. vi 에디터를 이용해서 파일을 수정한다.

- `vi .gitignore` 를 입력하면 파일을 수정할 수 있다.

- track하지 않을 파일을 입력한다. ([.gitignore 파일 안에 적용할 문법](https://nesoy.github.io/articles/2017-01/Git-Ignore) 참고)

  -  `.ipynb_checkpoints` : ipynb_checkpoints 파일을 없애고 싶을 경우
  - `*/.ipynb_checkpoints/*` : 폴더 안의 파일까지 무시하고 싶을 경우

  > **vi editor 사용법**
  >
  > `i` 를 입력하면 파일 편집이 가능
  >
  > 작성 후 `esc` 를 누르면 명령모드로 돌아올 수 있다.
  >
  > 명령모드에서 `:wq` 를 입력하면 저장 후 나올 수 있다.



----------------



##### 프로젝트 중간에 gitignore 파일을 만들 경우

```
# 로컬에서 캐시 지우기
git rm -r --cached .ipynb_checkpoints

# git에 반영
git add .
git commit -m "Ignore ipynb_checkpoints"
git push
```



##### 추가로  track하지 않을 파일 지정

- 터미널에서 `vi .gitignore` 입력 후, 에디터에 파일 추가해서 저장

