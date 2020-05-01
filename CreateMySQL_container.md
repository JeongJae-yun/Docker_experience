
## Docker에서 MySQL Download             
***
### $ docker pull mysql
: 우선 MySQL을 ubuntu 다운 받았던 것 처럼 다운로드를 받아야 하기에 pull로 mysql image를 받아온다.              
: mysql 옆에 버전을 따로 명시하지 않을 경우, 항상 최신버전을 다운로드 받는다.             
<img width="763" alt="1 docker pull mysql" src="https://user-images.githubusercontent.com/55985789/80792315-298fc300-8bcf-11ea-9ef3-3143dfa72523.png">

***
### $ docker images
: 다운 받은 MySQL이 잘 다운로드 되었는지 확인한다.
<img width="748" alt="2 docker images(설치후 확인)" src="https://user-images.githubusercontent.com/55985789/80792375-517f2680-8bcf-11ea-8eb7-a0b406139144.png">

***
### $ docker run -d --name [하고자 하는 이미지 이름] -p 3306:3306 MYSQL_ROOT_PASSWORD=[설정 할 비밀번호] [받아올 이미지]
: 명령어가 좀 길지만 다 이유가 있다.        
-d : daemon으로 db 백그라운드 처리가 가능하게 명시해주는 명령어.                   
-p : 어떤 port로 통신을 주고 받을지 설정하는 명령어.                    
-e : 계정 설정에서 root의 비밀번호를  설정하고 들어갈 때 사용한다. 이는 뒤에서 따로 설정 할 수도 있다.            
<img width="775" alt="3 Mysql설정" src="https://user-images.githubusercontent.com/55985789/80792427-6c519b00-8bcf-11ea-8531-4ca1059aa647.png">

***
### $ docker ps -a 
: 우분투 설치 할 때도 여러 번 사용한 명령어이다.     
: 현재 프로세스에 대해서 볼 수 있다. 
<img width="942" alt="4 docker ps -a로 up된거 확인" src="https://user-images.githubusercontent.com/55985789/80792636-e4b85c00-8bcf-11ea-917b-0b8ae480d4d9.png">
: 지난번에 깔아둔 ubuntu와 방금 설치한 MySQL이 있고 up상태로 되어있다.

***
### $ docker exec -it [mysql 컨테이너 이름] bash
exec :  host에서 컨테이너안의 mysql을 실행시키는                
-i : interactive 방식으로 다루겠다.. 이건 우분투 설치할때도 있었다.                
-t : 리눅스 기반의 bash 쉘을 이용하겠다.                
<img width="794" alt="5 docker exec -it mysqltmp bash" src="https://user-images.githubusercontent.com/55985789/80792673-074a7500-8bd0-11ea-9f53-2684fcdea0ee.png">

***

## MySQL다루기
***
### $ mysql -uroot -pcloud
: root user로 접근
: 비밀번호 생성을 안했을 경우, -p를 붙여서 비번 생성하여 접근이 가능하다. 
<img width="768" alt="6 mysql -uroot -pcloud" src="https://user-images.githubusercontent.com/55985789/80792782-5395b500-8bd0-11ea-9921-fe5fa1c820fd.png">

***
### 여기서부턴 MySQL로 진입하였으니 모든 명령어 끝에 ;를 붙여야한다.
### 간혹 캡쳐 사진에 깜빡하고 그냥 엔터를 눌러서 다시 ;를 치는 부분들이 있다..!
***
### mysql> show database;
: 맨 처음 실행 후, 데이터베이스를 보려고 할때 기본적으로 default로 내용이 담겨있다.
: 이 부분에 대해선 root권한으로 들어왔다 하더라도 건들지 말자.
<img width="586" alt="7 show databases" src="https://user-images.githubusercontent.com/55985789/80792818-6b6d3900-8bd0-11ea-8608-f4b9c618f261.png">

