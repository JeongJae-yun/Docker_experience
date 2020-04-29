# Docker 다뤄보기!      
## 간단한 명렁어 파악하기       

###  $ docker info        
#### : 서버에 컨테이너가 몇개 올라와 있는지 등 기본 정보를 알 수 있는 명령어.      
<img width="800" height="500" alt="docker info" src="https://user-images.githubusercontent.com/55985789/80590927-b6b00c00-8a57-11ea-9079-33fd83088289.png">

###  $ docker version        
#### : 도커 버전 확인 하는 명령어  
<img width="834" alt="docker version" src="https://user-images.githubusercontent.com/55985789/80592679-cbda6a00-8a5a-11ea-9f98-a6faf59123a7.png">


###  $ docker --help          
#### : 쉽게 생각하여 도움말 명령어이다. 리눅스와 다른 식으로 명령어를 사용하기에 알아두면 유용하게 쓰일 듯 싶다.            
<img width="800" alt="docker help" src="https://user-images.githubusercontent.com/55985789/80591378-946abe00-8a58-11ea-8460-8f246b48ffe9.png">

###  $ docker ps          
#### : Docker의 프로세스를 알 수 있는 명령어. (현재는 실행중인 컨테이너가 없지만 이후 과정에선 여러 차례 확인 해볼 수 있는 명령어이다.)
<img width="803" alt="docker ps" src="https://user-images.githubusercontent.com/55985789/80591514-cbd96a80-8a58-11ea-9ff3-a1843f27d6e8.png">

###  $ docker machine ls          
#### : Docker 머신에 관련한 정보들을 볼 수 있는 명령어. (default라는 이름으로 running중을 볼 수 있고 VM에서 사용 중인 ip도 확인 할 수 있다.)    
<img width="800" alt="docker-machine ls" src="https://user-images.githubusercontent.com/55985789/80591658-017e5380-8a59-11ea-8f92-8fa9b9aa6e58.png">

###  Windows의 CMD창에서 ipconfig 입력을 할 경우,
#### : HostOS가 쓰고 있는 ip 주소와 빨간 박스의 VM이 쓰고 있는 ip주소를 볼 수 있고 둘은 다르다.
#### : 이 ip주소는 위의 도커 머신에서도 볼 수 있었다. 별도의 머신으로 분리된 것을 확인할 수 있다.
<img width="628" alt="cmd창 도커" src="https://user-images.githubusercontent.com/55985789/80591905-794c7e00-8a59-11ea-9914-071446214369.png">

###  $ ps -ef
#### : 커널 프로세스를 제외하고 보여주는 명령어.
<img width="654" alt="ps -ef" src="https://user-images.githubusercontent.com/55985789/80592083-cfb9bc80-8a59-11ea-959d-d01037d49918.png">

###  $ docker images
#### : 실행중인 도커 이미지를 볼 수 있는 명령어. (현재 실행 중인 image가 없어 보이지 않는다.)
<img width="856" alt="docker images" src="https://user-images.githubusercontent.com/55985789/80592184-f7108980-8a59-11ea-8291-954e2ba3d670.png">


### +이외에.

### Docker의 Windows(HostOS) 상에서의 위치
#### default이름의 vm이 만들어져서 실행이 된다. 
<img width="960" alt="docker 물리적 위치" src="https://user-images.githubusercontent.com/55985789/80592825-0e03ab80-8a5b-11ea-9526-5b0f23a04154.png">


***
## Docker 더 다뤄보기!

>### $ docker rename [컨테이너 이름] 
>>#### : 컨테이너 이름 변경하는 명령어.
>>>#### : myubuntu를 yourubuntu로 변경하였다.
>>><img width="814" alt="마이우분투를 유어우분투로 리네임" src="https://user-images.githubusercontent.com/55985789/80593891-f4636380-8a5c-11ea-9a6c-068a07936648.png">
>>>이름 바꾼 후 $ docker ps -a로 프로세스를 체크해보면 name이 yourubuntu로 바뀐 것이 보인다.
>>><img width="838" alt="이름 바꾼 후 실행 해보고 실행 상태 체크" src="https://user-images.githubusercontent.com/55985789/80593937-07763380-8a5d-11ea-95d7-fdea2b8c31b3.png">
>>>바뀌기 전 이름인 myubuntu로 실행 시 에러가 나타난다.
>>><img width="742" alt="바뀌기 전 이름으로 실행 시 에러!!" src="https://user-images.githubusercontent.com/55985789/80594065-4d32fc00-8a5d-11ea-9207-9b92d1eb208d.png">

### $ docker rm [컨테이너 이름]
#### 조심해서 써야한다. 함부로 삭제는 위험하다. 저기 -f를 붙여 실행 중에도 강제삭제를 할 수 있으나 몰라도 된다.
<img width="656" alt="컨테이너 삭제" src="https://user-images.githubusercontent.com/55985789/80594398-dfd39b00-8a5d-11ea-8cb5-9d09a49a03ff.png">


***
## Docker에 익숙해지기
### $ 컨테이너 실행 후 실행 상태 확인 (up으로 바뀜)
<img width="764" alt="컨테이너 실행 후 실행 확인" src="https://user-images.githubusercontent.com/55985789/80594180-853a3f00-8a5d-11ea-9563-668a4256d84b.png">

### $ 컨테이너 종료 후 종료 확인 (exit으로 바뀜)
<img width="750" alt="컨테이너 종료 후 종료 확인" src="https://user-images.githubusercontent.com/55985789/80594254-a4d16780-8a5d-11ea-87ea-532c48b71a05.png">


















