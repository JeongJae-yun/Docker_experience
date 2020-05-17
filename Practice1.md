## :punch:우분투 파일 시스템 연습해보기:punch:
          
#### [만들어 볼 파일 시스템 구조]
![image](https://user-images.githubusercontent.com/55985789/82142516-d62c9e80-9877-11ea-9000-b868ba8ccd89.png)

>## :one: 사용자 계정 만들기
>###  # adduser jeong
>>#### : jeong 이란 이름의 유저 생성하기.
>><img width="361" alt="5 jeong 유저 생성하기" src="https://user-images.githubusercontent.com/55985789/82141063-4df5cb80-986e-11ea-90a6-cd375daaa0e4.png">

>## :one:-:one: 사용자 계정에 sudo 사용 권한 부여.
>###  # usermod -aG sudo [유저 이름]
>>#### : jeong 유저에서 sudo 사용을 위해 권한을 부여한다.
>><img width="392" alt="7 jeong에서 sudo사용을 위해 권한 부여" src="https://user-images.githubusercontent.com/55985789/82141138-c492c900-986e-11ea-9f50-ef84f67cd982.png">

>## :one:-:two: 사용자 계정으로 스위칭.
>>###  # su joeng
>>#### : 사용자 계정 생성 했으니 root 계정에서 나의 계정으로 스위칭한다. (#->$로 바뀐다.)
>><img width="501" alt="1  나의 계정으로 바꿈" src="https://user-images.githubusercontent.com/55985789/82142569-3f141680-9878-11ea-9558-8ca0c91071da.png">


>## :one:-:three: 작업 수행을 위해 위치 이동하기.
>>###  $ cd ~
>>#### : cd ~ 로 jeong의 home 디렉토리로 이동한다.
>>### $ pwd
>>#### : pwd를 통해 현재 나의 위치를 파악할 수 있다.
>>#### 상단의 그림에서 USER/ = JEONG/ 으로 온 것이다.
>><img width="404" alt="2  cd ~로 jeong의 home으로 이동" src="https://user-images.githubusercontent.com/55985789/82142603-7f739480-9878-11ea-9e00-8469c8876565.png">

****                                                                                             
                                                                              
>## :two:	4개 디렉토리 생성하기
>>###  $ mkdir document (동일하게 download, workspace, bin도 생성)
>>#### : jeong 계정으로 4개의 디렉토리를 생성한다. 
>><img width="463" alt="3  jeong으로 4개 디렉토리 생성" src="https://user-images.githubusercontent.com/55985789/82142679-07f23500-9879-11ea-9eb6-ec82f0fd12ef.png">

****   
>## :three:	Workspace 디렉토리 아래 hello.txt 파일을 만든다 
>>###  $ cd workspace
>>###  $ touch Hello.txt
>>#### ls -l로 보면 txt파일에 대한 권한이 [-rw-rw-r--]로 jeong으로 생성 했기에 root와 같은 권한을 갖고 있다.
>><img width="448" alt="4  ws들어가서 Hello.txt 생성" src="https://user-images.githubusercontent.com/55985789/82142727-57d0fc00-9879-11ea-81bc-985407c18b69.png">


***
##### :wave:[추가적인 우분투 명령어 관련한 실습](https://github.com/JeongJae-yun/Docker_experience/blob/master/Ubuntu_1.md) :thumbsup:


