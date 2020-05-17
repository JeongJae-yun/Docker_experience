## 우분투 기본 명령어 연습하기          
#### 우분투 환경으로 들어와서 시작한다.               
#### 명령창에 $가 아닌 #이 있으면 된다.            

>###  # apt update && apt upgrade
>>#### : apt 명령어를 사용하여 root 권한 업데이트 및 업그레이드를 수행한다. 
>><img width="663" alt="1 ubuntu root권한 업데이트" src="https://user-images.githubusercontent.com/55985789/82140869-f1de7780-986c-11ea-814a-a1b97a3da476.png">

***
>###  # apt install vim
>>#### : VI에디터 사용을 위한 다운로드를 진행한다.
>><img width="946" alt="2 vi editor 사용을 위한 다운로드" src="https://user-images.githubusercontent.com/55985789/82140947-7af5ae80-986d-11ea-9353-2b9ed1fabad5.png">
>>아래와 같이 다운로드가 진행된다.               
>><img width="956" alt="3 vi editor 무서운 속도로 다운로드" src="https://user-images.githubusercontent.com/55985789/82140967-9fea2180-986d-11ea-8d48-7b70175193ec.png">

***
>###  # apt install net-tools
>>#### : ifconfig 명령어 사용을 위한 툴 다운로드
>><img width="879" alt="4 ifconfig 이용을 위한 툴 다운로드" src="https://user-images.githubusercontent.com/55985789/82140985-c3ad6780-986d-11ea-88a0-c916f502f949.png">

***
>###  # adduser [유저 이름]
>>#### : jeong 이란 이름의 유저 생성하기 (매우 직관적인 명령어들...)
>><img width="361" alt="5 jeong 유저 생성하기" src="https://user-images.githubusercontent.com/55985789/82141063-4df5cb80-986e-11ea-90a6-cd375daaa0e4.png">

***
>###  # su [유저 이름]
>>#### : root로 사용하다가 jeong으로 유저를 스위칭하는 명령어. (맨 앞이 root에서 jeong으로 변화 된 것을 확인할 수 있다.)
>>#### : su root를 쳐서 다시 root 권한으로 돌아오자!
>><img width="219" alt="6  유저 스위칭 jeong으로 바꿈" src="https://user-images.githubusercontent.com/55985789/82141084-77165c00-986e-11ea-9acd-ae0574e0eebc.png">

***
>###  # usermod -aG sudo [유저 이름]
>>#### : jeong 유저에서 sudo 사용을 위해 권한을 부여한다. (그래야 root로 su를 써서 갈 수 있지 않을까?)
>><img width="292" alt="7 jeong에서 sudo사용을 위해 권한 부여" src="https://user-images.githubusercontent.com/55985789/82141138-c492c900-986e-11ea-9f50-ef84f67cd982.png">

***
>###  # apt-get install sudo
>>#### : sudo 명령어 사용을 위한 apt install 
>><img width="582" alt="8 sudo 명령어 사용을 위한 apt install" src="https://user-images.githubusercontent.com/55985789/82141217-4edb2d00-986f-11ea-94f7-287bc7228d11.png">

***
>###  # sudo
>>#### : 설치 이후 sudo를 쳐본다. 가능한지 확인하여야 하기에! (저런식으로 help 명령어 들이 나오지 않는다면 설치가 되지 않은 것!)
>><img width="918" alt="9 설치 이후 sudo 쳐서 가능한지 확인" src="https://user-images.githubusercontent.com/55985789/82141236-6fa38280-986f-11ea-8c81-61aa74e769b8.png">

***
>###  # sudo passwd 
>>#### : sudo 패스워드를 설정한다.(여전히 직관적인 명령어..) 
>>#### : 그리고 비번을 칠때는 아무것도 안나온다. 입력안되나 하고 키보드 다시 안쳐봐도 된다..
>><img width="381" alt="10 sudo passwd 처리" src="https://user-images.githubusercontent.com/55985789/82141256-9d88c700-986f-11ea-8ebd-2840068fcd2f.png">

***
>###  # sudo touch joeng.txt
>###  # ls -l
>>#### : 빈 깡통 파일 jeong.txt를 만든다. 이후 ls -l로 만들어졌는지 확인! (root권한으로 실행되었다)
>><img width="430" alt="12  빈 깡통 파일 만들기 jeong" src="https://user-images.githubusercontent.com/55985789/82141340-15ef8800-9870-11ea-880e-e8e255b1551e.png">

***
>###  # sudo touch joeng.txt
>>#### : 방금 만든 txt파일은 root에만 권한이 있음을 확인할 수 있다. 
>>#### : (-rw-r--r--) <- 맨앞을 빼고 3자리씩 끊어서 [root권한/guest user권한/ other] 이렇게 보면 된다.
>>#### : root는 read, write 가능. guest,other는 read만 가능하다.!! 누가 만들었느냐에 따라 다른 권한을 갖는다.
>><img width="449" alt="13  방금 만든 txt root에만 권한있음 확인" src="https://user-images.githubusercontent.com/55985789/82141412-a037ec00-9870-11ea-8229-7f0b9ab252d9.png">

