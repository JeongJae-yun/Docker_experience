# ☁ DockerHub 실습하기
****

### 📝실습의 순서

#### :one: (nano+nginx가 포함된) Docker file작성✍(공유폴더를 이용하여!) ➡ 권한을 수정하자!                        
#### :two: ⚒ Build Image ➡ image가 생성 될 것                                
#### :three: Container 생성!! ➡ localhost 확인하면 돼!! 🖥nginx화면 확인하면 돼!!                                
#### :four: 📤 push로 docker hub에 올리기!! ➡ (물론 이거 전에 id/pw 이용하여 docker hub 계정 생성 되야 해 )                                
#### :five: docker hub에서 push된 image 확인해보기!!  ➡ 끝!!✔                               

***

### 실습 전에💨

#### 우리는 지금까지 늘 모든 과정을 환경이 바뀔때마다 매번 해줬었다.
> $ apt update                          
> $ apt upgrade                          
> $ apt install vim                          
> $ apt install nano                          
> $ apt install net-tools                          
> $ apt install sudo                          
> $ apt install nginx                          
#### 이런 단순 작업을 작업 환경이 바뀔 때마다 하면 얼마나 비효율적인가💢💢

***

### 그래서 우린 basic image를 하나 두고 그 위에 
#### ➕ Nginx ➕ Nano ➕ Vi ➕ etc
#### ➡ 이렇게 한번에 하고자 한다.✔

*** 

### 한 번에 묶어서 만들면 뭐가 좋을까⁉
#### 우선, 단순 반복 작업을 해주지 않아도 된다.
#### 그리고, 허브에 올려서 내가 어디에 있던 상관없이 내려 받아 사용 가능하다.

***
## 즉, 나만의 기능이 있는 이미지를 클라우드에 올려두자.📤☁
### 누구나 접속이 가능한게 클라우드니까!! 그냥 어디서든 내려받음 되자나!! 이게 진정 클라우드지!! 
### 이 방법이 무엇이냐❔  Dockerfile ❗❗

***
## Dockerfile 만들려면 기본 명령어 정도는 알아야지!
| 명령어 | 의미 |
|----------|------------|
| FROM  | BASE IMAGE(주요 이미지). ubuntu에 얹을건지. debian에 얹을건지. 살을 붙일 뼈대가 되는 이미지 |
| MAINTAINER | 누가 지금 만드는지. 흔적을 남기자. 저작권자! |
| RUN  | shell scirpt실행!! install을 run으로 실행시켜줌 |
| VOLUME | 같이 작업 디렉토리를 공유하고자하는 볼륨 |
| WORKDIR | 프롬프트 실행하는 위치. 도커파일의 위치!! 어디서할건지! |
| EXPOSE | port번호 적어줄것 있으면 여기다 해줌 돼. expose 80 이런식 |
| ENV | 환경변수 설정할거 있음 하면돼 |

### 밑에서 실습하다보면 정확히 이해가 될 것이다.

*** 
***
***

# 실습을 해보자💥

## :one: (공유폴더를 이용하여!) (nano+nginx가 포함된) Docker file작성 

#### 우선적으로 공유폴더를 이용하여야 하는데 공유폴더가 뭐지? 
#### 💯 공유폴더 = host os(window)와 Docker Engine(linux)가 공유하는 폴더!
>### Docker에 들어가서 들어가자마자 pwd를 쳐보면 이상하게도 C드라이브가 나온다.
><img width ="800" height="400" src="https://user-images.githubusercontent.com/55985789/84292327-336af580-ab81-11ea-9e88-0a350d79ff47.png">                                  


>### 신경쓰지 않던 부분인데 과연 저게 정말 C드라이브인가 확인해보자.
><img width ="800" height="400" src="https://user-images.githubusercontent.com/55985789/84292724-b4c28800-ab81-11ea-9f19-2bd56816e18c.png">                                   

>### 정말 동일하다!!

### 근데 공유가 어찌 가능할까?🧐
#### 정답은 Oracle VM을 보면 된다!! 설정의 공유폴더에 이미 지정되어 있다! Default로!
<img width ="800" height="500" 
src="https://user-images.githubusercontent.com/55985789/84292972-184cb580-ab82-11ea-86b1-2366a59ebc7f.png">                                   

