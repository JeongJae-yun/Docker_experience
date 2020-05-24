## 🔥Debian을 설치하자

***

> ## $ docker run -it --name debserver -p 80:80 debian:buster
>> #### : 이것은 지난번 nginx 설치 시에도 봤었다.
>> #### : run을 사용하여 create부터 attach까지 한번에 할 것이며 debserver이름을 줄 것.
>> #### 포트포워딩의 경우, 지난번에 해두었기에 또 vm가서 설정할 필요 없다.
>><img width="591" alt="1 run으로 attach까지 데비안 설치" src="https://user-images.githubusercontent.com/55985789/82752347-5f078500-9df8-11ea-8dd5-ac7021ef892f.png">

##### 참고로 debian :buster 버전은 가장 최신 버전이다.

> ## $ docker attach debserver 
>> #### : debian에서 exit으로 나온 후, attach를 사용해서 들어가려하면 에러가 난다.
>> #### : 왜? start를 안해줬기에 에러가 난다. run이 다 했었기에 exit하면 다시 처음부터 해야한다.
>><img width="578" alt="2  데비안에서 exit으로 나온 뒤에 attach로 들어가려하면 안된다  왜냐면 start를 해줘야하기에" src="https://user-images.githubusercontent.com/55985789/82752444-0389c700-9df9-11ea-92a4-f30d55c706de.png">

> ## Ctrl + P , Q
>> #### ⛏위에서의 문제를 해결할 방법은 exit으로 나오는게 아닌 ctrl+p,q를 치고 나오면 up 상태에서 잠깐 나오게 된다.
>> #### 그러면 start -> attach로 들어가지 않고 attach로 바로 들어갈 수 있다.
>><img width="700" alt="3  ctrl+p,q 하고 나오면 exit하고 나올때랑 다르다  up이 된 상태에서 잠깐 나온거다 그러니 start, attach해서 다시 안들어가도 된다" src="https://user-images.githubusercontent.com/55985789/82752464-33d16580-9df9-11ea-8a5e-095e7ad4851c.png">

***
## 이제 정말 설치하자!

> ## # apt update
>> #### 가장 처음 apt update를 해주자!
>><img width="568" alt="4 apt update 처음에 해주기" src="https://user-images.githubusercontent.com/55985789/82752505-7bf08800-9df9-11ea-8af8-9fa01c41b913.png">

***
## ⁉근데 apt가 뭐지?   ❗❗ Advanced Package Tool
#### apt : pacakge가 있을 경우 
#### apt-get  : apt 패키지까지 다 같이 받는 경우.
*** 
   
> ## # apt upgrade
>> #### update이후엔 꼭 upgrade 
>><img width="542" alt="5 apt upgrade" src="https://user-images.githubusercontent.com/55985789/82752596-06d18280-9dfa-11ea-8520-d6907d07a96a.png">

> ## # apt install vim
>> #### vi에디터도 설치해주자!!
>><img width="538" alt="6 vim 에디터 설치" src="https://user-images.githubusercontent.com/55985789/82752604-18b32580-9dfa-11ea-87fa-1d67b20434f4.png">

> ## # apt-get install nano
>> #### nano가 편하니 나는 nano를 쓸것이다. nano도 설치해주자
>><img width="529" alt="7  nano 에디터 설치" src="https://user-images.githubusercontent.com/55985789/82752632-3da79880-9dfa-11ea-840f-1e66bcecf36b.png">

> ## # apt-get install net-tools
>> #### 통신 패키지도 설치해주자! 
>><img width="528" alt="8  통신 패키지 설치" src="https://user-images.githubusercontent.com/55985789/82752639-5748e000-9dfa-11ea-8549-ba41666b2039.png">


> ## # apt-get install sudo
>> #### sudo 사용을 위해서 설치해주자.
>><img width="564" alt="9  sudo 사용을 위한 설치" src="https://user-images.githubusercontent.com/55985789/82752657-79daf900-9dfa-11ea-97d0-35723c6de709.png">

> ## # apt-get install nginx
>> #### 우리가 사용할 web station = nginx 설치하자.
>><img width="595" alt="10 nginx설치" src="https://user-images.githubusercontent.com/55985789/82752667-90815000-9dfa-11ea-81ed-ef1099d4d195.png">


> ## # service nginx start
>> #### 서버,DB도 그렇듯 우리가 실행시켜줘야 한다. nginx도 실행시켜주자.
>><img width="585" alt="11  nginx service start" src="https://user-images.githubusercontent.com/55985789/82752683-b870b380-9dfa-11ea-8b3d-77e1e5053281.png">

>> #### 인터넷을 키고 url에 localhost:80을 쳐보면 service가 제대로 실행되고 있다.
>><img width="722" alt="12  실행시켜보면 이렇게 뜬다  localhost실행" src="https://user-images.githubusercontent.com/55985789/82752707-e2c27100-9dfa-11ea-8942-a82dcf44331f.png">

> ## # cd /etc/nginx/sites-availble
>> #### 위의 경로에 가면 default라는 nginx 초기화면 세팅 정보가 있다.
>><img width="591" alt="13  저 경로에 가면 nginx 초기화면 세팅 정보가 있다" src="https://user-images.githubusercontent.com/55985789/82752716-fe2d7c00-9dfa-11ea-8198-e970d21a59bb.png">

> ## # vi default
>> #### 들어가보면 html들이 나열된 부분이 있다.
>> #### 위에는 root /var/www/html 로 아마 html파일들이 들어있는 경로지 않을까?
>><img width="481" alt="18  default파일에 html을 넣어주면 그게 실행되겠지" src="https://user-images.githubusercontent.com/55985789/82752835-d0950280-9dfb-11ea-9c3e-38b7a1d77f35.png">

> ## # cd /var/www/html 
>> #### 위의 경로에 가면 초기화면 html이 들어있다. default에서 맨 마지막에 있던 html이 있다.
>><img width="521" alt="14  세팅파일 html은 저기 경로에 있다" src="https://user-images.githubusercontent.com/55985789/82752744-2b7a2a00-9dfb-11ea-9d7d-67721ba12dc1.png">

> ## vi index.nginx-debian.html
>> #### 들어가보면 html이 구성되어있다. 
>><img width="581" alt="15 들어가보면 구성되어있다" src="https://user-images.githubusercontent.com/55985789/82752762-58c6d800-9dfb-11ea-8787-5765ed243813.png">


>> #### 그럼 과면 이 HTML이 정말 초기화면으로 동작하는지 보기 위해서 코드를 수정해보겠다.😁
>><img width="514" alt="16  저부분을 바꿔보겠다" src="https://user-images.githubusercontent.com/55985789/82752799-8c096700-9dfb-11ea-90b0-173cd1249829.png">


>> #### 다시 localhost:80에 가보면 정말 바뀌어져 있다!!!
>><img width="813" alt="17  오 바뀌었다홈페이지" src="https://user-images.githubusercontent.com/55985789/82752821-b65b2480-9dfb-11ea-8277-b35e18343349.png">


***
#### 📑ubuntu가 아닌 debian에 설정을 하였고 이전에 설정해둔 nginx를 붙여서 서버도 올려보았다.
#### 📝Next : [PHP를 연동해서 서버에 올려봐야지](https://github.com/JeongJae-yun/Docker_experience/blob/master/Usingphp.md)




















