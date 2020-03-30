# Keras 설치

- [Reference site](http://needjarvis.tistory.com/424)



#### 1. 파이썬 설치 시 **Anaconda**를 사용하여 설치

- [Anaconda 설치방법](https://needjarvis.tistory.com/170)

#### 2. Anaconda 설치 후 **cmd** 창을 열어서 명령어를 입력한다. 

```
C:\Users\910S>conda list
```

- **conda list**를 실행하면, 아나콘다로 설치한 패키지 목록들이 나오게 되는데 케라스가 있는지를 확인해 본다.

```
jpeg                      9b                   hb83a4c4_2
json5                     0.8.5                      py_0
jsonschema                3.0.2                    py37_0
jupyter                   1.0.0                    py37_7
jupyter_client            5.3.3                    py37_1
jupyter_console           6.0.0                    py37_0
jupyter_core              4.5.0                      py_0
jupyterlab                1.1.4              pyhf63ae98_0
jupyterlab_server         1.0.6                      py_0
keras                     2.2.4                         0
keras-applications        1.0.8                      py_0
keras-base                2.2.4                    py37_0
keras-preprocessing       1.1.0                      py_1
keyring                   18.0.0                   py37_0
kiwisolver                1.1.0            py37ha925a31_0
krb5                      1.16.1               hc04afaa_7
lazy-object-proxy         1.4.2            py37he774522_0
libarchive                3.3.3                h0643e63_5
libcurl                   7.65.3               h2a8f88b_0
libiconv                  1.15                 h1df5818_7
liblief                   0.9.0                ha925a31_2
libmklml                  2019.0.5                      0
libpng                    1.6.37               h2a8f88b_0
libprotobuf               3.9.2                h7bd577a_0
libsodium                 1.0.16               h9d3ae62_0
```

- keras를 설치하였을 때 패키지 리스트이며 없을 경우 다음 명령어를 실행한다.

```
C:\Users\910S>conda install keras
```

- 위와 같이 아나콘다를 설치 하고, 뒤이어 **conda install keras**를 수행하여 케라스를 설치하였다면 기본적으로 케라스는 텐서플로우를 디폴트(default) 엔진으로 사용이 가능해진다.

```
C:\Users\910S>python
Python 3.7.1 (default, Dec 10 2018, 22:54:23) [MSC v.1915 64 bit (AMD64)] :: Anaconda, Inc. on win32
Type "help", "copyright", "credits" or "license" for more information.

>>> import keras
Using TensorFlow backend.
```

- 위와 같이 cmd창을 열어 "python"을 직접 입력 후, import keras를 입력하면, "Using TensorFlow backend."라는 문구가 표시가 되는 것을 볼 수 있다.  
- 완료!!

