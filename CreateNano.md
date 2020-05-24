## 💻Nano + Nginx 설치하기

#### 우선 docker start myubuntu / docker attach myubuntu 로 우분투에 접속하자.

***

>### $ apt-get install nano
>>#### : apt-get을 사용해서 nano를 설치한다. 근데? 시작부터 에러가 뜨네?
>><img width="803" alt="1  nano 에디터 다운받으려는데 뭔 에러가 뜸" src="https://user-images.githubusercontent.com/55985789/82751707-0f26bf00-9df4-11ea-8a12-676941fcdf6e.png">


### 🆖여기는 에러가 나는 사람만!!
>### $ apt-get install update
>>#### : 구글링을 통해 install을 update하라는걸 봐서 해보아도 여전히 에러가 남아있다.
>><img width="546" alt="2 구글링 통해 이걸해도 여전한 에러가 남음" src="https://user-images.githubusercontent.com/55985789/82751717-2a91ca00-9df4-11ea-8bdb-87b2bb05f08c.png">

>### $ echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
>>#### : apt-get install update를해도 에러가나서 구글링해보니 저걸 치면 된다해서 해보니 된다
>><img width="616" alt="3 apt-get update를해도 에러가나서 구글링해보니 저걸 치면 된다해서 해보니 된다" src="https://user-images.githubusercontent.com/55985789/82751754-717fbf80-9df4-11ea-9d30-8b4d7970e6e5.png">
##### 해결링크 ❗❗ https://m.blog.naver.com/PostView.nhn?blogId=cherrypeanut&logNo=221063230452&proxyReferer=https:%2F%2Fwww.google.com%2F

***
>### $ apt-get install nano
>>#### : apt-get install nano 다시!!
>>#### : 맨 마지막 줄에 여전한 warning이 있다. 오늘 에러 파티다...😥
>><img width="812" alt="4  apt-get install nano 또 뭔에러가 뜨네" src="https://user-images.githubusercontent.com/55985789/82751853-1bf7e280-9df5-11ea-8284-db93ac94cde9.png">

### 🆖다시 저런 warning이 뜬 사람만!!
>>#### : 구글링을 통해 apt-utils를 설치하면 된다는 글을 보았다. 함 해보자.
>><img width="542" alt="5 apt-utils를 설치해보자" src="https://user-images.githubusercontent.com/55985789/82751918-8c066880-9df5-11ea-951e-afd00b81efb6.png">

##### 해결링크 ❗❗ https://qastack.kr/superuser/413463/catch-22-need-apt-utils-to-install-apt-utils
***

>>## $ apt-get install nano
>>#### : 저 명령어만 3번째.. Nano 설치 이미 되어 있고 다른 이상 현상 없다. 이제서야 나노를 설치했네..
>><img width="516" alt="6  음 나노 이미 설치되어있고 다 되었다고 이제 나온다 휴 안심 ㅎ" src="https://user-images.githubusercontent.com/55985789/82751962-e7385b00-9df5-11ea-8901-9c709cfabd08.png">


## Nano 사용하기
>>#### sample.txt를 touch로 만들고 이렇게 nano를 이용하여 sample.txt를 적어 볼 수 있다.
>><img width="727" alt="7 이르캐 nano이용해서 sample txt에 적어본다" src="https://user-images.githubusercontent.com/55985789/82751993-1949bd00-9df6-11ea-9f84-6171adec77b6.png">


>>#### ctrl+O 를 누르면 아래 화면이 뜨고 enter를 누르면 반영이 된다.
>><img width="714" alt="8 ctrl+o 를 누르면 저렇게 뜨고 enter 누르면" src="https://user-images.githubusercontent.com/55985789/82752015-3e3e3000-9df6-11ea-8085-bb479346f0de.png">


>>#### 위의 사진에서 enter를 누르면 이렇게 나오고 여기서 ctrl+X를 눌러서 exit하자!
>><img width="720" alt="9 이르케 나오고 ctrl+x 써서 빠져나온다" src="https://user-images.githubusercontent.com/55985789/82752040-6e85ce80-9df6-11ea-8c1a-c40626048073.png">


#### 📆 nano가 vi에디터 보다 훨씬 편하다. vi 에디터는 들어가서도 작성하려면 insert누르고..무튼 할게많다.


* * *
***

## Nginx 설치하기
> ### $ docker pull nginx 
>> #### : nginx 사용하려면 image파일 받아오듯이 pull로 땡겨온다.
>><img width="604" alt="10 우선 nginx 이미지 설치" src="https://user-images.githubusercontent.com/55985789/82752118-d0463880-9df6-11ea-92d3-a46e4e53a617.png">

> ### $ docker container run --name webserver -d -p 80:80 nginx
>> #### : run을 이용해서 create->start->attach 다 해줄 수 도 있다.
>>> #### : --name 이미지 이름 네이밍 (webserver)
>>> #### : -p 포트번호 설정
>>> #### : 앞에 80은 host머신의 포트
>>> #### : 뒤에 80은 nginx컨테이너의 포트 번호
>>> #### : nginx : 받아올 이미지
>><img width="599" alt="11  한번에 docker run" src="https://user-images.githubusercontent.com/55985789/82752146-f7046f00-9df6-11ea-88e7-d7d355234b68.png">

> ### $ docker ps -a 
>> #### : webserver = nginx가 up으로 변경된 것 확인! 귀찮아도 꼭 해보자.
>><img width="715" alt="12 docker ps -a로 up된거 확인" src="https://user-images.githubusercontent.com/55985789/82752200-595d6f80-9df7-11ea-8c35-c61aeb6f1781.png">


> ### VM VirtualBox로 가서 포트포워딩을 해줘야한다.
>> #### : 설정-> 네트워크 -> 포트포워딩 규칙에서 우측에서 +를 누르고 아래와 같이 작성한다. http 127.0.0.1 80 80 
>><img width="943" alt="13 vm에서 설정 들어가서 네트워크들어가서 포트포워딩 들어가서 추가 누르고 http 우분투 ip넣어주고 8080 맞춰주면 끝" src="https://user-images.githubusercontent.com/55985789/82752214-7134f380-9df7-11ea-9213-feeaa4f8c583.png">


> ### $ docker container rename webserver nginxserver
>> #### : webserver에서 nginxserver로 이름을 좀 바꿨다. 
>><img width="537" alt="14 websesrver에서 이름 바꿈" src="https://user-images.githubusercontent.com/55985789/82752256-b527f880-9df7-11ea-8fae-4f8d591aa675.png">


### 👀Next : [ubuntu말고 debian으로 해보자](https://github.com/JeongJae-yun/Docker_experience/blob/master/CreateDebian.md)



