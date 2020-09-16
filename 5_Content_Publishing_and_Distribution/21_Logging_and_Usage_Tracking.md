## 21장 :octopus: 로깅과 사용추적
### __21.1__ 　  로그란 무엇인가?　 `hylee`
1. 대체로 우리가 로깅을 하는 이유 2가지는 뭘까요? (서술형)
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
> 정답: 1. 서버나 프락시의 문제를 찾기 위해서 2.접근 통계를 내려고

</div>
</details>
<br>

### __21.2__ 　  로그 포맷 (일반로그포맷 21.2.1만!)　 `hylee`
1. 요즘 사용하는 가장 일반적인 포맷의 이름은 무엇일까요??
- 보기 : `(a) 일반 로그 포맷(Common Log Format)`, `(b) 기본 로그 포맷(Basic Log Format)`, <br>`(c) 커몬 로그 포맷(Comeon Log Fromat)`, `(d) 표준 로그 포맷(Standard Log Format)`


2.다음 로그 포맷을 분석해서 아래에 해당하는 필드에 맞는 엔트리 (1)~(5)에 들어갈 순서는 무엇일까요?
> `https://www.yebalja.com/ - hylee [17/Sep/ :10:55:32 +0900] "GET /foo HTTP/1. 0" 200 0`
- 보기 : `(a)-` `(b)hylee`  `(c)"GET /foo HTTP/1.0"` `(d)200` `(e)0`

![image](https://user-images.githubusercontent.com/44167177/93292152-d2a62580-f81f-11ea-8657-203c929f3833.png)




<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 요즘 사용하는 가장 일반적인 포맷의 이름은 무엇일까요??
  - 보기 : `일반 로그 포맷(Common Log Format)`
  
2.다음 로그 포맷을 분석해서 아래에 해당하는 필드에 맞는 엔트리 (1)~(5)에 들어갈 순서는 무엇일까요?
> `https://www.yebalja.com/ - hylee [17/Sep/ :10:55:32 +0900] "GET /foo HTTP/1. 0" 200 0`
- 보기 : `(a)-` `(b)hylee`  `(c)"GET /foo HTTP/1.0"` `(d)200` `(e)0`
> 정답 : (b) - (a) - (d) - (c) - (e)

![image](https://user-images.githubusercontent.com/44167177/93292634-f322af80-f820-11ea-9349-dd525f1e7481.png)


</div>
</details>
<br>

### __21.3__ 　  적중 계량하기　 `kukim`
1. 다음은 어떤 규약에 관한 설명인가요? `단답형`

```bash
원 서버는 클라이언트(사용자)들의 통계자료(특정 URL 접속 횟수 등)를 알기위해 많은 로깅, 로그파일을 남긴다.
하지만 클라이언트와 원 서버 사이에 수 많은 프락시, 캐시 서버로 인해 많은 요청이 원 서버로 오지 않고 처리된다.
이를 방지하기 위해 원 서버는 자신에게 요청이 오게 하기 위해 중요한 페이지의 캐시를 일부로 파기하여 원 서버로 요청을 돌리게 만든다.
하지만 이런 문제는 네트워크에 부담을 주어 응답속도를 느리게 만든다.
이를 해결하기 위해서 어떤 규약을 만들었다.
```

2. 위의 규약을 활용하여 캐시나 서버는 `( )` 헤더를 사용하여 캐시서버가 원 서버 사이에 통신을 하여 클라이언트의 정보를 알 수 있다.



<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 다음은 어떤 규약에 관한 설명인가요? `단답형`

```bash
원 서버는 클라이언트(사용자)들의 통계자료(특정 URL 접속 횟수 등)를 알기위해 많은 로깅, 로그파일을 남긴다.
하지만 클라이언트와 원 서버 사이에 수 많은 프락시, 캐시 서버로 인해 많은 요청이 원 서버로 오지 않고 처리된다.
이를 방지하기 위해 원 서버는 자신에게 요청이 오게 하기 위해 중요한 페이지의 캐시를 일부로 파기하여 원 서버로 요청을 돌리게 만든다.
하지만 이런 문제는 네트워크에 부담을 주어 응답속도를 느리게 만든다.
이를 해결하기 위해서 어떤 규약을 만들었다.
```

- 정답 : Hit Metering(적중 계량 규약)

2. 위의 규약을 활용하여 캐시나 서버는 `( )` 헤더를 사용하여 캐시서버가 원 서버 사이에 통신을 하여 클라이언트의 정보를 알 수 있다.

- 정답 : Meter 헤더

</div>
</details>
<br>

### __21.4__ 　  개인 정보 보호에 대해 `kukim`
1. 클라이언트(사용자)들은 서버에 접속할 때 자신의 정보가 저장되고 있다는 사실을 완벽하게 인지하지 못하기 때문에 서버는 반드시 공지해야 한다.(ex) 쿠키 수집 동의) (O / X / △)

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 클라이언트(사용자)들은 서버에 접속할 때 자신의 정보가 저장되고 있다는 사실을 완벽하게 인지하지 못하기 때문에 서버는 반드시 공지해야 한다.(ex) 쿠키 수집 동의) (O / X / △)
    - 정답 : △
    - 나라마다 법률에 관한 범위는 다르다.
    - But 하는 것이 좋다..?
    - 나라별 쿠키에 관한 법률 차이 : https://www.kisa.or.kr/jsp/common/downloadAction.jsp?bno=158&dno=203&fseq=1
    - EU GDPR의 쿠키 수집에 대한 동의 약관
    - [https://gdpr.eu/cookies/](https://gdpr.eu/cookies/)
    - [https://ec.europa.eu/ipg/basics/legal/cookies/index_en.htm](https://ec.europa.eu/ipg/basics/legal/cookies/index_en.htm)

</div>
</details>
<br>
