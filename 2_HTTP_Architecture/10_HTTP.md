## 10장 :octopus: HTTP/2.0

### 10.1 　  HTTP/2.0의 등장 배경　 `hylee`
1. 다음 문장에서 빈칸에 들어갈 단어로 알맞은 것은? <br>
    > HTTP 2.0은 주로 HTTP/1.1의 _________ 문제를 해결하기 위해 나왔다.
   
    a. 구현의 단순성
    
    b. 성능
    
    c. 접근성
    
2. HTTP/1.x 에서 HTTP/2가 되면서 바뀐 것을 모두 고르시오

    a. HTTP 의미 체계(예: 동사, 메서드 및 헤더)
    
    b. 의미 체계가 인코딩되는 방식

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 다음 문장에서 빈칸에 들어갈 단어로 알맞은 것은? <br>
    > HTTP 2.0은 주로 HTTP/1.1의  ` b.성능 ` 문제를 해결하기 위해 나왔다.
               
2. HTTP/1.x 에서 HTTP/2가 되면서 바뀐 것을 모두 고르시오.

    a. HTTP 의미 체계(예: 동사, 메서드 및 헤더)
    
    b. 의미 체계가 인코딩되는 방식
    
    > 정답 : b
    
     > HTTP/2의 모든 성능 향상 중 핵심은 새 바이너리 프레이밍 계층인데 이 계층은 HTTP 메시지가 캡슐화되어 클라이언트와 서버 사이에 전송되는 방식을 규정합니다.
     이런 변화를 통해 HTTP 의미 체계(예: 동사, 메서드 및 헤더)는 영향을 받지 않지만 전송 중에 이 의미 체계가 인코딩되는 방식은 달라졌습니다.
     줄바꿈으로 구분되는 일반 텍스트 HTTP/1.x 프로토콜과 달리, 모든 HTTP/2 통신은 더 작은 메시지와 프레임으로 분할되며, 각각은 바이너리 형식으로 인코딩됩니다.<br>
     <출처> <br> (https://developers.google.com/web/fundamentals/performance/http2?hl=ko#%EB%B0%94%EC%9D%B4%EB%84%88%EB%A6%AC_%ED%94%84%EB%A0%88%EC%9D%B4%EB%B0%8D_%EA%B3%84%EC%B8%B5)

 
</div>
</details>
<br>

### 10.2 ~ 10.3 　  개요 ~ HTTP/1.1과의 차이점　 `hylee`
1.  HTTP/2.0에서 모든 메시지는 _______ 에 담겨 전송된다.


2. 스트림과 멀티 플렉싱에 대해 옳은 것을 모두 고르시오.

    a. 하나의 커넥션에서 여러 개의 스트림을 동시에 열 수 있고 이를 통해 응답 순서에 상관없이 데이터를 주고 받을 수 있다.

    b. 스트림은 우선순위를 가질 수 있다.

    c. 스트림을 만들 때 서버와 클라이언트는 빠르게 TCP패킷을 주고 받음으로써 스트림을 만들 수 있다.
    
    
    
3. 빈칸에 들어갈 내용은? 
    > HTTP/2에서는 _______ 압축 형식을 사용하여 요청 및 응답 헤더 메타 데이터를 압축합니다.
    
    
    
4. Stream 3의 HEADERS frame에 들어갈 내용 적으세요.

    ![헤더_문제](https://user-images.githubusercontent.com/44167177/90633426-fb5aef80-e260-11ea-84df-455bcb271985.png)
    
    

5. 서버푸시를 통해 서버는 원래 요청에 응답할 뿐만 아니라 클라이언트가 명시적으로 요청하지 않아도 서버가 추가적인 리소스를 클라이언트에 보낼 수 있다. ( O  / X )

     <img src="https://images.velog.io/images/jehjong/post/a7a3817e-e07d-48a2-a203-cf3ac0c9c3d0/Frame%201.svg" style="zoom:100%;" />
     
     
     
6. 모든 서버 푸시 스트림은 ____________ 프레임을 통해 시작되며 이 프레임은 푸시된 리소스를 요청하는 응답 데이터보다 먼저 전달되어야 합니다.



7. 6 번에서 해당 프레임이 먼저 전달되어야 되는 이유는?

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1.  HTTP/2.0에서 모든 메시지는 `프레임` 에 담겨 전송된다.


2. 스트림과 멀티 플렉싱에 대해 옳은 것을 모두 고르시오.

    a. 하나의 커넥션에서 여러 개의 스트림을 동시에 열 수 있고 이를 통해 응답 순서에 상관없이 데이터를 주고 받을 수 있다.

    b. 스트림은 우선순위를 가질 수 있다.

    c. 스트림을 만들 때 서버와 클라이언트는 빠르게 TCP패킷을 주고 받음으로써 스트림을 만들 수 있다.
    
    > 정답 : a, b <br>
      c 에서 서버와 클라이언트는 스트림을 상대방과 협상 없이 일방적으로 만든다. 이는 스트림을 만들 때 협상을 위한 TCP패킷을 주고받는 시간을 낭비하지 않아도 됨을 의미한다. (p. 291)
    
3. 빈칸에 들어갈 내용은? 
    > 정답 : HTTP/2에서는 `HPACK` 압축 형식을 사용하여 요청 및 응답 헤더 메타 데이터를 압축합니다.
    
    
    
4. Stream 3의 HEADERS frame에 들어갈 내용 적으세요.

    ![헤더_정답](https://user-images.githubusercontent.com/44167177/90634245-5e00bb00-e262-11ea-89f9-ebb8816bcebd.JPG)
    
5. 서버푸시를 통해 서버는 원래 요청에 응답할 뿐만 아니라 클라이언트가 명시적으로 요청하지 않아도 서버가 추가적인 리소스를 클라이언트에 보낼 수 있다. ( O  / X )

     <img src="https://images.velog.io/images/jehjong/post/a7a3817e-e07d-48a2-a203-cf3ac0c9c3d0/Frame%201.svg" style="zoom:100%;" />
     
    >  정답 : `O` <br> 이는 클라이언트가 HTML 문서를 파싱해서 필요한 리소스를 다시 요청하여 발생하게 되는 트래픽과 회전 지연을 줄여준다.
     
6. 모든 서버 푸시 스트림은 `PUSH_PROMISE` 프레임을 통해 시작되며 이 프레임은 푸시된 리소스를 요청하는 응답 데이터보다 먼저 전달되어야 합니다.

7. 6 번에서 해당 프레임이 먼저 전달되어야 되는 이유는?
    > 정답 : 서버가 푸시하려고 하는 자원을 클라이언트가 별도로 또 요청하게 되는 상황을 피하기 위함이다. (= 리소스에 대해 중복 요청이 생성되는 것을 막기 위해서)

</div>
</details>
<br>


### 10.4 　  알려진 보안 이슈　 `kukim`
1. HTTP/2.0 메세지를 중간의 프락시가 HTTP/1.1 메세지로 변환할 때 메세지가 변질 될 수 있다  (O/X)
2. ɑ+🔥) 캡슐화 공격이란 무엇인가?
3. HTTP/2.0은 HTTP/1.1과 달리 스트림과 멀티플렉싱을 통해 효율적으로 통신할 수 있다. 이때 발생할 수 있는 보안 이슈는 무엇인가?

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. HTTP/2.0 메세지를 중간의 프락시가 HTTP/1.1 메세지로 변환할 때 메세지가 변질 될 수 있다  (O/X)
- 정답 : O (CR,LF,Null 문자 등을 잘못 처리하여 헤더와 메세지를 구분하지 못하게 될 수 있다. 이런 취약점을 가지고 공격하는 것을 "중개자 캡슐화 공격(Intermediary Encapulation Attacks)"이라고 한다.
- 현재까지도 발생하는 보안 이슈이다. (2019년 11월에 NVD-CVE에서 발표 https://nvd.nist.gov/vuln/detail/CVE-2019-19330)
2. ɑ+🔥) 캡슐화 공격이란 무엇인가?
- 정답 : 캡슐화된 데이터를 다른 곳에서 디코딩할 때 데이터를 잘못 분리하거나 구별하여 잘못된 코드가 소프트웨어에 들어와 문제를 일으키는 경우이다. 이는 전체 시스템에 쌓여 프로그램 누수를 시키거나 도메인 간 공격이 생길 수 있고 엑세스 권한을 얻을 수 있다.
```
예를 들어보자.
1. 해커가 HTTP/1.1을 사용하는 서버와 중간에 멍청한 프락시를 찾는다.
2. HTTP/2.0 메세지를 보내 1.1로 해석하게 만든다.
3. 이때 2.0으로 보내는 메세지에 CR,LF, Null 문자등을 넣어 어떻게 HTTP/1.1 코드가 해석되는지 확인하고 컴파일 보안 문제를 찾는다.
4. 문제점을 발견하고 아래와 같은 코드를 HTTP/2.0 메세지를 보내 서버가 이를 실행하게 만들고 그 응답을 받고 공격한다.

char* path = getenv("PATH");
...
sprintf(stderr, "cannot find exe on path %s\n", path);

getenv() 함수는 표준오류 스트림을 이용해서 환경변수를 확인하는 코드이다. 
이를 HTTP/2.0 메세지로 캡슐화하여 보내고 순진한 프락시는 이를 쉽게 해석하여
HTTP/1.1 메세지로 변환하는데 서버는 이를 모르고 그대로 아래의 코드를 컴파일하여
공격자에게 그대로 노출시킬 수 있다.

reference : https://www.veracode.com/security/encapsulation
```
3. HTTP/2.0은 HTTP/1.1과 달리 스트림과 멀티플렉싱을 통해 효율적으로 통신할 수 있다. 이때 발생할 수 있는 보안 이슈는 무엇인가?
- 정답 : 긴 커넥션을 유지하고 있으면 개인정보 유출에 악용될 수 있다. 

### HTTP/2.0 그림으로 살펴보기
- [Google - HTTP/2 소개](https://developers.google.com/web/fundamentals/performance/http2?hl=ko)
- [http/1.1 vs http/2.0 속도비교, 개발자 도구를 통해 실제 메세지도 확인 가능](https://www.httpvshttps.com/)

- HTTP/1.1 vs HTTP/2
<img src="https://evan-moon.github.io/static/3752593b39ad6ad4dee6a23573eff5d3/29d31/multiplexing.jpg" width="300" height="300">

- Binary Framing Layer
<img src="https://developers.google.com/web/fundamentals/performance/http2/images/binary_framing_layer01.svg?hl=ko" width="500" height="500">

- 요청 및 응답 다중화
<img src="https://developers.google.com/web/fundamentals/performance/http2/images/multiplexing01.svg?hl=ko" width="500" height="500">

- 헤더 압축
<img src="https://developers.google.com/web/fundamentals/performance/http2/images/header_compression01.svg?hl=ko" width="500" height="500">


</div>
</details>
<br>