***
### 다시 돌아와서! 공유 폴더가 C밑에 User밑에 라는 걸 알았다!!
>> #### 저 경로에 Docker 폴더를 하나 만들거다!! 관리자 권한이 필요하다니 계속을 눌러주자!
>> <img src="https://user-images.githubusercontent.com/55985789/84293365-a2951980-ab82-11ea-826b-5f4142097c98.png">    

>> #### 폴더의 이름을 Docker라고 해주고!! 관리자 권한을 계속 눌러주자!
>> <img src="https://user-images.githubusercontent.com/55985789/84293640-0ae3fb00-ab83-11ea-9fd0-7e9d740384ca.png">

>> #### 한가지 더!!✅
>> #### Docker텍스트 파일 권한을 바꿔주자!
>> #### Docker 텍스트 파일의 속성에 들어가서 보안-편집-Users를 누르고 수정/쓰기를 모두 허용해주자!
>> <img src="https://user-images.githubusercontent.com/55985789/84293857-50082d00-ab83-11ea-8ebe-9a6b06116e91.png">

>> #### 이걸 해줘야 수정/쓰기 할 수 있고 그래야 공유폴더가 의미 있는 것이다.

***

* ### Docker 폴더에 들어가서 Docker 텍스트 파일을 만들자!! 이게 Dockerfile이다!!
<img src="https://user-images.githubusercontent.com/55985789/84294105-a5443e80-ab83-11ea-9fd9-94921900b99e.png">
 
* #### 근데 txt확장자는 없애야 한다! 근데? 확장자가 안 보인다면!
<img src="https://user-images.githubusercontent.com/55985789/84294202-d02e9280-ab83-11ea-8ec7-a3d3d27726d1.png">

* #### 이렇게 상단에서 보기- 숨김 목록에서! 파일 확장명을 체크하자! 그리고 txt를 지우자!
<img src="https://user-images.githubusercontent.com/55985789/84294398-0ff57a00-ab84-11ea-9758-bed60f63b2e0.png">

* #### 지우고 나서 예!! 누르면 된다!! 

***
### 드디어 Dockerfile 작성한다.
<img src="https://user-images.githubusercontent.com/55985789/84294529-43380900-ab84-11ea-974b-f0ddf72d2b82.png">

* ### 위의 그림처럼 적어주자!! 토씨하나 틀리지않게.🆗🈁
***
* ### 그리고 Docker로 돌아와서 공유폴더에 들어가보면 Docker폴더가 있고 안에 txt파일이 있다!! 확인하자✅
<img src="https://user-images.githubusercontent.com/55985789/84294745-914d0c80-ab84-11ea-94e9-56f63fba7d01.png">

* ### vi editor로 들어가서 메모장에서 적은 내용이 맞나 확인해보자.
<img src="https://user-images.githubusercontent.com/55985789/84294973-eab53b80-ab84-11ea-9373-3af715d07ee3.png">

### ➡ 정확하게 똑같다!! 이제 반은 한거다!!


***
***
***
***
## :two: ⚒ Build Image
> ### $ docker build --tag mydocker:0.1 
> #### mydocker라는 이름으로 0.1버전으로 build를 시키자! 뭐가 엄청 나온다..
> <img src="https://user-images.githubusercontent.com/55985789/84400244-c3ba4080-ac3c-11ea-86ce-bbeedc23d56c.png">

> #### 마지막 부분에 가보면 나온다!! success✅
> <img src="https://user-images.githubusercontent.com/55985789/84400461-0714af00-ac3d-11ea-9f6e-26443f556383.png">

> #### docker images를 해서 확인해보면 mydocker가 들어있다!!😁
> <img src="https://user-images.githubusercontent.com/55985789/84400592-31ff0300-ac3d-11ea-876e-3fdee68d729c.png">



***
***
### 우린 mydocker image를 한번에 생성 하는 파일을 공유폴더 이용하여 만들었고 실행시켰고 이제 run만 하면 된다❗❗(간편)
***
***
## :three: Container 생성하자!!
#### $ docker run --name mydocker-svr -d -p 80:80 mydocker:0.1
* #### 이름은 mydocker-svr로 실행시키고 daemon으로 포트는 80으로 포워딩하고 실행시킬 image는 mydocker:0.1 버전이다!
<img src="https://user-images.githubusercontent.com/55985789/84400862-8ace9b80-ac3d-11ea-95e9-f9a35429fb17.png">

