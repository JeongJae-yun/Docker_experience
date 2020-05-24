## 💥Debian Nginx에 PHP 연동하기

***

> ## # apt-get install php7.3 php-mysql php-fpm php-cli php-mbstring
>> #### : php7.3버전, mysql, fpm, cli, mbstring을 같이 설치해준다.
>><img width="855" alt="1 php7 3버전 설치 및 기타 같잇 설치" src="https://user-images.githubusercontent.com/55985789/82752986-0edef180-9dfd-11ea-8d26-35fb6f39bfa9.png">

***
### 지난번 html위치를 보기위해 들어간 default파일에 다시 들어간다.
>### # cd /etc/nginx/sites-available/default 
>> #### 아래 사진의 빨간 부분에서 흰 부분만 #을 없애준다. 주석 처리를 지워준다. 
>><img width="687" alt="2  sites-available밑에 default에 들어가서 저 빨간 네모의 흰 부분만 #을 없애준다" src="https://user-images.githubusercontent.com/55985789/82753013-51083300-9dfd-11ea-99cc-662500eefd3b.png">

>> #### 같은 파일에서 좀 내려와서 접근 권한과 관련된 부분도 주석을 없애준다.
>><img width="706" alt="3  default파일에 접근권한 부분에 대해서도 주석 해제" src="https://user-images.githubusercontent.com/55985789/82753049-a2182700-9dfd-11ea-8f1f-6880f70d662a.png">

***
### cd /etc/php/7.3 으로 이동해주자
>### 아래 사진처럼 cli하고 fpm이 보일텐데 우선 부터 고쳐주자!! 어차피 동일하다
>><img width="544" alt="4  etc에php에7 3 들어가서 cli, fpm에서 ini파일 2개 고쳐줄것" src="https://user-images.githubusercontent.com/55985789/82753062-be1bc880-9dfd-11ea-9cdf-f9b7e43e15c7.png">

### # nano php.ini
>### php.init파일에 nano로 들어간다.
>><img width="501" alt="7 앞의 두예제의 위치" src="https://user-images.githubusercontent.com/55985789/82753154-88c3aa80-9dfe-11ea-8dce-bc411a9067b7.png">

:one:-:one:
>### Ctrl + Shift + -를 눌러서 192라인으로 가서 아래 사진 처럼 on으로 고쳐준다. 
>><img width="726" alt="5  php ini파일에 nano로 들어가서 ctrl+shfit+-를 눌러서 라인 찾기 해서 192번라인에 가서 short_open_tag 를 open으로 바꿔줌" src="https://user-images.githubusercontent.com/55985789/82753086-f02d2a80-9dfd-11ea-9fb2-3c0cde04277f.png">

:one:-:two:
>### Ctrl + Shift + -를 눌러서 793라인으로 가서 아래 사진 처럼 0으로 고쳐준다. 
>><img width="753" alt="6  php ini파일에서 793라인에 cgi fix_pathinfo1을 를 없애준다  주석없애는개념" src="https://user-images.githubusercontent.com/55985789/82753129-4c904a00-9dfe-11ea-9fa2-febecfffca34.png">

***
***
### 이제 cli에 가서 수정하자!!
><img width="544" alt="4  etc에php에7 3 들어가서 cli, fpm에서 ini파일 2개 고쳐줄것" src="https://user-images.githubusercontent.com/55985789/82753062-be1bc880-9dfd-11ea-9cdf-f9b7e43e15c7.png">

### # 아래의 경로로 들어간다.
>### php.init파일에 nano로 들어간다.
>><img width="560" alt="8  cil파일에 들어가서 다음작업" src="https://user-images.githubusercontent.com/55985789/82753172-a5f87900-9dfe-11ea-9df1-5fccbb0b3e56.png">

:one:-:one:
>### Ctrl + Shift + -를 눌러서 192라인으로 가서 아래 사진 처럼 on으로 고쳐준다. 
>><img width="735" alt="9 위에서한것과 동일하게 php ini파일에 192라인 바꾸기" src="https://user-images.githubusercontent.com/55985789/82753216-ebb54180-9dfe-11ea-81e2-4e460e7f9d92.png">

:one:-:two:
>### Ctrl + Shift + -를 눌러서 793라인으로 가서 아래 사진 처럼 0으로 고쳐준다. 
>><img width="732" alt="10 위와 동일하게 793라인 주석해제 0으로바꿈" src="https://user-images.githubusercontent.com/55985789/82753220-f4a61300-9dfe-11ea-8ffe-ae63de17f0d7.png">

