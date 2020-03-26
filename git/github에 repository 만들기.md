# github에 repository 만들기

- 이미 만들고자 하는 폴더와 파일이 있는 경우

- [참고사이트](https://emflant.tistory.com/135)

  

### 1. github 페이지

 1. **+** 버튼 누른 후 **New repository** 클릭

    <img width="132" alt="1 1" src="https://user-images.githubusercontent.com/59239352/77598851-3ffa8d00-6f46-11ea-8ec8-0304508da41e.PNG">

2. 필요한 구성 완성

   - **Repository name** : Repository 이름 설정
   - **Description** : Repository 설명
   - **Public / Private** : 누구나 볼 수 있게 / 지정한 사람만 볼 수 있게
   - **Initialize this repository with a README** : README.md 파일 만들지 여부

   <img width="434" alt="1 2" src="https://user-images.githubusercontent.com/59239352/77598884-5dc7f200-6f46-11ea-8bce-3b876d7d7229.PNG">

   

   

   ### 2. gitbash

   - 디렉토리를 만들고자 하는 폴더위치로 이동

     ```
     cd 만들고자 하는 폴더 위치
     ```

     

   - git repository로 생성하기

     ```
     git init
     ```

     

   - local repository를 origin이라는 이름의 remote repository와 연결하기

     ```
     git remote add origin 방금 만든 레파지토리 주소
     ```

     

   - 원격 저장소(github 사이트)에 있는 README.md 파일을 가지고 오기

     ```
     git pull origin master
     ```

     

   - Local repository에 있는 파일 commit 하기

     ```
     git add .
     
     git commit -m "first update"
     ```

     

   - git push의 기본값을 git push origin master로 지정

     ```
     git push -u origin master
     ```

     

<img width="486" alt="1 3" src="https://user-images.githubusercontent.com/59239352/77598895-6b7d7780-6f46-11ea-8cac-d31bd7f75017.PNG">