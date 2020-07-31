## 05장 :octopus: 웹 서버

[5.1　다채로운 웹 서버](#51--다채로운-웹-서버-junslee) <br>
[5.2　간단한 펄 웹 서버](#52--간단한-펄-웹-서버-junslee) <br>
[5.3　진짜 웹 서버가 하는 일](#53--진짜-웹-서버가-하는-일-mihykim) <br>
[5.4　단계 1: 클라이언트 커넥션 수락](#54--단계-1-클라이언트-커넥션-수락-mihykim)<br>
[5.5　단계 2: 요청 메시지 수신](#55--단계-2-요청-메시지-수신-mihykim) <br>
[5.6　단계 3: 요청 처리](#56--단계-3-요청-처리-daelee) <br>
[5.7　단계 4: 리소스의 매핑과 접근](#57--단계-4-리소스의-매핑과-접근-daelee) <br>
[5.8　단계 5: 응답 만들기](#58--단계-5-응답-만들기-secho) <br>
[5.9　단계 6: 응답 보내기](#59--단계-6-응답-보내기-secho) <br>
[5.10　단계 7: 로깅](#510--단계-7-로깅-secho) <br>
<br>

### 5.1　  다채로운 웹 서버　 `junslee`
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

### 5.2　  간단한 펄 웹 서버　 `junslee`
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

### 5.3　  진짜 웹 서버가 하는 일　 `mihykim`
![quiz](https://user-images.githubusercontent.com/60066472/89006440-bcacd600-d341-11ea-973e-f4424c2b2b01.png)
- 위 그림을 참고하여 빈칸에 알맞은 순서를 기입해주세요
  - 리소스에 접근한다 _(메세지에서 지정한 리소스에 접근한다)_ : __`(　)`__
  - 커넥션을 맺는다 _(클라이언트의 접속을 받아들이거나, 원치 않는 클라이언트라면 닫는다)_ : __`(　)`__
  - 트랜잭션을 로그로 남긴다 _(로그파일에 트랜잭션 완료에 대한 기록을 남긴다)_ : __`(　)`__
  - 요청을 받는다 _(HTTP 요청 메세지를 네트워크로붜 읽어들인다)_ : __`(　)`__
  - 응답을 만든다 _(올바른 헤더를 포함한 HTTP 응답 메세지를 생성한다)_ : __`(　)`__
  - 요청을 처리한다 _(요청 메세지를 해석하고 행동을 취한다)_ : __`(　)`__
  - 응답을 보낸다 _(응답을 클라이언트에게 돌려준다)_ : __`(　)`__
  
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
- 리소스에 접근한다 _(메세지에서 지정한 리소스에 접근한다)_ : __`(4)`__
- 커넥션을 맺는다 _(클라이언트의 접속을 받아들이거나, 원치 않는 클라이언트라면 닫는다)_ : __`(1)`__
- 트랜잭션을 로그로 남긴다 _(로그파일에 트랜잭션 완료에 대한 기록을 남긴다)_ : __`(7)`__
- 요청을 받는다 _(HTTP 요청 메세지를 네트워크로붜 읽어들인다)_ : __`(2)`__
- 응답을 만든다 _(올바른 헤더를 포함한 HTTP 응답 메세지를 생성한다)_ : __`(5)`__
- 요청을 처리한다 _(요청 메세지를 해석하고 행동을 취한다)_ : __`(3)`__
- 응답을 보낸다 _(응답을 클라이언트에게 돌려준다)_ : __`(6)`__

</div>
</details>
<br>

### 5.4　  단계 1: 클라이언트 커넥션 수락　 `mihykim`
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

### 5.5　  단계 2: 요청 메시지 수신　 `mihykim`
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

### 5.6　  단계 3: 요청 처리　 `daelee`
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

### 5.7　  단계 4: 리소스의 매핑과 접근　 `daelee`
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

### 5.8　  단계 5: 응답 만들기　 `secho`
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

### 5.9　  단계 6: 응답 보내기　 `secho`
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

### 5.10　  단계 7: 로깅　 `secho`
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

[맨위로](#05장-octopus-웹-서버)