***
> #### 다시 default 설정 파일로 가보면 socket 파일 위치가 run/php 이다. 
>> <img width="719" alt="11  다시 default파일로 가보면 socket파일 위치가 run밑 php밑이다 가보자" src="https://user-images.githubusercontent.com/55985789/82753234-1901ef80-9dff-11ea-9701-eb70c287abcd.png">

> #### 그러나 위의 경로에 가보면 php파일이 존재 하지 않는다. ❌
>><img width="604" alt="12  run밑에 php파일이 없다" src="https://user-images.githubusercontent.com/55985789/82753247-3636be00-9dff-11ea-8421-658b1cd7c1cd.png">

### 그럼 어디에⁉

> ## # service nginx restart
>> #### 우리가 설정들을 여러개 바꾸었으니 nginx를 restart해줘야 한다.
>><img width="667" alt="13 그렇다면 nginx를 리스타트하자" src="https://user-images.githubusercontent.com/55985789/82753272-62ead580-9dff-11ea-97f1-d39f19e20247.png">

> ## # service php7.3-fpm start
> ## # service php7.3-fpm restart
>> #### 또한 php설정-fpm을 변경하였으니 start한적 없는 php도 start -> restart해주자
>><img width="675" alt="14  fpm을 수정했으니 여기도 스타트 리스타트 해주자" src="https://user-images.githubusercontent.com/55985789/82753296-8746b200-9dff-11ea-8075-c98524418832.png">

> #### 다시 socket파일 위치에 가보면 위에서 없던 php파일이 생겼다.
>><img width="608" alt="15  12에선 없던 run이 생겼다  리스타트 해주었기에" src="https://user-images.githubusercontent.com/55985789/82753314-9af21880-9dff-11ea-8e3d-bcc1a0b4d475.png">

> #### 들어가서 확인해보면 socket파일도 들어있다.
>><img width="611" alt="16  php들어가보면 socke파일이 들어있다" src="https://user-images.githubusercontent.com/55985789/82753350-d68ce280-9dff-11ea-9786-1285b82ba86c.png">

***
## 설정은 끝났다. 이제 php사용해서 진짜 서버에 올려보자👌
> ### default파일에 html파일들이 있는 곳에 php를 추가해주자!! 우리 php로 쓸거니까!
>><img width="681" alt="18  그전에 php 파일 만들어서 실행할거기에 index에 php넣어주자" src="https://user-images.githubusercontent.com/55985789/82753380-0a680800-9e00-11ea-8047-0c7ebfaa0b71.png">

> ## cd /var/www/html
>> #### 그럼 이제 default파일에 명시되어 있는 지난번 html 수정한 위치로 가보자.
>><img width="659" alt="17  default파일에 명시되어잇는 html위치로 가보자" src="https://user-images.githubusercontent.com/55985789/82753366-ead0df80-9dff-11ea-82e8-a9a87cc2317b.png">

> ## touch test.php
>> #### html이 있는 위치에 와서 php파일을 하나 만들어보자
>> <img width="698" alt="19  html이 있는 위치로 와서 test php를 만들어보자" src="https://user-images.githubusercontent.com/55985789/82753412-53b85780-9e00-11ea-9817-56d764cb541a.png">

> ## Oh Happy Day ~
>> #### php를 사용하여 간단하게 적어주고 나오자. 아무거나 적어보았다!
>><img width="722" alt="20  단순하게 적어주고" src="https://user-images.githubusercontent.com/55985789/82754090-9e889e00-9e05-11ea-971a-a86fc10c6a8a.png">


> ## localhost:80/test.php
>> #### 실행시켜보면 입력해둔 그대로 나온다!!!
>><img width="691" alt="21  웹서버 test php 실행시켜보니 제대로 나온다" src="https://user-images.githubusercontent.com/55985789/82754102-b4965e80-9e05-11ea-8f5b-2cfd931defb3.png">

***
👨‍💻 debian(linux) + nginx(웹스테이션) + php(사용언어) = 생각보다 복잡한 과정을 거쳐서 하나의 결과물이 나왔다.             
💭 여전히도 의문점들이 많기에 차근차근 복습을 하면서 내용을 조금씩 더 추가해나가야겠다.