***
>###  # vi joeng.txt
>>#### : VI 에디터를 사용하여 txt파일에 들어간다. [권한을 jeong으로 스위칭 하고서 들어갔다!]
>><img width="255" alt="14  vi editor로 들어가서" src="https://user-images.githubusercontent.com/55985789/82141510-366c1200-9871-11ea-9db9-a3ebf82398a5.png">

***
>>#### : VI 에디터에서 아무거나 치고 저장을 누르면 에러가 뜬다. 
>>#### 에러명 : readonly option is set (add ! to override) = 읽기전용이란다.. 
>>#### readonly는 jsp에서 input태그에서 본적있다.
>>#### shift + z z 를 눌러서 나온다. 혹은 esc + q + ! 누르고 나온다.
>><img width="407" alt="14-1  아무거나 치고 저장 누르면 에러뜬다" src="https://user-images.githubusercontent.com/55985789/82141514-4a177880-9871-11ea-940c-f52d94ec5f5f.png">

***
>###  # vi joeng.txt
>>#### : VI 에디터 사용하여 txt파일 다시 들어가 본다. [권한을 root로 스위칭 하고서 들어갔다!]
>><img width="237" alt="15  root 권한으로 txt 접속" src="https://user-images.githubusercontent.com/55985789/82141685-87303a80-9872-11ea-9f20-b243b3d841af.png">

***
>>#### : VI 에디터 사용하여 글도 쓰고 저장도 된다. 에러도 안난다. root권한이라 가능하다.!
>><img width="363" alt="15-1  글 쓰고 저장 됨" src="https://user-images.githubusercontent.com/55985789/82141745-dd04e280-9872-11ea-94a3-6ad6a0f63818.png">

***
>>#### : 작성하고서 나오면 작성 이전과 달라져있음을 볼 수 있다. 0->21로 바뀌어져 있다. 
>><img width="570" alt="16  작성 후 달라짐을 확인" src="https://user-images.githubusercontent.com/55985789/82141767-06be0980-9873-11ea-9ee0-84b5a9f3f008.png">

***
>###  # sudo cat jeong.txt
>>#### : cat 명령어로 확인을 하면 아까 root로 작성한 hello world가 보인다. (cat은 미리보기같아서 파일 수정은 안된다.)
>><img width="408" alt="17 cat 명령어로 확인 시에 아까 쓴 helloworld보임" src="https://user-images.githubusercontent.com/55985789/82141901-95328b00-9873-11ea-807f-dd6f357012a2.png">

***
>###  # whoami
>>#### : whoami 명령어로 현재 접속자 권한이 누군지 알 수 있다. 권한을 바꿔가며 하다보면 헷갈릴 수 있으니..!
>><img width="177" alt="18  현재 접속자 누군지 whoami" src="https://user-images.githubusercontent.com/55985789/82141951-bbf0c180-9873-11ea-911d-4dba8f592d53.png">

***
>###  # mkdir cloud
>>#### : cloud라는 directory를 만든다. (파란색이라 잘 안보이지만 cloud가 만들어졌다)
>><img width="458" alt="19  mkdir cloud" src="https://user-images.githubusercontent.com/55985789/82141969-e3478e80-9873-11ea-9c87-16469707ca2a.png">

***
>###  # cd cloud
>>#### : cd이용해서 cloud 디렉토리로 이동해본다.
>><img width="220" alt="20  cd 이용해서 cloud로 이동" src="https://user-images.githubusercontent.com/55985789/82141985-08d49800-9874-11ea-815e-150e1bfa4b33.png">

***
>###  # rm sam*.txt
>>#### : rm을 이용해서 sam 붙은 txt를 지운다. sam*.txt을 할 경우, sam으로 시작하는 모든 txt이다.
>><img width="382" alt="20  rm 이용해서 sam 붙은 txt 지우기" src="https://user-images.githubusercontent.com/55985789/82142007-45a08f00-9874-11ea-9b50-5252c4cf6ba0.png">

***
>###  # ls -tl 
>>#### : 시간 순서대로 파일을 볼 수 도 있다. 항상 ls -l만 썻는데 t 붙이면 시간 순서!
>><img width="449" alt="21  시간순서대로 파일 보기" src="https://user-images.githubusercontent.com/55985789/82142035-83051c80-9874-11ea-9c79-f49d1aaeab86.png">

***
>###  # ls *.txt 
>>#### : 확장자가 txt인 애들만 골라볼수도 있다
>><img width="347" alt="22  확장자가 txt인 애들만 골라볼수도 있다" src="https://user-images.githubusercontent.com/55985789/82142056-9e702780-9874-11ea-8634-a2075bec5a07.png">

