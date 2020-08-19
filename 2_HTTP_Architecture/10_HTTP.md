## 10장 :octopus: HTTP/2.0

### 10.1 　  HTTP/2.0의 등장 배경　 `hylee`
- 여기에
- 문제를 작성해주세요
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
- 여기에
- 해설을 작성해주세요

</div>
</details>
<br>

### 10.2 　  개요　 `hylee`
- 여기에
- 문제를 작성해주세요
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
- 여기에
- 해설을 작성해주세요

</div>
</details>
<br>

### 10.3 　  HTTP/1.1과의 차이점　 `hylee`
- 여기에
- 문제를 작성해주세요
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
- 여기에
- 해설을 작성해주세요

</div>
</details>
<br>

### 10.4 　  알려진 보안 이슈　 `kukim`
1. HTTP/2.0 메세지를 중간의 프락시가 HTTP/1.1 메세지로 변환할 때 메세지가 변질 될 수 있다  (O/X)
2. +++) 캡슐화 공격이란 무엇인가?
3. HTTP/2.0은 HTTP/1.1과 달리 스트림과 멀티플렉싱을 통해 효율적으로 통신할 수 있다. 이때 발생할 수 있는 보안 이슈는 무엇인가?

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. HTTP/2.0 메세지를 중간의 프락시가 HTTP/1.1 메세지로 변환할 때 메세지가 변질 될 수 있다  (O/X)
- 정답 : O (CR,LF,Null 문자 등을 잘못 처리하여 헤더와 메세지를 구분하지 못하게 될 수 있다. 현재까지도 발생하는 보안 이슈이다. 2019년 11월에 NVD-CVE에서 발표된 메세지 변환시 발생하는 문제https://nvd.nist.gov/vuln/detail/CVE-2019-19330)
2. +++) 캡슐화 공격이란 무엇인가?
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

- Binary Framing Layer
<img src="https://developers.google.com/web/fundamentals/performance/http2/images/binary_framing_layer01.svg?hl=ko" width="500" height="500">

- 요청 및 응답 다중화
<img src="https://developers.google.com/web/fundamentals/performance/http2/images/multiplexing01.svg?hl=ko" width="500" height="500">

- 헤더 압축
<img src="https://developers.google.com/web/fundamentals/performance/http2/images/header_compression01.svg?hl=ko" width="500" height="500">

- HTTP/1.1 vs HTTP/2
<img src="https://evan-moon.github.io/static/3752593b39ad6ad4dee6a23573eff5d3/29d31/multiplexing.jpg" width="300" height="300">
</div>
</details>
<br>
