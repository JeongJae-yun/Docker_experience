# Docker..Experience              

* * *             

# Docker 기본 개념      
     
## *Docker?    
- 간단하게 생각하면 개발을 할 때, 고려해야할 설정 부분들이 많다.   
- version을 맞춰주는 것도 있고, vender에 따라 다르게 설정해야하는 부분들도 있다.      
- 이런 부분들에서 어떠한 개발환경에 있다 하더라도 호환성을 신경 쓰지 않고 서로 맞춰주기 위한 Tool. (나는 이렇게 이해했다)    
- 팀 프로젝트를 하더라도 각자 만든거를 누군가 일괄적으로 맞춰주면 편하듯..    
- 쉽게 패키징하여 쉽게 배포를 한다.      
- Docker는 Linux를 기반으로 한다. 그렇다보니 Open Source이고 현재도 계속해서 Develop이 진행중이다.    
         
<img width="112" alt="도커 로고" src="https://user-images.githubusercontent.com/55985789/80305893-c979d500-87fa-11ea-86a5-2932033b42f0.png">     
- 도커의 로고는 고래이다. 왜?       
- Docker는 컨테이너에 한 번에 설정 정보를 담아서 날라준다. 배달한다.      
- 고래가 정박해 있다가 물건을 실어나르듯 설정 정보에 맞춰 가져가는 것이다.     
       
# 특징       
> 초기 구축 시간을 줄인다. 
>> 많이 고려해야 할 부분들이 줄어든다.

## 컨테이너형 가상화 VS 하이퍼바이저형 가상화        
> 컨테이너형 가상화(Docker)        
>> HostOS와 공유한다. 실제 가상머신처럼 GuestOS를 실제로 설치하지 않는다.       
>> 최소한의 파일로 도킹을 한다.      
>> 어찌보면 HostOS에 의존적이다. = HostOS영향을 많이 받는다.          
>> IMG파일에 들어가있어서 용량이 적고 빠르다.       
>> 오버헤드가 거의 없다.      

> 하이퍼바이저형 가상화 <VM>      
>> Hypervisor위에 GuestOS를 설치한다.     
>> GuestOS위에 사용할 APP을 설치한다.      
>> Guest OS ? : Ubuntu, Centos,..etc.. 메모리, 공간 차지 힘들고 느릴수 있다. 컨테이너형 가상화에 비해!!            
>> 컨테이너형 가상화에 비해 오버헤드가 조금 있다.       
>> GuestOS는 HostOS에 독립적이다!!       

## VM(Virtual Machine) VS Docker     
VM(Virtual Machine) : 웹 호스팅을 하지 않는 이상 가상 머신 컨트롤 할 필요가 없다.      
Docker : 개발자, 서비스를 할 경우, 필요할 수 있다.            
                  
* * *                        
                              
## Docker 설치    
>1. https://www.docker.com/ 접속 or https://github.com/docker/toolbox/releases 깃허브     
>> 나의 경우, Github를 통해 Download       
>> <img width="578" alt="Docker설치1" src="https://user-images.githubusercontent.com/55985789/80305273-d268a780-87f6-11ea-9e77-b827c32191bd.png">    
>> DockerToolbox-19.03.01.exe 파일 Download    
    
>2. 여러번의 next끝에 Download를 하면 아래와 같이 3개의 아이콘이 생성된다.    
>> <img width="141" alt="Docker설치2" src="https://user-images.githubusercontent.com/55985789/80305391-4efb8600-87f7-11ea-87d2-37382fd76aa5.png">     
    
>3. image파일들을 모아서 제공해주는 Kitematic 사용(여전한 에러...처리중...)     
>> 우선 실행을 할 경우,      
>> <img width="909" alt="kite1" src="https://user-images.githubusercontent.com/55985789/80305459-c7fadd80-87f7-11ea-9fe7-9d023c7cd02b.png">    
>> 위와 같은 화면을 지나서          
>> <img width="849" alt="kite2" src="https://user-images.githubusercontent.com/55985789/80305607-b960f600-87f8-11ea-8d8c-5600567c60ef.png">     
>> 이 화면에서 Use VirtualBox를 눌러서 넘어가면 된다.       
>> 나는 현재 이 부분에서 SSH 관련한 Error가 무수히 발생하고 있다. 계속해서 찾아봐야겠다..      
>> Kitematic 실행 이전에 Docker를 먼저 실행하고 Kitematic을 실행하였을 경우, 이러한 에러도 발생한다.     
>> <img width="808" alt="kite3" src="https://user-images.githubusercontent.com/55985789/80305649-f2996600-87f8-11ea-8dd6-4502e3fa49ed.png">    
          
>4. Kitematic과 상관없이 위에서 보였던 3가지 아이콘 중 Docker Quickstarter Terminal을 누를 경우,      
>> <img width="730" alt="toolbox1" src="https://user-images.githubusercontent.com/55985789/80305591-8e76a200-87f8-11ea-804d-93f475cf4f79.png">      
>> 여러 세팅 글들을 지나서... 이렇게 귀여운 고래 모양이 나온다.    
     
>5. 도커 사용이 가능하니 몇가지 확인.     
>> 설정이라기 보단 기본적으로 어떤 것들이 있는지 볼 수 있다.
>> <img width="614" alt="docker설정1" src="https://user-images.githubusercontent.com/55985789/80305730-93882100-87f9-11ea-8962-65b1032d1064.png">    
>> 위의 그림 처럼, default로 Name이 설정되어 있고 URL도 설정이 되어있다. state 상태는 가동중이고 VirtualBox를 Driver로 하이퍼바이저로 사용중을 확인할수 있다.     
>> VirtualBox를 실행하여 확인해보면,     
>> <img width="958" alt="vm1" src="https://user-images.githubusercontent.com/55985789/80305793-17420d80-87fa-11ea-8a71-23c2345bb882.png">     
>> 좌측에 default라는 이름으로 실행 중.. 표시를 볼 수 있다.        
>> 가상머신(VM)이 실행이 되야 Docker도 가능하듯, Docker가 실행이 느릴경우, VM을 보면 진행상황을 알 수도 있다.     



