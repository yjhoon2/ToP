# Python 가상환경 만들기



### 1. 가상환경이란?

----

- 파이썬에서는 한 라이브러리에 대해 하나의 버전만 설치가 가능하다.
- 여러개의 프로젝트를 진행하게 되면 이는 문제가 된다. 작업을 바꿀때마다 다른 버전의 라이브러리를 설치해야한다.
- 이를 방지하기 위한 격리된 독립적인 가상환경을 제공한다.
- 일반적으로 프로젝트마다 다른 하나의 가상환경을 생성한 후 작업을 시작하게 된다.
- 가상환경의 대표적인 모듈은 4가지가 있다.
  - **venv** : Python 3.3 버전 이후 부터 기본모듈에 포함됨
  - **virtualenv** : Python 2 버전부터 사용해오던 가상환경 라이브러리, Python 3에서도 사용가능
  - **conda** : Anaconda Python을 설치했을 시 사용할 수있는 모듈
  - **pyenv** : pyenv의 경우 Python Version Manger임과 동시에 가상환경 기능을 플러그인 형태로 제공

> <가상환경을 쓰는 이유>
>
> 다양한 이유가 있겠지만, 제가 생각하는 가장 중요한 이유는 **python 버젼 관리**와 **패키지 충돌 방지**가 있습니다.
>
> python은 현재 2.x 버젼과 3.x 버젼이 혼용되는 과도기에 있고 (물론, 요즘엔 대다수의 프로젝트들이 3.x로 많이 업그레이드를 하고 이를 support 하고 있습니다), 때론, 2.x 버젼의 python 환경에서 프로젝트를 개발해야할 때도 있고, 3.x버젼의 python 환경에서 개발해야할 때도 있습니다. 이럴 때마다, uninstall과 install하면서 python 버젼을 바꿀 수는 없을 것입니다.
>
> 두번째로, 프로젝트별로 필요한 python 패키지만 설치해서 사용하면 되는데, 가상환경이 아닌 곳에 패키지를 몽땅 설치해버리면 불필요한 패키지까지 설치된 환경이 될 것이고, 때론 dependency또한 꼬여버릴 수 있습니다. (마치, python 2.x 와 python 3.x 가 모두 설치 되었을때처럼 말이죠)

​	

### 2. 가상환경  만들기

----



##### virtualenv 사용

1.  cmd 창을 이용하여 virtualenv를 설치한다.

   ```
   pip install virtualenv
   
   # python -m pip install virtualenv
   ```

2.  가상환경이 만들어질 경로에 가상환경을 만든다.

   ```
   virtualenv 가상환경이 만들어질 경로\가상환경 이름
   
   (가상환경이 만들어질 경로로 이동한 후)
   virtualenv 가상환경 이름
   
   # python -m virtualenv 가상환경 이름
   ```

3.  가상환경이  생성된 디렉토리 안에 Scripts 디렉토리로 이동 하여 실행한다.

   ```
   cd 가상환경이 만들어질 경로\가상환경 이름\Scripts\activate
   ```

   - 명령 콘솔 앞에 (가상환경 이름)이 표시되면  가상환경이 실행된 것이다.
   - 가상환경을 종료하는 명령어는 **deactive**이다.

4.  원하는 모듈을 설치

   ```
   pip install numpy pandas sklearn matplotlib tensorflow
   ```



> 파이썬2에서는 가상환경 라이브러리가 기본 제공되지 않았기 때문에, 써드파티 라이브러리인 virtualenv 라이브러리가 필수입니다. 하지만 파이썬3에서는 **venv**라는 가상환경 라이브러리가 기본제공되기 때문에, virtualenv 를 쓰지 않으셔도 됩니다.



##### venv 사용

- venv는 python3에 빌트인 되어있기 때문에 설치를 하지 않아도 사용가능

1.  가상환경 생성

   ```
   # 가상환경 만들 경로로 이동 후
   python -m venv 가상환경 이름
   ```

2.  가상환경 활성화

   ```
   가상환경이름\Scripts\activate
   ```

3.  이후는 virtualenv와 동일.



##### conda 사용

1. 가상환경 생성

   ```
   conda create -n 가상환경 이름
   ```

   - base와 동일한 환경의 가상환경을 만들 때 (예를 들어 base를 복사해서 test라는 이름에 가상환경을 만들고 싶으면)

     ```
     conda create --name pytorch --clone base
     ```

     

2. 가상환경 활성화

   ```
   activate 가상환경 이름
   ```

   * ``conda deactivate``로 가상환경 종료

* 가상환경을 **.yaml** 파일로 내보내서 저장을 할 수도 있고, 이를 활용해서 새로운 가상환경을 만들 수도 있다.

  - .yaml 파일로 저장

    ```
    conda env export > 가상환경 이름.yaml
    ```

  - .yaml 파일로 새로운 가상환경 만들기

    - 미리 저장해 둔 가상환경 설정을 그대로 가져와서 다른 이름의 동일한 가상환경 만들 수 있다.

    ```
    conda env create -f 가상환경 이름.yaml
    ```

* 가상환경 리스트 출력

  ```
  conda env list
  ```

* 가상환경 제거하기

  ``` 
  conda env remove -n 가상환경 이름
  ```

  