***
### mysql> create database [만들고자 하는 DB이름];
### mysql> show databases;                     
: DB생성 후, 잘 만들어진 것인지 확인한다.                            
: 모든 단계에서 각 단계별 확인하는 작업이 중요한 것 같다.                   
: 나중에 다~ 하고서 확인하면 어디서 잘못 설정한건지 모를 수 있으니..!!                     
: 그래서 show databases 같은 명령어들이 기본적이지만 잘 알아둬야한다.                  
<img width="571" alt="8 create database cloudtmp" src="https://user-images.githubusercontent.com/55985789/80792927-ae2f1100-8bd0-11ea-90d6-068d4aa05686.png">

***
### mysql> use [방금 만든 DB이름];
: 방금 만든 DB를 사용하겠다는 명령어.                
#### : 이걸 쓰지도 않고 테이블을 생성하여 데이터 입력하고 그럴 경우, default로 지정된 db에 저장이 될 수 있다.!!                   
<img width="539" alt="9 방금만든 db에 접속 use cloudtmp" src="https://user-images.githubusercontent.com/55985789/80793181-62c93280-8bd1-11ea-9fcf-ed7dfa9c641e.png">


***
### mysql> show tables;
: 습관적으로 확인하자.
: 현재 DB에 만든 테이블이 없으니 empty가 당연하다.
<img width="508" alt="10 현재 만든 테이블이 없다" src="https://user-images.githubusercontent.com/55985789/80793269-a02dc000-8bd1-11ea-800b-3eb90efed5e2.png">

***
### mysql> create table [테이블 이름] 
( id varchar(10) not null primary key,
name varchar(20) not null,
age int(3) not null);                        
: 단순하게 id,name,age 정도만 있는 테이블을 생성하였다.                  
: primary key는 꼭 int로 쓰고 auto increment를 할 필요 없다!.               
#### : varchar로 쓰고 primary key만 해두자. 실제 필드에서도 가능하단다!!
<img width="567" alt="11  mysql create table kpuuser" src="https://user-images.githubusercontent.com/55985789/80793308-be93bb80-8bd1-11ea-88a5-b5197b1645a4.png">

***
### mysql> show tables;
: 방금 만든 테이블이 잘 들어있다.
<img width="646" alt="12  방금 만든 테이블 확인" src="https://user-images.githubusercontent.com/55985789/80793494-3b269a00-8bd2-11ea-9b15-e4c0aefad143.png">

***
### mysql> desc [테이블 이름];
: 방금 만든 테이블의 전체 정보 확인이 가능하다.            
: 컬럼명, 타입, 널 허용 유무 등등...            
<img width="671" alt="13 만든 테이블 정보확인 desc" src="https://user-images.githubusercontent.com/55985789/80793544-5db8b300-8bd2-11ea-8516-065516c25259.png">


***
### mysql> insert into kpuuser (id,name,age) values ('1','son',28);
### mysql> select * from kpuuser;
: id 1번에 이름 son에 나이 28로 데이터 하나 입력 후 조회하였다.          
: 너무 간단한 내용이지만 이런 기본적인게 제일 중요하다.          
<img width="601" alt="14  데이터 입력후 들어간지 확인" src="https://user-images.githubusercontent.com/55985789/80793595-8640ad00-8bd2-11ea-8f9b-e60ddbaec1d0.png">

***
### mysql> 이외에도 많은 데이터를 넣어보았다.
<img width="649" alt="15 이외에도 많은 데이터 넣어봄" src="https://user-images.githubusercontent.com/55985789/80793749-ef282500-8bd2-11ea-9860-0936c760b835.png">

***
### mysql> select * from kpuuser where age > 30;
: 나이가 30 이상인 데이터만 조회해보았다.           
: 어쩌면 단순할 수 있는 쿼리 문들이지만 손에 익어서 기계적으로 나오게 하는게 중요한 것 같다.          
<img width="696" alt="16 간단한질의select30이상" src="https://user-images.githubusercontent.com/55985789/80793827-2696d180-8bd3-11ea-8bb5-e4ca468e5120.png">


                
              
***
### MySQL의 경우, TODD나 Workbench와 같은 편리한 툴을 사용하지 않고 
### command line에서 처리하기에 에러 처리 부분에서 답답한 부분이 있다. 
### syntax에러의 경우, error 넘버가 나오니 구글링을 통해 에러 안나오게..!!