* ### docker run 했으니 up되었는지 확인해보자!
<img src="https://user-images.githubusercontent.com/55985789/84401418-37a91880-ac3e-11ea-9d8c-a94cbbb41bd3.png">

#### 되어있다. 성공✅

* ### 이제 뭘 해야겠어? 포트포워딩 해서 run한거면 당연히 nginx 작동 잘 되는지 봐야지. localhost치자💨
<img src="https://user-images.githubusercontent.com/55985789/84401631-763ed300-ac3e-11ea-94fb-ccb02b847160.png">

#### 잘 돌아간다. 성공✅

***
***
***
***
## :four: push로 docker hub에 올리기!! 

***
#### 일단 무엇보다 도커 허브에 계정이 있어야 한다. 많은 거 요구 안하니 가입하고 이메일 인증하자!!
#### 🖐 참고로 이메일 인증 안하면 계속 오류 날 수 있다. 꼭 인증하고 이용하자!!
#### ☝ 하나 더! 내 아이디/비밀번호 까먹지말자! 이따가 docker에서 인증을 요구할 것이다.
<img src="https://user-images.githubusercontent.com/55985789/84402294-375d4d00-ac3f-11ea-884d-f5767baa012a.png">

***

* ### 아마 처음 가입하고 repositories 들어가보면 이렇게 빈.. 화면이다. 이제 시작하면 된다.
<img src="https://user-images.githubusercontent.com/55985789/84402571-8d31f500-ac3f-11ea-9a9a-cba56763343e.png">

* ### 도커 허브에 올리기 위해 우선 내 계정 밑에 다시 만들자. 무슨 말이냐고?
### $ docker build --tag wodbs135/mydocker:0.1   ⬅  아까 한 빌드를 내 계정 밑에 하면 된다.
<img src="https://user-images.githubusercontent.com/55985789/84401842-b56d2400-ac3e-11ea-98b4-1647ca3e1433.png">

* ### $ docker images를 통해 내 계정 밑에 또 생성 된 것을 볼 수 있다.✅
<img src="https://user-images.githubusercontent.com/55985789/84403107-47c1f780-ac40-11ea-892a-52ef2bf56e0b.png">

***

* ### 도커에 로그인 하자!!
### $ docker login 치면 아까 hub에서 가입한 ID/PW를 요구한다. 기억했겠지..😂
<img src="https://user-images.githubusercontent.com/55985789/84403264-78099600-ac40-11ea-9b0d-849ba6db92c7.png">

### $ docker push wodbs135/mydocker
* ### push라는 직관적인 단어로 나의 docker에서 docker hub로 올려준다.📤 
* ### 즉, 이젠 다른 사람들도 내가 만든 나만의 도커 쓸 수 있다. 이 말이다🈁
<img src="https://user-images.githubusercontent.com/55985789/84403454-b010d900-ac40-11ea-8df0-51e4457bf9be.png">

### 트루인지 도커 허브가서 확인하자!!🧐
<img src="https://user-images.githubusercontent.com/55985789/84403808-14cc3380-ac41-11ea-89d8-84ce49cd46da.png">

### 올라와있다.😊. 오늘 목표는 성공적이다. 끝❗❗
#### 🙋‍♂️참고로. push하고서 바로 가서 보면 안 보일 수 있다. 깃헙도 그렇듯 어느정도 격차를 두고 가서 확인해보자.

***
***
***
🗯💬💭
#### 여지껏 직접 하나 하나 만들던 걸.. 한 번에 모아서 해결하니 너무 속 시원하다.
#### 오늘 실습에서 기억 할 건, 진정한 의미의 클라우드 = 도커 허브에 내가 직접 Dockerfile을 만들어서 올린 것!!
#### 그리고 그것을 남들도 사용할 수 있고 나도 어디서든 다운 받아 사용 가능하다는 것👌
#### 실습을 따라하는 것도 중요하지만 내가 치는 하나하나가 어떤 의미를 갖는지 기억하는 게 더 중요하다고 생각한다.👨‍💻

#### 많이 쌓인 공부 흔적들이..[도커 실습 기록](https://github.com/JeongJae-yun/Docker_experience)👋 헛되지 않게😂 



