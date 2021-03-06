# Nginx

엔진엑스(Nginx)는 웹 서버 프로그램이다. Apache보다 동작이 단순하고, 전달자 역할만 하기 때문에 동시접속 처리에 특화되어 있다.

동시접속자(약 700명) 이상이라면 서버를 증설하거나 Nginx 환경을 권장한다고 한다.



**아래는 알아야할 개념들**

## 프록시

서버와 클라이언트 사이에서 통신을 중계해주는 것을 말한다. 이러한 역할을 하는 서버를 프록시 서버라고 한다. 

캐싱을 지원해준다. 원래의 서버로 가지 않기 때문에, 네트워크 비용이 감소하고 응답속도가 빨라진다. 

프록시 서버에 들어오는 request, response을 filter할 수 있다. 

### 포워드 프록시

### 리버시 프록시

리버시 프록스는 클라이언트에서 들어오는 request를 프록시 서버(reverse proxy)가 받은 후 이를 Web Server(reverse server)로 보내주는 역할을 한다.  
여기서 프록시 서버가 Nginx, 리버스 서버가 응용프로그램 서버(Express 서버)를 의미한다.

리버스 포록시를 두면, 여러개의 요청이 들어왔을 때, 이를 로드 밸런싱해주어 reverse Server로 보내주어 부하를 줄여준다. 

웹 응용프로그램 서버에 리버스 프록시(Nginx)를 두는 이유는 요청(request)에 대한 버퍼링이 있기 때문이다. 클라이언트가 직접 App 서버에 직접 요청하는 경우, 프로세스 1개가 응답 대기 상태가 되어야만 한다. 따라서 프록시 서버를 둠으로써 요청을 배분하는 역할을 한다.

## Proxy 서버를 통한 무중단 배포  

Nginx 프록시 서버에서 요청을 받고 reverse server로 요청을 보내는데, Nginx가 port 80을 열어두고 reverse server는 다른 포트 (예를 들어 8080)을 열어둔다. 그러면 Nginx 서버의 80 포트로 들어온 요청을 reverse server로 보내준다.  

서버 프로그램을 돌리다가 수정을 해야할 때, 새로운 포트 8081로 프로그램을 돌린 후, Nginx를 8081 서버와 연결 시켜서 reload 시키면, 무중단 배포를 할 수 있다.


## 웹서버 vs WAS

Client -> 웹서버 -> WAS -> 웹서버 -> Client

### 웹서버

소프트웨어와 하드웨어로 구분되며, 하드웨어는 말 그대로 Web 서버가 설치되어 있는 컴퓨터를 말한다. 

그리고 소프트웨어 Web 서버란 브라우저 클라이언트로 부터 HTTP 요청을 받아들이고 HTML 등의 웹 페이지 문서에 반응하는 컴퓨터 프로그램이다. (Apache, Nginx)

HTTP 프로토콜을 기반으로 하여 브라우저의 요청을 서비스 하는 기능을 담당한다.

WEB 서버는 HTML 문서같은 정적 컨텐츠를 처리하는 것이다. (HTTP 프로토콜을 통해 읽힐 수 있는 문서)

### WAS(Web Application Server)

HTTP를 통해 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어(소프트웨어 엔진) 혹은 소프트웨어 프레임워크이다.   
동적 서버 콘텐츠를 수행한다는 것으로 일반 WEB 서버와 구별되며, 주로 데이터베이스 서버와 같이 수행된다.   

WAS 서버는 asp, php, jsp 등 개발 언어를 읽고 처리하여 동적 컨텐츠, 웹 응용 프로그램 서비스를 처리하는 것이다.