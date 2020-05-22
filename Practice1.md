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
>><img width="518" alt="1 4개디렉토리 생성하기 root로" src="https://user-images.githubusercontent.com/55985789/82623925-59edde80-9c1c-11ea-8ae8-cae68f3a934e.png">

****   
>## :three:	Workspace 디렉토리 아래 hello.txt 파일을 만든다 
>>###  $ cd workspace
>><img width="396" alt="2  workspace로 들어감" src="https://user-images.githubusercontent.com/55985789/82624037-a1746a80-9c1c-11ea-8761-c678405c837f.png">      

                             
>>###  $ touch Hello.txt
>>#### ls -l로 보면 txt파일에 대한 권한이  root로 되어있다.
>><img width="401" alt="3  Hello txt 만들기 root로" src="https://user-images.githubusercontent.com/55985789/82624116-c79a0a80-9c1c-11ea-8d0b-3fd2df87aea4.png">

>>###  $ sudo chown jeong:jeong Hello.txt
>>#### Hello.txt에 대한 권한을 jeong으로 바꾼다. 위와 다르게 권한이 jeong으로 바뀐것을 확인할 수 있다.
>><img width="502" alt="4 jeong으로 바꿈" src="https://user-images.githubusercontent.com/55985789/82624299-26f81a80-9c1d-11ea-9aba-f7dafa111ec0.png">




***
##### :wave:[추가적인 우분투 명령어 관련한 실습](https://github.com/JeongJae-yun/Docker_experience/blob/master/Ubuntu_1.md) :thumbsup:


