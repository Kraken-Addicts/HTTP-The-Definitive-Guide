## 20장 :octopus: 리다이렉션과 부하 균형
### __20.1__ 　  왜 리다이렉트인가?　 `jehong`

1. 리다이렉션이란 최적의 분산된 콘텐츠를 찾는 것을 도와주는 기법의 집합이라고 생각할 수 있다. ( O / X )

2. 리다이렉션은 현대의 웹에서는 피할 수 없는 현실이다. 왜냐하면 웹 콘텐츠는 흔히 여러 장소에 배포되기 때문이다. ( O / X )

3. 웹 콘텐츠가 여러 장소에 배포되는 이유는 HTTP 애플리케이션이 다음 중 세 가지를 원하기 때문입니다. 알맞은 것을 보기에서 골라 빈칸을 채우세요.

   > **<보기>**
   >
   > `응답시간`,  `네트워크 대역폭 절약`, `신뢰성`, `지연 최소화`, `신뢰할 수 있는 HTTP 트랜잭션의 수행`, `네트워크 혼잡도`

   | 😝 HTTP어플이는 이런걸 원해염 | 😜 웹 콘텐츠를 분산이 이렇게 해결해줘염                       |
   | ---------------------------- | ------------------------------------------------------------ |
   | `____________a____________`  | 클라이언트가 보다 가까운 리소스에 접근할 수 있게 해주어 `_____b_____` 을/를 줄여준다 |
   | `____________c____________`  | 목적지 서버가 분산되어 `_____d_____` 이/가 줄어든다          |
   | `____________e____________`  | 한 곳에서 실패한 경우 다른 곳을 이용할 수 있도록 하여 `_____f_____` 을/를 개선한다 |

4. 대부분의 리다이렉션 장치들은 몇 가지 방식의 `____a____`을 포함해 들어오는 메시지의 `__b__`를 서버들의 집합에게 분산할 수 있다.

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">

1. 리다이렉션이란 최적의 분산된 콘텐츠를 찾는 것을 도와주는 기법의 집합이라고 생각할 수 있다. ( **O** )  **p.522**

2. 리다이렉션은 현대의 웹에서는 피할 수 없는 현실이다. 왜냐하면 웹 콘텐츠는 흔히 여러 장소에 배포되기 때문이다. ( **O** )  **p.522**

3. 웹 콘텐츠가 여러 장소에 배포되는 이유는 HTTP 애플리케이션이 다음 중 세 가지를 원하기 때문입니다. 알맞은 것을 보기에서 골라 빈칸을 채우세요. **p.522**

   > **<보기>**
   >
   > `응답시간`,  `네트워크 대역폭 절약`, `신뢰성`, `지연 최소화`, `신뢰할 수 있는 HTTP 트랜잭션의 수행`, `네트워크 혼잡도`

   | 😝 HTTP어플이는 이런걸 원해염             | 😜 웹 콘텐츠를 분산이 이렇게 해결해줘염                       |
   | ---------------------------------------- | ------------------------------------------------------------ |
   | `a. 지연 최소화`                         | 클라이언트가 보다 가까운 리소스에 접근할 수 있게 해주어 `b. 응답시간` 을/를 줄여준다 |
   | `c. 네트워크 대역폭 절약`                | 목적지 서버가 분산되어 `d. 네트워크 혼잡도` 이/가 줄어든다   |
   | `e. 신뢰할 수 있는 HTTP 트랜잭션의 수행` | 한 곳에서 실패한 경우 다른 곳을 이용할 수 있도록 하여 `f. 신뢰성` 을/를 개선한다 |

4. 대부분의 리다이렉션 장치들은 몇 가지 방식의 `a.부하균형`을 포함해 들어오는 메시지의 `b.부하` 를 서버들의 집합에게 분산할 수 있다. **p.522**

</div>
</details>
<br>

### __20.2__ 　  리다이렉트 할 곳　 `jehong`

1. 서버, 프락시, 캐시, 게이트웨이는 모두 서버의 특성을 갖고 있기 때문에 모든 리다이렉션 기법이 이들 모두에서 동작한다. ( O / X )

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">

1. 서버, 프락시, 캐시, 게이트웨이는 모두 서버의 특성을 갖고 있기 때문에 모든 리다이렉션 기법이 이들 모두에서 동작한다. ( **X** ) **p.522**

   > **답: X**
   >
   > 어떤 리다이렉션 기술들은 특정 종류의 종단만을 위해 특별히 설계되어 일반적인 적용이 불가능하다.

</div>
</details>
<br>

### __20.3__ 　  리다이렉션 프로토콜의 개요　 `jehong`

1. 리다이렉션의 목표는 HTTP 메시지를 가용한 웹 서버로 가급적 빨리 보내는 것이다. ( O / X )

2. HTTP 메시지가 인터넷을 통해 나아가는 방향은 그 메시지를 다루는 `_______a______` 과 `______b______` 에 영향을 받는다.

3. 리다이렉션 방법 이름을 설명에 맞게 보기에서 골라 채우세요.

   > **<보기>**
   >
   > `HTTP 리다이렉션`, `DNS 리다이렉션`, `임의 캐스트 어드레싱`, `아이피 맥(MAC) 포워딩`, `IP 주소 포워딩`

   | 메커니즘              | 동작 방식                                                    |
   | --------------------- | ------------------------------------------------------------ |
   | `_________a_________` | 서버가 URL의 호스트 명에 대한 응답으로 어떤 IP 주소를 사용할지 결정한다. |
   | `_________b_________` | 스위치나 라우터 같은 네트워크 요소가 패킷의 목적지 주소를 읽는다.<br />만약 패킷이 리다이렉트되어야한다면, 스위치는 그 패킷에게 서버나 프락시의 목적지 MAC 주소를 준다. |
   | `_________c_________` | 여러 서버가 같은 IP 주소를 사용한다.<br />각 서버는 백본 라우터인 척 하고 그 외의 라우터들은 그 공유된 IP 주소로 향하는 패킷을 가장 가까운 서버로 보낸다.(그들이 패킷을 가장 가까운 라우터로 보내고 있다고 믿으면서) |
   | `_________d_________` | 레이어 4 스위치는 패킷의 목적지 포트를 평가하고, 리다이렉트 패킷의 아이피 주소를 프락시나 미러링된 서버의 아이피 주소로 바꾼다. |
   | `_________e_________` | HTTP 요청은 콘텐츠를 제공하기에 최적인 웹 서버를 선택해줄 첫 번째 웹 서버로 간다.<br />그 웹 서버는 클라이언트에게 선택한 서버로의 HTTP 리다이렉트를 보내준다.<br />클라이언트는 선택된 서버에게 다시 요청을 보낸다. |



<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">

1. 리다이렉션의 목표는 HTTP 메시지를 가용한 웹 서버로 가급적 빨리 보내는 것이다. ( **O** ) **p.523**

2. HTTP 메시지가 인터넷을 통해 나아가는 방향은 그 메시지를 다루는 `a. HTTP 애플리케이션` 과 `b. 라우팅 장치` 에 영향을 받는다. **p.523**

3. 리다이렉션 방법 이름을 설명에 맞게 보기에서 골라 채우세요. **p.524**

   > **<보기>**
   >
   > `HTTP 리다이렉션`, `DNS 리다이렉션`, `임의 캐스트 어드레싱`, `아이피 맥(MAC) 포워딩`, `IP 주소 포워딩`

   | 메커니즘                   | 동작 방식                                                    |
   | -------------------------- | ------------------------------------------------------------ |
   | `a. DNS 리다이렉션`        | 서버가 URL의 호스트 명에 대한 응답으로 어떤 IP 주소를 사용할지 결정한다. |
   | `b. 아이피 맥(MAC) 포워딩` | 스위치나 라우터 같은 네트워크 요소가 패킷의 목적지 주소를 읽는다.<br />만약 패킷이 리다이렉트되어야한다면, 스위치는 그 패킷에게 서버나 프락시의 목적지 MAC 주소를 준다. |
   | `c. 임의 캐스트 어드레싱`  | 여러 서버가 같은 IP 주소를 사용한다.<br />각 서버는 백본 라우터인 척 하고 그 외의 라우터들은 그 공유된 IP 주소로 향하는 패킷을 가장 가까운 서버로 보낸다.(그들이 패킷을 가장 가까운 라우터로 보내고 있다고 믿으면서) |
   | `d. IP 주소 포워딩`        | 레이어 4 스위치는 패킷의 목적지 포트를 평가하고, 리다이렉트 패킷의 아이피 주소를 프락시나 미러링된 서버의 아이피 주소로 바꾼다. |
   | `e. HTTP 리다이렉션`       | HTTP 요청은 콘텐츠를 제공하기에 최적인 웹 서버를 선택해줄 첫 번째 웹 서버로 간다.<br />그 웹 서버는 클라이언트에게 선택한 서버로의 HTTP 리다이렉트를 보내준다.<br />클라이언트는 선택된 서버에게 다시 요청을 보낸다. |

   



</div>
</details>
<br>



### __20.4.1.~20.4.2.__ 　  일반적인 리다이렉션 방법 (1)　 `taelee`

#### 1. 다음 중 HTTP 리다이렉션의 단점으로 알맞지 않은 것은?

  1. 어떤 서버로 리다이렉트할 지 결정하는데에 사용하는 처리량이 너무 크다
  2. 페이지에 접근할 때마다 2 번의 왕복이 발생해서 시간이 증가된다
  3. 서버가 클라이언트의 주소를 모르기 때문에 클라이언트와 가까운 서버로의 리다이렉션이 불가능하다
  4. 리다이렉트 서버가 고장나면 사이트에 접근할 수 없게 된다.

#### 2. DNS 라다이렉션 중 하나인 라운드 로빈 방식은 도메인과 연결된 IP주소를 하나씩 돌아가면서 클라이언트에게 제공하는 방식이다(O/X)

#### 3. 라운드 로빈(Round-Robin)은 스포츠리그에서 자주 쓰이는 토너먼트 방식으로 한 팀이 다른 모든 팀과 경기를 하는 방식을 뜻한다. 예를 들어 EPL(영국 축구리그)는 더블 라운드 로빈 토너먼트 방식으로 한팀이 다른 모든 팀과 2번씩 경기를 치룬다. 다음 중 라운드 로빈의 어원인 것은?

1. 로빈 후드(Robin Hood)는 아들의 머리 위에 사과를 올려놓고 명중 시킨 것으로 유명하다. 이 사건 이후로 통나무 위에 사과를 올려놓고 사람들이 주위에 둘러서서 돌아가면서 사과를 향해 화살을 쏘는 게임이 유행했는데 이를 계기로 라운드 로빈 게임 방식이 생겨났다.
2. 과거의 프랑스 및 여러지역에서 선원들이 문서(보통 정부를 향한)에 싸인을 할 때 주동자가 누군지 들키지 않도록 문서 주위의 원 모양을 그리면서 싸인을 했다고 한다. 이 방식을 영어로 읽으면서 라운드 로빈이 되었다.
3. H는 손으로 코를 훑는 습관이 있었다(스으읍). 이 행동(스으읍)을 너무 사랑한 H는 친구들에게 이 행동(스으읍)을 널리 전파하고 다녔다. 신기하게도 이 행동(스으읍)을 소개받은 친구들도 이 행동(스으읍)에 중독이 되고 말았다. 결국 전교생이 이 행동(스으읍)에 중독이 되었고 매일 아침마다 운동장에 전교생이 원 모양으로 둘러서서 이 행동(스으읍)을 하곤 했다. 이 초등학교의 이름이 로빈 초등학교였기 때문에 후에 라운드 로빈이라는 단어의 어원이 되었다.
4. 현대 스포츠 리그 방식의 창시자로 불리는 축구선수 A가 이 게임 방식을 제안했고 당시 뛰고 있던 구단의 감독(마이클 로빈) 이름을 따와 라운드 로빈방식이 되었다.
5. 어원이 밝혀지지 않았다.

#### 4. 클라이언트 `여름`은 naver.com에 접속하여 DNS룩업을 실행하였다.
![Group 4 (1)](https://user-images.githubusercontent.com/55867479/93372632-1be18e00-f88f-11ea-846b-395ed27d27a2.png)

naver.com이 라운드 로빈 주소 순환을 사용한다고 했을 때 1번에서 2번그림은 주소 순환이 정상적으로 잘 이루어졌다. (210.89.164.90에서 21.89.160.88로 순서대로 넘어갔기 때문에) 
하지만 문제는 그 다음 룩업에서 일어나고 말았다. 이번에는 라운드 로빈 DNS 리다이렉션에 의해 끝자리가 142인 IP로 갈 차례였지만 순서를 하나 건너뛰고 끝자리가 141인 IP로 넘어가버렸다. 그 이유는 무엇일까?

#### 5. 보기에서 골라 알맞게 짝지으세요.

보기) `부하 균형 알고리즘`, `근접 라우팅 알고리즘`, `결함 마스킹 알고리즘`

1. 흐트트프.com에는 3개의 서버(`세초`, `현준`, `대리`)와 연결되어 있다.  이중 서버 `현준`과 `대리`는 여자친구들이랑 놀러 다니기 바뻐서 항상 모든 트래픽을 서버 `세초`가 다 받아낸다. 참다참다 못한 세초는 이제 트래픽 부하를 봐가면서 적은 부하를 갖고 있는 사람이 일을 하자고 현준과 대리를 설득해냈다. 이 알고리즘은?
2. 장수 막걸리 사이트는 서버 `쿠킴`과 `예하`가 연결되어 있다. `쿠킴`은 전라북도 장수군에 `예하`는 서울에 설치되어 있다. 어느날 서버 `쿠킴`은 땡볕에 일을 너무 열심히 하다가 서버가 망가져서 서버 `예하`가 모든 일을 다하게 됐다. 이 알고리즘은?




<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">

#### 1. 다음 중 HTTP 리다이렉션의 단점으로 알맞지 않은 것은?


  1. 어떤 서버로 리다이렉트할 지 결정하는데에 사용하는 처리량이 너무 크다
  2. 페이지에 접근할 때마다 2 번의 왕복이 발생해서 시간이 증가된다
  3. 서버가 클라이언트의 주소를 모르기 때문에 클라이언트와 가까운 서버로의 리다이렉션이 불가능하다
  4. 리다이렉트 서버가 고장나면 사이트에 접근할 수 없게 된다.

> 정답: 3번, HTTP 리다이렉션은 서버가 클라이언트의 주소를 알 수 있는 방식이다

#### 2. DNS 리다이렉션 중 하나인 라운드 로빈 방식은 도메인과 연결된 IP주소를 하나씩 돌아가면서 클라이언트에게 제공하는 방식이다(O/X)



> 정답: O, 라운드 로빈 방식은 가장 간단한 DNS 리다이렉션 방식으로 연결된 IP주소를 돌아가면서 클라이언트에게 제공한다.

#### 3. 라운드 로빈(Round-Robin)은 스포츠리그에서 자주 쓰이는 토너먼트 방식으로 한 팀이 다른 모든 팀과 경기를 하는 방식을 뜻한다. 예를 들어 EPL(영국 축구리그)는 더블 라운드 로빈 토너먼트 방식으로 한팀이 다른 모든 팀과 2번씩 경기를 치룬다. 다음 중 라운드 로빈의 어원인 것은?

1. 로빈 후드(Robin Hood)는 아들의 머리 위에 사과를 올려놓고 명중 시킨 것으로 유명하다. 이 사건 이후로 통나무 위에 사과를 올려놓고 사람들이 주위에 둘러서서 돌아가면서 사과를 향해 화살을 쏘는 게임이 유행했는데 이를 계기로 라운드 로빈 게임 방식이 생겨났다.

2. 과거의 프랑스 및 여러지역에서 선원들이 문서(보통 정부를 향한)에 싸인을 할 때 주동자가 누군지 들키지 않도록 문서 주위의 원 모양을 그리면서 싸인을 했다고 한다. 이 방식을 영어로 읽으면서 라운드 로빈이 되었다.

3. H는 손으로 코를 훑는 습관이 있었다(스으읍). 이 행동(스으읍)을 너무 사랑한 H는 친구들에게 이 행동(스으읍)을 널리 전파하고 다녔다. 신기하게도 이 행동(스으읍)을 소개받은 친구들도 이 행동(스으읍)에 중독이 되고 말았다. 결국 전교생이 이 행동(스으읍)에 중독이 되었고 매일 아침마다 운동장에 전교생이 원 모양으로 둘러서서 이 행동(스으읍)을 하곤 했다. 이 초등학교의 이름이 로빈 초등학교였기 때문에 후에 라운드 로빈이라는 단어의 어원이 되었다.

4. 현대 스포츠 리그 방식의 창시자로 불리는 축구선수 A가 이 게임 방식을 제안했고 당시 뛰고 있던 구단의 감독(마이클 로빈) 이름을 따와 라운드 로빈방식이 되었다.

5. 어원이 밝혀지지 않았다.

> 정답: 2번, 
> 1번의 사과를 맞춤 사람은 윌리엄텔이다.
> 4번 100% 지어낸 이야기다.
> 2번 https://www.wikiwand.com/en/Round-robin_(document)
> 위 링크에 들어가면 Round Robin방식으로 싸인된 문건을 볼 수 있다.
> 불어로 'rond rouban'라고 하는데 circle of ribbon이라는 뜻이다. 

#### 4. 클라이언트 `여름`은 naver.com에 접속하여 DNS룩업을 실행하였다.
![Group 4 (1)](https://user-images.githubusercontent.com/55867479/93372632-1be18e00-f88f-11ea-846b-395ed27d27a2.png)

naver.com이 라운드 로빈 주소 순환을 사용한다고 했을 때 1번에서 2번그림은 주소 순환이 정상적으로 잘 이루어졌다. (210.89.164.90에서 21.89.160.88로 순서대로 넘어갔기 때문에)
하지만 문제는 그 다음 룩업에서 일어나고 말았다. 이번에는 라운드 로빈 DNS 리다이렉션에 의해 끝자리가 142인 IP로 갈 차례였지만 순서를 하나 건너뛰고 끝자리가 141인 IP로 넘어가버렸다. 그 이유는 무엇일까?

> naver.com서버에 `여름` 클라이언트 이외에도 다른 클라이언트가 접속해서 순환을 돌기 때문에

#### 5. 보기에서 골라 알맞게 짝지으세요.

보기) `부하 균형 알고리즘`, `근접 라우팅 알고리즘`, `결함 마스킹 알고리즘`

1. 흐트트프.com에는 3개의 서버(`세초`, `현준`, `대리`)와 연결되어 있다.  이중 서버 `현준`과 `대리`는 여자친구들이랑 놀러 다니기 바뻐서 항상 모든 트래픽을 서버 `세초`가 다 받아낸다. 참다참다 못한 세초는 이제 트래픽 부하를 봐가면서 적은 부하를 갖고 있는 사람이 일을 하자고 현준과 대리를 설득해냈다. 이 알고리즘은?
> 정답: `부하 균형 알고리즘`
2. 장수 막걸리 사이트는 서버 `쿠킴`과 `예하`가 연결되어 있다. `쿠킴`은 전라북도 장수군에 `예하`는 서울에 설치되어 있다. 어느날 서버 `쿠킴`은 땡볕에 일을 너무 열심히 하다가 서버가 망가져서 서버 `예하`가 모든 일을 다하게 됐다. 이 알고리즘은?
> 정답: `결함 마스킹 알고리즘`