***
>###  # cp sample.txt pengsoo.txt
>>#### : cp를 이용하여 파일을 복사할수 있다. cp = copy | sample.txt = 기존파일 pengsoo.txt = 복사할 파일명 
>><img width="310" alt="23  cp  기존   바꿀이름" src="https://user-images.githubusercontent.com/55985789/82142071-b182f780-9874-11ea-9110-f9d7e4fa9882.png">

***
>>#### : 복사가 된 것을 확인할 수 있다. sample.txt와 pengsoo.txt가 모두 있다.
>><img width="327" alt="24  cp 된거 확인" src="https://user-images.githubusercontent.com/55985789/82142090-e2fbc300-9874-11ea-8d2e-2cac0f3ad6ed.png">

***
>###  # cp -i sample2.txt pengsoo.txt
>>#### : 복사 할 때 복사를 할 지 말지 물어 볼 수 도 있다. -i만 붙이면 된다. 
>>#### 잘못된 수정을 방지하기 위해 습관 들이는 것도 좋을 것 같다.
>><img width="338" alt="25  복사 시 물어보기" src="https://user-images.githubusercontent.com/55985789/82142150-484fb400-9875-11ea-8da2-1db39dc2db6a.png">

***
>###  # cp sample*.txt cloud
>>#### : 기존 txt파일들을 cp를 이용하여 cloud 디렉토리에 넣을 수 있다.
>>#### 일반 복사 할 때 작성하듯, 새로운 txt명 자리에 기존 directory명을 적으면 된다.
>><img width="287" alt="26  기존 txt파일들을 cp로 cloud에 넣기" src="https://user-images.githubusercontent.com/55985789/82142184-7af9ac80-9875-11ea-9474-7ee6ac1e129e.png">

***
>###  # mkdir cloud/young
>>#### : home directory에서도 cloud안에 mkdir할 수 있다. cloud안에 young이란 디렉토리를 만들었다.
>><img width="325" alt="27  홈 디렉터리에서 cloud안에 mkdir 하기" src="https://user-images.githubusercontent.com/55985789/82142222-b6947680-9875-11ea-8319-89ddf7a85a09.png">

***
>###  # mv sample2.txt tempprofile.txt
>>#### : mv를 이용하여 기존파일의 이름을 바꿀 수 있다. rename 방식으로 사용할 수 있다.
>><img width="379" alt="28  mv  기존파일   새로운파일" src="https://user-images.githubusercontent.com/55985789/82142249-e17eca80-9875-11ea-8b01-25208e829574.png">

***
>###  # rm -i [삭제할 파일명]
>>#### : rm을 이용할땐 = 파일 삭제 => -i를 써서 꼭 재확인해야한다.!!!!
>><img width="325" alt="29  rm 할땐 -i 꼭써라" src="https://user-images.githubusercontent.com/55985789/82142287-230f7580-9876-11ea-9d58-f86c8e2b30dc.png">

***
>###  # cat pro*.txt >> ordertest.txt 
>>#### : 이름에 꺽새(>>)를 써서 cat 출력 될 내용을 파일로 만든다.
>>#### pro로 시작되는 txt파일의 내용을 ordertest.txt로 만든다.
>><img width="351" alt="30  이름에 꺽새 를 써서 cat출력될껄 파일로 만들어라" src="https://user-images.githubusercontent.com/55985789/82142301-4508f800-9876-11ea-85e7-39b52b4be914.png">

***
>###  # cat -n sa*2.txt
>>#### : cat에 -n 을 붙이면 행 번호를 같이 출력해준다. 
>><img width="259" alt="31  cat에 -n을 붙이면 행번호 같이출력" src="https://user-images.githubusercontent.com/55985789/82142331-89949380-9876-11ea-9c85-541f69a8ed57.png">

***
>###  # more 1 sa*2.txt
>>#### : more를 쓰면 한 줄 씩 코드를 볼 수 있다.
>><img width="349" alt="32  more를 쓰면 한줄씩 보여준다" src="https://user-images.githubusercontent.com/55985789/82142354-b0eb6080-9876-11ea-8055-62528a22a4dd.png">

***
>###  # grep peng soo *
>>#### : grep을 통해서 특정 단어 하위디렉토리에 있는 지 검색할 수 있다.
>>#### peng과 soo가 하위에 있는지 찾았고 어떤 txt파일에 있는지 보여준다. 
>><img width="366" alt="33 grep을 통해서 특정 단어 하위디렉토리에 있는 지 검색" src="https://user-images.githubusercontent.com/55985789/82142375-d5dfd380-9876-11ea-9772-eb57aa815a84.png">

***
>###  # find -name '*.txt' | grep peng >> listfatch.txt
>>#### : find+grep 이용해서 모든 txt파일 중 peng이 있는 것을 listfatch로 저장한다.
>><img width="454" alt="34 find+grep 이용해서 찾아서 listfatch로 저장" src="https://user-images.githubusercontent.com/55985789/82142392-ff98fa80-9876-11ea-97dd-442bc7b94039.png">











































