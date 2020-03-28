## github fork

- **fork**는 어떤 GitHub 저장소를 내 저장소로 가져와서 '관리'할 수 있게 한다. 

  다른 이의 프로젝트를 그저 사용하거나 보기만 한다면 clone을 하면 되지만, fork를 하면 소스를 '관리'할 수 있는 것이다. 

  즉, 타인의 GitHub 프로젝트는 Read-only이지만 내 저장소로 fork하면 그 프로젝트에 대한 Write 권한이 생긴다.

- **fork**는 다른 사람의 Github repository에서 내가 어떤 부분을 수정하거나 추가 기능을 넣고 싶을 때 해당 respository를 내 Github repository로 그대로 복제하는 기능이다.

- **fork**한 저장소는 원본(다른 사람의 github repository)와 연결되어 있다. 여기서 연결 되어 있다는 의미는 original repository에 어떤 변화가 생기면(새로운 commit) 이는 그대로 forked된 repository로 반영할 수 있다. 이 때 fetch나 rebase의 과정이 필요하다.

- **clone** : clone은 특정 repository를 내 local machine에 복사하여 새로운 저장소를 만든다. clone한 원본 repository를 remote 저장소 `origin`으로 가지고 있다. 권한이 없는 경우 해당 저장소로 push 하지 못한다.



#### 실행 방법

1.  fork하고 싶은 repository에 가서 아래 그림에 있는 **Fork**버튼을 누른다.

   <img width="235" alt="3 1" src="https://user-images.githubusercontent.com/59239352/77728153-415bb080-703f-11ea-894f-800461fc563f.PNG">

   - 그럼 내 repository에 추가된 것을 확인할 수 있을 것이다.

     

2.  내 원격저장소에 있는 것을 local 저장소로 불러온다.

   ```
   git clone 내 원격저장소 주소
   ```



3. 여기서 개인 repository에 계속 업데이트 할 수 있지만 원본 소스에 권한이 있는 사람이 원본 소스를 수정하고 업데이트 했을 때  필요한 것이 **upstream 등록**과 **upstream 동기화**이다.

   ##### upstream 등록

   - 보통 원본 소스코드가 있는 곳의 위치를 **upstream**이라고 한다. 이 이름으로 원본소스의 위치를 등록해줘야한다.

   - 먼저 `git remote -v`를 사용하여 확인해보면 내 위치만 등록되어 있는 것을 확인할 수 있다.

     > 이 때 새로 생성된 repository로 디렉토리를 이동하여 실행해야 한다.
   
     ```
     $ git remote -v
     origin  https://github.com/yjhoon2/deep-learning-with-python-notebooks.git (fetch)
  origin  https://github.com/yjhoon2/deep-learning-with-python-notebooks.git (push)
     ```

     

   - 여기에 **upstream**이라는 이름으로 원본 소스코드의 위치를 추가시켜준다.
   
     ```
  $ git remote add upstream https://github.com/fchollet/deep-learning-with-python-notebooks.git
     ```

     

   - 제대로 추가되었는지 확인
   
     ```
     $ git remote -v
     origin  https://github.com/yjhoon2/deep-learning-with-python-notebooks.git (fetch)
     origin  https://github.com/yjhoon2/deep-learning-with-python-notebooks.git (push)
     upstream        https://github.com/fchollet/deep-learning-with-python-notebooks.git (fetch)
  upstream        https://github.com/fchollet/deep-learning-with-python-notebooks.git (push)
     ```

     

   - 만약 주소를 잘못 저장했을 때 삭제하는 방법
   
     ```
  $ git remote remove upstream
     ```

     

   ##### upstream 동기화

   - **fetch** 명령어를 통해 원본 소스코드의 내용을 local에 내려받는다.
   
     ```
     $ git fetch upstream
     From https://github.com/fchollet/deep-learning-with-python-notebooks
      * [new branch]      master     -> upstream/master
     
     
     
     ## 만약 바뀐게 많다면 이렇게 뜬다.
     
     $ git fetch upstream
     remote: Enumerating objects: 34, done.
     remote: Counting objects: 100% (34/34), done.
     remote: Compressing objects: 100% (6/6), done.
     remote: Total 38 (delta 27), reused 32 (delta 27), pack-reused 4
     Unpacking objects: 100% (38/38), done.
     From https://github.com/kaldi-asr/kaldi
      * [new branch]          5.0                      -> upstream/5.0
      * [new branch]          5.1                      -> upstream/5.1
      * [new branch]          5.2                      -> upstream/5.2
      * [new branch]          5.3                      -> upstream/5.3
      * [new branch]          5.4                      -> upstream/5.4
      * [new branch]          cudnn                    -> upstream/cudnn
      * [new branch]          jtrmal-patch-1           -> upstream/jtrmal-patch-1
      * [new branch]          master                   -> upstream/master
      * [new branch]          multitree                -> upstream/multitree
      * [new branch]          reorthonormalize-cleaned -> upstream/reorthonormalize-cleaned
   * [new branch]          revert-3018-pr           -> upstream/revert-3018-pr
     ```

     

   - 내려받은 소스코드를 실제 내 repository에 **merge** 시켜줘야 한다.
   
     ```
     $ git merge upstream/master
     
     
     
     # 바뀐 것이 많을 경우
     
     $ git merge upstream/master
     Updating 05d9a3d5e..afc5e78c2
     Fast-forward
      .gitignore                                             |   1 +
      egs/babel/s5d/conf/lang/404-georgian.FLP.official.conf |   4 +--
      egs/babel/s5d/local/make_L_align.sh                    |  14 +++++++---
      egs/heroico/s5/cmd.sh                                  |   1 +
      egs/heroico/s5/local/heroico_download.sh               |  37 --------------------------
      egs/heroico/s5/local/subs_prepare_data.pl              |   2 +-
      egs/heroico/s5/run.sh                                  |  22 +++++++++++-----
      egs/voxforge/s5/local/voxforge_prepare_dict.sh         |   2 +-
      src/base/kaldi-error.cc                                |   8 ++++--
      src/decoder/grammar-fst.cc                             | 124 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++--
      src/decoder/grammar-fst.h                              |  17 ++++++------
      src/doc/grammar.dox                                    |   2 +-
      src/feat/mel-computations.h                            |   2 +-
      src/online/online-feat-input.h                         |  38 +++++++++++++++++++++++----
      14 files changed, 203 insertions(+), 71 deletions(-)
      delete mode 100755 egs/heroico/s5/local/heroico_download.sh
     ```



이제 내쪽 *repository* 와 원본코드가 존재하는 *repository* 가 동기화 되었습니다. 빠르게 변하는 프로젝트일수록 동기화는 매우 중요합니다. 코드를 수정하거나 반영하기 전에 항상 동기화 해주는 습관이 필요하겠습니다.



[참고 사이트](https://jybaek.tistory.com/775)