</div>
</details>
<br>



### __20.4.3.~20.4.6.__ 　  일반적인 리다이렉션 방법 (2)　 `yeosong`

#### __20.4.3.~20.4.5__ 　  

다음 설명에 적합한 리다이렉션 방법을 고르세요.

`DNS 리다이렉션`
`캐시 배열 라우팅 프로토콜`
`애니캐스트(임의 어드레싱 캐스트)`
`IP MAC 포워딩`
`IP 주소 포워딩`

1. 이 방법은 라우터가 잠재적인 수신자 그룹 안에서 가장 가까운 노드로 연결 시켜주는 기법이 사용된다.
2. 점 대 점으로만 가능하기 때문에, 서버와 프락시가 스위치와 한 홉 거리에 위치해야만 한다.
3. full NAT(완전 네트워크 주소 변환)으로 처리될 경우, 클라이언트 IP 주소를 웹 서버가 알 수 없게 된다.

#### __20.4.6__ 　  네트워크 구성요소 제어 프로토콜 NECP

1. NECP는 어디에 쓰이는 프로토콜 일까요?


2. 아래는 NECP가 사용하는 메시지 입니다. 설명에 맞는 메시지를 고르세요. 

![20-3-1](https://user-images.githubusercontent.com/53321189/93372998-af1ac380-f88f-11ea-93e6-db4bd1c80b26.png)

a. NE에게 하나 이상의 예외를 그의 목록에서 삭제하라고 요청한다. <br>
b. NECP_INIT을 받았음을 알린다.  <br>
c. 피어가 살아있는지 물어본다. <br>
d. NE 전체의 예외 목록을 문의한다. <br>
e. SE는 NE에게 "트래픽을 나에게 보내는 것을 중단하라"라고 말한다.  <br>

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
#### __20.4.3.~20.4.5__ 　  

다음 설명에 적합한 리다이렉션 방법을 고르세요.

`DNS 리다이렉션`
`캐시 배열 라우팅 프로토콜`
`애니캐스트(임의 어드레싱 캐스트)`
`IP MAC 포워딩`
`IP 주소 포워딩`

1. 이 방법은 라우터가 잠재적인 수신자 그룹 안에서 가장 가까운 노드로 연결 시켜주는 기법이 사용된다. `애니캐스트(임의 어드레싱 캐스트)`
2. 점 대 점으로만 가능하기 때문에, 서버와 프락시가 스위치와 한 홉 거리에 위치해야만 한다. `IP MAC 포워딩`
3. full NAT(완전 네트워크 주소 변환)으로 처리될 경우, 클라이언트 IP 주소를 웹 서버가 알 수 없게 된다. `IP 주소 포워딩`

#### __20.4.6__ 　  네트워크 구성요소 제어 프로토콜 NECP

1. `NECP`는 `NE`(네트워크 구성요소 - ex 라우터, 스위치)가 `SE`(서버 구성요소 - ex 웹 서버, 프락시 캐시)와 대화할 때 쓰는 프로토콜이다.



2. 아래는 NECP가 사용하는 메시지 입니다. 설명에 맞는 메시지를 고르세요. 

![20-3](https://user-images.githubusercontent.com/53321189/93371884-0455d580-f88e-11ea-9121-4b6872673ce1.png)

a. NE에게 하나 이상의 예외를 그의 목록에서 삭제하라고 요청한다.  `NECP_EXCEPTION_DEL`    <br>
b. NECP_INIT을 받았음을 알린다. `NECP_INIT_ACK`  <br>
c. 피어가 살아있는지 물어본다. `NECP_KEEPALIVE`  <br>
d. NE 전체의 예외 목록을 문의한다. `NECP_EXCEPTION_QUERY`  <br>
e. SE는 NE에게 "트래픽을 나에게 보내는 것을 중단하라"라고 말한다. `NECP_STOP`  <br>


</div>
</details>
<br>

