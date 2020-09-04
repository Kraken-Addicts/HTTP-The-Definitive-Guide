## 15장 :octopus: 엔터티와 인코딩
### __15.1__ 　  메시지는 컨테이너, 엔터티는 화물　 `yeosong`
- 여기에
- 문제를 작성해주세요
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
#### __15.1.1__ 　  메시지는 컨테이너, 엔터티는 화물

인턴 `yeosong`은 www.joes-hardware.com 에서 오고 갔던 HTTP 메시지를 살펴보고 있다.

각 문항에서 제시하는 정보를 확인하고 싶을 때, <보기>의 엔터티 관련 주요 헤더 중 어느 헤더를 찾아서 읽어야할까?

||<보기>||
|---|---|---|
|`a. Content-Type`       | `e. Content-Location`    |      `i. Expires`         |
|`b. Content-Length`     | `f. Content-Range`       |      `j. Allow`           |
|`c. Content-Language`   | `g. Content-MD5`         |      `k. ETag`            |
|`d. Content-Encoding`   | `h. Last-Modified`       |      `l. Cache-Control`   |

1) 엔터티 본문의 콘텐츠에 대한 체크섬                                `g. Content-MD5`
2) 전달되는 객체와 가장 잘 대응되는 자연어                            `c. Content-Language` 
3) 서버에서 이 콘텐츠가 생성 혹은 수정된 날                           `h. Last-Modified`    
4) If-Match나 If-None-Match 요청을 받았을 때 인스턴스에 대한 검사기    `k. ETag`                           
5) 이 리소스에 대해 허용되는 요청 메서드 (ex GET, HEAD..)             `j. Allow`  
6) 이 데이터가 더 이상 신선하지 않은 것으로 간주되는 시점                 `i. Expires`   
7)
8) 이 문서를 캐시할 때 지킬 요청사항                                 `l. Cache-Control`
9)
10)
11)
12)




</div>
</details>
<br>

### __15.2__ 　  Content-Length: 엔터티의 길이　 `hylee`
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

### __15.3__ 　  엔터티 요약　 `kukim`
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

### __15.4__ 　  미디어 타입과 차셋(Charset)　 `kukim`
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

### __15.5__ 　  콘텐츠 인코딩　 `junslee`

1. 다음은 콘텐츠 인코딩 과정을 순서에 따라 나열한 것입니다. 빈칸을 채워주세요.<br>

- 웹서버가 원본 'Content-Type'헤더와 `________________`헤더를 수반한 원본 응답 메시지를 생성한다.
- 콘텐츠 인코딩 서버(원 서버 또는 다운스트림 프락시 서버)가 `_______`된 메시지를 생성한다
- 콘텐츠 인코딩 서버는 `_________________`헤더를 인코딩된 메시지에 추가하여 수신하는 애플리케이션이 그것을 디코딩하도록 해준다.
- 수신 측 프로그램은 인코딩된 메시지를 받아 `_______`하고 원본을 얻는다.

2. 인코딩된 메시지는 Content_Type과 Content_Length가 이전과 같다. (O / X)
 
<img src="https://postfiles.pstatic.net/MjAyMDA0MjVfNzEg/MDAxNTg3NzgxNzM0ODA5.bASW0WINsL0k8_xqPCI8Lj7l-3mEoHN0vaRmfIiIZggg.JB_M4JBGhJWGyH_Da3BX9OgnIxo0SOdhls7bcMpKAsAg.JPEG.dlaxodud2388/1587781732919.jpg?type=w580" width="400" height="200"><br>
3-1. 위의 Content-Type헤더는 생략이 가능하다. (O / X)<br>
3-2. 위의 Content_Length값인 7023은 `인코딩된 본문/ 디코딩된 본문`의 길이이다.<br> 
3-3. 위의 Content_Encoding의 'gzip'은 엔터티에 GNU zip 인코딩이 적용되었음을 의미한다. (O / X) 

4. 서버에서 클라이언트가 지원하지 않는 인코딩을 사용하는 것을 막기 위해, 클라이언트는 자신이 지원하는 인코딩 목록을 어떤 헤더를 통해 전달할까요?
 

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  1. Content_Length, 인코딩, Content_Encoding, 디코딩<br><br>
  
  2. 인코딩된 메시지는 Content_Type과 Content_Length가 이전과 같다. (X)<br>
  => 인코딩된 메시지는 인코딩된 메시지와 Content-Type는 같지만 (압축같은 것이 되었다면)Content-Length는 다르다.<br>
  
  3-1. 위의 Content-Type헤더는 생략이 가능하다. (X)<br>
  => Content-Type헤더는 디코딩된 엔터티를 보여주기 위해 필요한 정보이므로 메시지에 존재할 수 있고 또 그래야 한다.
  
  3-2. 위의 Content_Length값인 7023은 `디코딩된 본문`의 길이이다.<br>
  
  3-3. 위의 Content_Encoding의 'gzip'은 엔터티에 GNU zip 인코딩이 적용되었음을 의미한다. 일반적으로 가장 효율적이고 널리 쓰이는 압축 알고리즘이다. (O)<br>
  
  4. Accept-Encoding
  
</div>
</details>
<br>

### __15.6__ 　  전송 인코딩과 청크 인코딩　 `junslee`

1. 콘텐츠 인코딩은 단지 메시지의 엔터티 본문만 인코딩하지만, 전송인코딩 에서는 인코딩 전체 메시지에 대해 적용되며 메시지 전체 구조를 바꾸게 된다. (O / X)

2. 전송 인코딩을 제어하고 서술하기 위해 정의된 헤더는 단 두개 뿐이다. (O / X)

3. 서버가 청크 인코딩 데이터를 보낼 때 본문이 끝났음을 알려야 하는데 그 방법으로 옳은것은 무엇일까요?

- a. Content-Length헤더에 본문의 길이를 담아서 보내준다.
- b. 본문의 끝에 데이터의 끝을 알리는 특별한 종결문자를 포함시켜 보내준다.
- c. 여러 청크로 쪼개서 보내기를 반복하다가(버퍼에 담아 한덩어리를 그 크기와 함께 보냄) 크기가 0인 청크로 본문이 끝났음을 알린다.

4. 클라이언트도 청크 인코딩된 데이터를 서버에 전송할 수 있다. 이때 클라이언트는 서버가 청크 인코딩을 받아들여줄지 모르기 때문에, 청크 요청이 `__________________`응답으로 거절당하는 것에 대비해야 한다.

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 콘텐츠 인코딩은 단지 메시지의 엔터티 본문만 인코딩하지만, 전송인코딩 에서는 인코딩 전체 메시지에 대해 적용되며 메시지 전체 구조를 바꾸게 된다. (O)

2. 전송 인코딩을 제어하고 서술하기 위해 정의된 헤더는 단 두개 뿐이다. (O)

3. 동적으로 본문이 생성되면서, 서버는 그중 일부를 버퍼에 담은 뒤 그 한 덩어리를 그의 크기와 함께 보낼 수 있다. 본문을 모두 보낼 때까지 이 단계를 반복한다. 서버는 크기가 0인 청크로 본문이 끝났음을 알리고 다 음 응답을 위해 커넥션을 열린 채로 유지할 수 있다.

4. 411 Length Required
</div>
</details>
<br>

### __15.7__ 　  시간에 따라 바뀌는 인스턴스　 `mihykim`
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

### __15.8__ 　  검사기와 신선도　 `mihykim`
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

### __15.9__ 　  범위 요청　 `daelee`
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

### __15.10__ 　 델타 인코딩　 `daelee`
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
