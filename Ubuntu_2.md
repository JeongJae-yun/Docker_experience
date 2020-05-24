## :computer:우분투 기본 명령어 연습하기 2  


### 오늘은 리눅스 권한에 대해 알아볼 것!

***
### Linux 큰 특징
>#### 1. multi user 허용!
>#### 2. 보안이 중요! -> 사용자 권한, 소유권에 대한 기능이 철저하게 분리 되어있다.
>#### : 파일, 디렉토리에 소유자, 그룹, others 각각의 권한을 분리해서 관리한다.    
									
																		
																											
***
### 파일, 디렉토리에 R,W,X 권한 별도 생성 가능!                                        
>### :one: Owner(소유자)                         
>>#### : 파일 주인 : <login해서 파일, 디렉토리를 생성한 계정>
>>#### : root라면 root, jeong이라면 jeong
 			
>### :two: group(소유그룹)
>>#### : 계정들이 특정 그룹으로 묶일 수 있다. (소유권 관리 비교적 잘 되어있다.)
>>#### : $groups 명령어로 확인 가능하다. 밑에서 해볼 것.

>### :three: others
>>##### : 특정 디렉토리나 파일이 소유자도 아니고 같은 그룹도 아니면 제 3자라고 할 수 있다.
>>#### : 소유자 jeong 그룹 jeong 인데 다른 계정으로 들어가면 소유자도 그룹도 아닐때는 제 3자가 된다. 일반적으로 read만 가능.

***
### 권한을 볼  수 있는 방법
>>### ◾ d rwx rwx r-x   jeong   jeong   test
| (0) d | (1) rwx |(2) rwx |(3) r-x |(4) jeong | (5) jeong | (6) test |
|:----------|:----------|:----------|:----------|:----------|:----------|----------|
| d: directory | 소유자 권한 표기 | 소유 그룹의 권한 표기 | others 권한 표기 | 소유자  | 소유 그룹 |  파일(디렉토리) |
| ㅣ : 링크 |||||||
| - : 파일 |||||||
### (1),(2),(3) : read/ write /execute 권한

*** 
## 권한변경 : 소유자 계정 또는 root 계정만 할 수 있다.
> ### :one: 영문자 chmod 
>> ### $ chmod u-x test : test 디렉토리의 소유자 권한(u) 중 x 권한을 제거(-)
>> #### (u:소유자, g:소유그룹, o:others)
>> #### (-, + )
>> #### (r,w,x)
>> #### 연습) chmod go+rwx text : test 디렉토리의 소유그룹(g)과 제3자(o)에게 rwx 권한 부여

> ### :two: 숫자(2진수 표기법 이용) : rwx rwx rwx
>> #### 4,2,1 = rwx 
>> #### 표시 : 사용가능 1, 사용 불가능 0
>> #### 101 : 5(rx만 가능), 110 : 6(rw만 가능) ...
>> #### 연습) $chmod 777 test : 소유자 ->7, 소유그룹->7, others->7 : 모두 다 가능하게 만든다.
>> #### 연습) $chmod 555 test : 모두 rx만 가능하게 한다.


### 혹시라도 2진수 -> 16진수 변환이 헷갈릴 수 있으니 참고할 수 있게 적어둬야겠다.🆗

| linux 표기 | 2진수 표기| 16진수 표기 |
|:----------:|:----------:|:----------:|
| --- | 000 | 0 |
| --x | 001 | 1 |
| -w- | 010 | 2 |
| -wx | 011 | 3 |
| r-- | 100 | 4 |
| r-x | 101 | 5 |
| rw- | 110 | 6 |
| rwx | 111 | 7 |

***

## 이제 docker켜서 실습 해보자!

***
 
>###  '$ docker start myubuntu'
>>#### : 실행시 ubuntu로 들어간다. start로 up을 시켜두고 attach로 들어간다.
>><img width="524" alt="1 실행시 우분투로 입장" src="https://user-images.githubusercontent.com/55985789/82750014-56a74e00-9de8-11ea-8a0d-24539857f72b.png">
>###  $ docker attach myubuntu
>><img width="525" alt="2  ps-a로 up된거 확인할 필요 없이 바로 attach로 우분투 입장" src="https://user-images.githubusercontent.com/55985789/82750027-69218780-9de8-11ea-98e5-607e1e132720.png">


>###  $ groups
>>#### : 나의 그룹이 어디인지 확인할 수 있다. root->root / jeong -> jeong
>><img width="406" alt="3 groups 어딘지 확인" src="https://user-images.githubusercontent.com/55985789/82750059-a71eab80-9de8-11ea-9764-8c7339d486af.png">


>###  $ mkdir sample
>>#### : sample이라는 디렉토리! 를 jeong권한으로 만들어본다.
>><img width="533" alt="4 home디렉토리에 sample디렉토리만들고" src="https://user-images.githubusercontent.com/55985789/82751195-8fe3bc00-9df0-11ea-9754-cee480cfb33e.png">

>###  $ chmod o+w sample
>>#### : sample에 대해서 other그룹에 write 권한을 준다. 내가 jeong으로 들어왔기에 가능하다.!!
>>#### : 없던 write권한이 생긴걸 볼 수 있다.(r-x -> rwx)
>><img width="556" alt="5 chmod로 sample에 대한 others권한 write줌 바뀜" src="https://user-images.githubusercontent.com/55985789/82751220-b7d31f80-9df0-11ea-86d6-647ea9eaa286.png">


>###  $ touch jeong.txt
>>#### : 이번엔 sample 디렉토리 안에 txt파일을 만들고 권한을 확인해보자(jeong으로 만들었다)
>><img width="545" alt="6 sample안에 jeong txt만들고 권한확인" src="https://user-images.githubusercontent.com/55985789/82751258-fa94f780-9df0-11ea-9587-d148f03ffbdc.png">

>###  $ chmod u+x jeong.txt
>>#### : jeong.txt에 대해서 user(소유자)에게 exec 권한을 부여한다.
>><img width="503" alt="7 jeong txt에 user에 x권한을 부여 확인" src="https://user-images.githubusercontent.com/55985789/82751269-14363f00-9df1-11ea-9266-389f76046d75.png">

>###  $ chmod 777 jeong.txt
>>#### : 2진수 777 = rwx 모두 활용해서 권한을 바꿔보았다. 
>><img width="506" alt="8 2진수 777활용해서 권한 바굼" src="https://user-images.githubusercontent.com/55985789/82751324-5790ad80-9df1-11ea-809f-7ce932ea5f59.png">

***

TODAY🌈🕔😮 
##### window에서 파일 권한 변경하려면 GUI환경이라서 클릭 몇번으로 하던걸 코드로 리눅스 환경에서 해보니 색다르다. 
##### 권한 변경 방법이 2가지가 있었는데 개인적으로는 아직까진 어느쪽이 더 편하다는것 보단 둘 다 익숙해져보는게 먼저 일 것 같다.
 





