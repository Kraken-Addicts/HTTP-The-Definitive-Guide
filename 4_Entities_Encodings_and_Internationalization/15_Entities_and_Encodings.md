## 15장 :octopus: 엔터티와 인코딩

### __15.1__ 　  메시지는 컨테이너, 엔터티는 화물　 `yeosong`

인턴인 `yeosong`은 www.joes-hardware.com 에서 오고 갔던 HTTP 메시지를 살펴보고 있다.

각 문항에서 제시하는 정보를 확인하고 싶을 때, <보기>의 엔터티 관련 주요 헤더 중 어느 헤더를 찾아서 읽어야할까?

||<보기>||
|---|---|---|
|`a. Content-Type`       | `e. Content-Location`    |      `i. Expires`         |
|`b. Content-Length`     | `f. Content-Range`       |      `j. Allow`           |
|`c. Content-Language`   | `g. Content-MD5`         |      `k. ETag`            |
|`d. Content-Encoding`   | `h. Last-Modified`       |      `l. Cache-Control`   |

1) 엔터티 본문의 콘텐츠에 대한 체크섬                            
2) 전달되는 객체와 가장 잘 대응되는 자연어                         
3) 서버에서 이 콘텐츠가 생성 혹은 수정된 날                         
4) If-Match나 If-None-Match 요청을 받았을 때 인스턴스에 대한 검사기                    
5) 이 리소스에 대해 허용되는 요청 메서드 (ex GET, HEAD..)          
6) 이 데이터가 더 이상 신선하지 않은 것으로 간주되는 시점                  
7) 엔터티에 의해 전달된 객체의 종류                               
8) 이 문서를 캐시할 때 지킬 요청사항                


#### __15.1.1__ 　  엔터티 본문

다음 표를 참고하여 문장에 맞게 빈칸을 채우세요. 

![216CE84C52694FF020](https://user-images.githubusercontent.com/53321189/92330070-158d2e00-f0a7-11ea-9159-58f210858004.png)

엔터티 본문은 헤더 필드의 끝을 의미하는 `1)____` 바로 다음부터 시작한다. 

`1)____`는 헥스덤프 상에서 `2)_____`로 표시된다. 이것 다음 글자부터가 엔터티 본문이다.

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
#### __15.1.1__ 　  메시지는 컨테이너, 엔터티는 화물

인턴인 `yeosong`은 www.joes-hardware.com 에서 오고 갔던 HTTP 메시지를 살펴보고 있다.

각 문항에서 제시하는 정보를 확인하고 싶을 때, <보기>의 엔터티 관련 주요 헤더 중 어느 헤더를 찾아서 읽어야할까?

||<보기>||
|---|---|---|
|`a. Content-Type`       | `e. Content-Location`    |      `i. Expires`         |
|`b. Content-Length`     | `f. Content-Range`       |      `j. Allow`           |
|`c. Content-Language`   | `g. Content-MD5`         |      `k. ETag`            |
|`d. Content-Encoding`   | `h. Last-Modified`       |      `l. Cache-Control`   |

1) 엔터티 본문의 콘텐츠에 대한 체크섬                                `g. Content-MD5`
  - MD5는 보안용으로는 약해서 지금은 쓰이지 않지만, 체크섬 용도로는 지금도 쓰이고 있다고 합니다.
2) 전달되는 객체와 가장 잘 대응되는 자연어                            `c. Content-Language` 
3) 서버에서 이 콘텐츠가 생성 혹은 수정된 날                           `h. Last-Modified`    
4) If-Match나 If-None-Match 요청을 받았을 때 인스턴스에 대한 검사기    `k. ETag`                           
5) 이 리소스에 대해 허용되는 요청 메서드 (ex GET, HEAD..)             `j. Allow`  
6) 이 데이터가 더 이상 신선하지 않은 것으로 간주되는 시점                 `i. Expires`   
7) 엔터티에 의해 전달된 객체의 종류                                  `a. Content-Type`
8) 이 문서를 캐시할 때 지킬 요청사항                                 `l. Cache-Control`

#### __15.1.1__ 　  엔터티 본문

다음 표를 참고하여 문장에 맞게 빈칸을 채우세요. 

![216CE84C52694FF020](https://user-images.githubusercontent.com/53321189/92330070-158d2e00-f0a7-11ea-9159-58f210858004.png)

엔터티 본문은 헤더 필드의 끝을 의미하는 `1)CRLF` 바로 다음부터 시작한다. 

`1)CRLF`는 헥스덤프 상에서 `2)0d 0a`로 표시된다. 이것 다음 글자부터가 엔터티 본문이다.

아스키 테이블에서 CR은 0x0d, LF는 0x0a 임을 확인할 수 있다.

</div>
</details>
<br>

### __15.2__ 　  Content-Length: 엔터티의 길이　 `hylee`

1. HTTP 스터디 이후 Content- Length 헤더에 대해 얘기하는데 큰일날 사람을 모두 골라주세요

      새초 : Content- Length 헤더는 메시지의 엔터티 본문의 크기를 비트단위로 나타낸다.

      태리 : 압축 된 파일을 보낼 때 Content- Length 헤더에는 압축 되기 전 원본 크기로 표현해서 보내야된다.

      쿠킴 : Content- Length 헤더를 이용해서 서버 충돌로 인해 메시지가 잘렸는지 감지할 수 있다.

      준서 : 엔터티 본문을 포함한 메시지에서는 필수적으로 있어야 된다.

      여름 : 커넥션을 공유하는 메시지를 올바르게 분할할 때 필요하다.
<br>
  
2. 엔터티 본문 길이 판별을 위한 규칙을 위해 아래 규칙들을 알맞은 우선 순위로 배열해주세요

  
    (a) 메시지가 Transfer-Encoding 헤더를 포함하고 있는지 확인한다.
  
    (b) 본문을 갖는 것이 허용되지 않는 특정 타입의 HTTP 메시지인지 확인한다.

    (c) 메시지가 Content- Length 헤더를 갖는지 확인해본다.
  
  
<br>

  
3. HTTP/ 1.1 명세는 요청에 본문은 있지만 Content-Length 헤더는 없는 경우, 
   메시지의 길이를 판별할 수 없다면 _______ 응답을 보내고 
   유효한 Content- Length를 요구하고 싶다면  _________ 응답을 보내라고 조언하고 있다.
   
   `<보기>`<br> `400 Bad Request`, `404 Not Found`, `405 Method Not Allowd`,<br> `410 Content Required`, `411 Length Required`, `418 I'm a teapot`


  
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1"> 
  
1. HTTP 스터디 이후 Content- Length 헤더에 대해 얘기하는데 큰일날 사람을 모두 골라주세요
      > 정답 : 새초, 태리, 준서

      <b>새초</b> : Content- Length 헤더는 메시지의 엔터티 본문의 크기를 <b>`바이트단위`</b> 로 나타낸다.

      <b>태리</b> : 압축 된 파일을 보낼 때 Content- Length 헤더에는 <b>`압축 된 후`</b> 크기로 표현해서 보내야된다.

      쿠킴 : Content- Length 헤더를 이용해서 서버 충돌로 인해 메시지가 잘렸는지 감지할 수 있다.

      <b>준서</b> : <b>`메시지를 청크 인코딩으로 전송하지 않는 이상`</b>엔터티 본문을 포함한 메시지에서는 필수적으로 있어야 된다.

      여름 : 커넥션을 공유하는 메시지를 올바르게 분할할 때 필요하다.
      
 <br>

  
2. 엔터티 본문 길이 판별을 위한 규칙을 위해 아래 규칙들을 알맞은 우선 순위로 배열해주세요

    > 정답 : (b) -> (a) ->(c)
    
    (b) 본문을 갖는 것이 허용되지 않는 특정 타입의 HTTP 메시지인지 확인한다.
    
        본문을 갖는 것이 허용되지 않는 특정 타입의 HttP 메시지에서는, 본문 계산을위한 Content-Length 헤더가 무시된다.
        이 경우 Content-Length 헤더는 부가정보에 불과하며, 실제 본문 길이를 서술하지 않기 때문이다.
        그렇기 때문에 본문을 갖는 것이 허용되지 않는 특정 타입의 HTTP 메시지인지를 Content- Length 헤더보다 먼저 검사한다.
       
    (a) 메시지가 Transfer-Encoding 헤더를 포함하고 있는지 확인한다.

        Transfer-Encoding 헤더 필드를 갖고 있는 메시지를 받았다면 반드시 Content- Length 헤더를 무시해야 한다.
        왜냐하면 전송 인코딩은 엔터티 본문을 표현하고 전송하는 방식(그리고 아마 전송된 바이트 크기도)을 바꿀 것이기 때문이다.
        그렇기 때문에 Content- Length 헤더보다 Transfer-Encoding 헤더를 먼저 검사해야 한다.

    (c) 메시지가 Content- Length 헤더를 갖는지 확인해본다.
    
         메시지가 Content- Length 헤더를 갖는다면(그리고 메시지 유형이 엔터티 본문을 허용한다면)
         Transfer-Encoding 헤더가 존재하지 않는 이상 Content-Length 값은 본문의 길이를 담게되기 때문에
         이것으로 엔터티의 본문 길이를 판별할 수 있다.
    
    
  
<br>

  
3. HTTP/ 1.1 명세는 요청에 본문은 있지만 Content-Length 헤더는 없는 경우, 
   메시지의 길이를 판별할 수 없다면 (1)____________ 응답을 보내고 
   유효한 Content- Length를 요구하고 싶다면 (2)____________ 응답을 보내라고 조언하고 있다.
   
   `<보기>`<br> `400 Bad Request`, `404 Not Found`, `405 Method Not Allowd`,<br> `410 Content Required`, `411 Length Required`, `418 I'm a teapot`

   > 정답 : (1) 400 Bad Request (2) 411 Length Required
</div>
</details>
<br>

### __15.3__ 　  엔터티 요약　 `kukim`
1. HTTP는 TCP/IP와 같이 신뢰할 만한 전송 프로톨콜 위에서 구현되기 때문에 메세지 일부분에는 전송중에 변형되는 일이 없다. (O / X)
2. Content-MD5 헤더는 서버가 엔터티 본문에 MD5 알고리즘을 적용한 결과를 보내기 위해 사용된다. 중간에 있는 프락시와 캐시는 그 헤더를 변경하거나 추가하지 않고 end-to-end 무결성을 검증하겠다는 목적을 가지고 사용된다. 메세지 무결성 검사를 할 수 있고 추가로 해시 테이블의 키로 사용하여 콘텐츠 중복 저장을 방지하는 목적으로도 사용할 수 있다. 이처럼 Content-MD5 헤더는 자주 전송된다. (O / X)

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. HTTP는 TCP/IP와 같이 신뢰할 만한 전송 프로톨콜 위에서 구현되기 때문에 메세지 일부분에는 전송중에 변형되는 일이 없다. (O / X)
  - X 불완전한 트랜스코딩 프락시, 중개자 프락시를 비롯한 여러 이유로 메세지의 일부분이 전송 중에 변형되는 일이 일어난다.
2. Content-MD5 헤더는 서버가 엔터티 본문에 MD5 알고리즘을 적용한 결과를 보내기 위해 사용된다. 중간에 있는 와 캐시는 그 헤더를 변경하거나 추가하지 않고 end-to-end 무결성을 검증하겠다는 목적을 가지고 사용된다. 메세지 무결성 검사를 할 수 있고 추가로 해시 테이블의 키로 사용하여 콘텐츠 중복 저장을 방지하는 목적으로도 사용할 수 있다. 이처럼 Content-MD5 헤더는 자주 전송된다. (O / X)
  - X ('자주 전송되진 않는다'라고 책에 작성되어 있는데 Content-MD5는 현재 RFC 7231에 따라 사라졌다.)
  - 또한 책에서 content-md5는 잘 사용하지 않고Want-digest란 기술이 책에 RFC3230으로 승인되었다고 나오지만 사실상 이것도 더이상 사용하지 않고 RFC7231의 "selected representation"란 키워드로 다시 명시되어 엔터티를 요약하고 있다. 자세한 내용은 RFC7231을 참고하자
  - [https://www.rfc-editor.org/rfc/rfc7231.txt](https://www.rfc-editor.org/rfc/rfc7231.txt)
    ```
       The Content-MD5 header field has been removed because it was
       inconsistently implemented with respect to partial responses.
    ```
    

</div>
</details>
<br>

### __15.4__ 　  미디어 타입과 차셋(Charset)　 `kukim`
1. Content-Type 헤더 필드는 엔터티 본문의 `(  )` 타입을 기술한다.
2. 엔터티가 콘텐츠 인코딩을 거친 후 어떤 방법으로 인코딩 했는지 명시한다면 Content-Type 헤더를 명시할 필요가 없다. (O / X)
3. Content-Type 헤더는 내용 유형을 자세히 지정하기 위해 매개변수도 지원한다. ( O / X)
4. HTTP는 본문 메시지 콘텐츠를 보낼 때 한 번에 하나의 데이터 폼만 전송 할 수 있다. (O / X)
5. 다음 괄호를 채우시오
```bash
HTTP/1.0 206 Partial content
Server: Microsoft-IIS/5 . 0
Date: Sun, 10 Dec 2000 19:11:20 GMT
Content-Location:
Content-Type: multipart/x-byteranges; boundary=--[kukim]-- 
Last-Modified: Sat, 09 Dec 2000 00:38:47 GMT
--( )-- 
Content-Type: text/plain 
Content-Range: bytes 0-174/1441
Fourscore and seven years ago our fathers brough forth on this continent a new nation, conceived in liberty and dedicated to the proposition that all men are created equal.
--( )-- 
Content-Type: text/plain 
Content-Range: bytes 552-761/1441
But in a larger sense , we can not dedicate , 씨e can not consec rate , we can not hallo씨 this ground. The brave men, living and dead who struggled here have consecrated it far above our poor po싸er to add or detract.
--( )-- 
Content-Type: text/plain 
Content-Range: bytes 1344-1441/1441
and that government of the people, by the people, for the people shall not perish from the earth.
--( )--
```

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. Content-Type 헤더 필드는 엔터티 본문의 `(  )` 타입을 기술한다.
  - MIME(Multipurpose Internet Mail Extensions)
2. 엔터티가 콘텐츠 인코딩을 거친 후 어떤 방법으로 인코딩 했는지 명시한다면 Content-Type 헤더를 명시할 필요가 없다. (O / X)
  - X, Content-Type 헤더가 원본 엔터티 본문의 미디어 타입을 명시해야 한다.
3. Content-Type 헤더는 내용 유형을 자세히 지정하기 위해 매개변수도 지원한다. ( O / X)
  - O : Content-Type: text/html; charset=iso-8859- 4 처럼 인코딩 버전도 입력할 수 있다.
4. HTTP는 본문 메시지 콘텐츠를 보낼 때 한 번에 하나의 데이터 폼만 전송 할 수 있다. (O / X)
  - X : 멀티파트 미디어 타입을 통해 서로 붙어있는 여러 개의 메시지를 포함하여 보낼 수 있다.

5. 다음 괄호를 채우시오
```bash
HTTP/1.0 206 Partial content
Server: Microsoft-IIS/5 . 0
Date: Sun, 10 Dec 2000 19:11:20 GMT
Content-Location:
Content-Type: multipart/x-byteranges; boundary=--[kukim]-- 
Last-Modified: Sat, 09 Dec 2000 00:38:47 GMT
--(kukim)-- 
Content-Type: text/plain 
Content-Range: bytes 0-174/1441
Fourscore and seven years ago our fathers brough forth on this continent a new nation, conceived in liberty and dedicated to the proposition that all men are created equal.
--(kukim)-- 
Content-Type: text/plain 
Content-Range: bytes 552-761/1441
But in a larger sense , we can not dedicate , 씨e can not consec rate , we can not hallo씨 this ground. The brave men, living and dead who struggled here have consecrated it far above our poor po싸er to add or detract.
--(kukim)-- 
Content-Type: text/plain 
Content-Range: bytes 1344-1441/1441
and that government of the people, by the people, for the people shall not perish from the earth.
--(kukim)-- 
```

</div>
</details>
<br>

### __15.5__ 　  콘텐츠 인코딩　 `junslee`

1. 다음은 콘텐츠 인코딩 과정을 순서에 따라 나열한 것입니다. 빈칸을 채워주세요.<br>

- 웹서버가 원본 Content-Type과 `________________`헤더를 수반한 원본 응답 메시지를 생성한다.
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
- __보기에서 알맞은 단어를 골라 빈 칸을 채워넣어 주세요__ <br><br> `<보기>`<br>`인스턴스 조작(instance manipulation)`, `인스턴트 식품(instant food)`, `범위요청(range request)`, `더미요청(dummy request)`, `델타인코딩(delta-encoding)`, `됐다인코딩(successful-encoding)`

    - HTTP 프로토콜은 어떤 특정한 종류의 요청이나 응답을 다루는 방법들을 정의하는데, 이것은 `___________`이라 불리며, 객체의 인스턴스에 작용한다. 이들 중 대표적인 두 가지가 `___________`과 `___________`이다. 이 둘 모두가, 클라이언트가 자신이 갖고 있는 리소스의 사본이 서버가 갖고 있는 것과 정확히 같은지 판단하고, 상황에 따라서는 새 인스턴스를 요청할 수 있는 능력을 가질 것을 요구한다.

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
- HTTP 프로토콜은 어떤 특정한 종류의 요청이나 응답을 다루는 방법들을 정의하는데, 이것은 `인스턴스 조작`이라 불리며, 객체의 인스턴스에 작용한다. 이들 중 대표적인 두 가지가 `범위요청`과 `델타인코딩`이다. 이 둘 모두가, 클라이언트가 자신이 갖고 있는 리소스의 사본이 서버가 갖고 있는 것과 정확히 같은지 판단하고, 상황에 따라서는 새 인스턴스를 요청할 수 있는 능력을 가질 것을 요구한다.

</div>
</details>
<br>

### __15.8__ 　  검사기와 신선도　 `mihykim`

- __잘나가는 캐시프락시서버 ‘현준’ 은 오늘도 수많은 클라이언트의 요청을 처리하느라 바쁘다고 합니다.__
- __다음은 ‘현준’ 의 업무처리 계획입니다. <br>아래 그림을 참고하여 누구의 업무를 처리하려고 하는 것인지 맞춰보세요.__ <p align="center"><img src="https://user-images.githubusercontent.com/60066472/92241624-80006b80-eef9-11ea-9b6c-60f3e5d56e3c.png" width="650"></p>

    - __객관식 1 ★__ “`ㅇㅇ`님이 요청한 리소스는 정확도가 높은 최신 사본이 필요하신가보다! 꼭 ‘태혁’님이랑 재검사해서 보내드려야지!”
    - __객관식 2 ★__ “`ㅇㅇ`님은 많이 급하신가? 신선하지 않게된 지 하루 지난 사본도 괜찮다고 하셨네? 얼른 보내드려야지!”
    - __객관식 3 ★__ “`ㅇㅇ`님은 꼭 나한테서 찾고싶으신거구나! ‘태혁’님께 따로 여쭤볼 필요가 없겠어~”
    
<br><br>
  
- __점점 더 똑똑해지는 클라이언트들은 자신이 원하는 리소스를 '조건부'로 요청하기 시작했습니다. <br>아래 그림을 참고하여 물음에 답해보세요.__ <p align="center"><img src="https://user-images.githubusercontent.com/60066472/92244093-69f4aa00-eefd-11ea-81d5-b2aec2ba9cf3.png" width="650"></p>

    - __주관식 1 ★__ 똑똑한 ‘준서’ 는 10시에 http study파일이 변경되었다는 이야기를 듣고, 조건부요청을 보냈지만 안타깝게도 최신화된 파일을 받지 못했습니다. 그 이유는 무엇일까요?
    - __주관식 2 ★__ 똑똑한 ‘정아’ 는 Etag를 활용한 조건부 요청을 보냈습니다. ‘현준’ 이 부지런히 알아보니 지난번 응답에서 태혁이 보낸 Etag는 ‘grownup-kido’였었습니다. 이때 ‘정아’ 는 캐시된 사본을 받게 될까요? 이유는 무엇인가요?
    - __주관식 3 ★__ 똑똑한 ‘건희’ 또한 Etag를 활용한 조건부 요청을 보냈습니다. 부지런한 ‘태혁’ 은 세심하게 사이트를 가꾸고 있었기 때문에 v.9.0이후 의미상 두드러지지는 않지만 여러가지 변화들이 있었는데요. 이때 ‘건희＇는 캐시된 사본을 받게 될까요? 이유는 무엇인가요?

<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
- __객관식 1__ “`여름`님이 요청한 리소스는 정확도가 높은 최신 사본이 필요하신가보다! 꼭 ‘태혁’님이랑 재검사해서 보내드려야지!”
- __객관식 2__ “`대현`님은 많이 급하신가? 신선하지 않게된 지 하루 지난 사본도 괜찮다고 하셨네? 얼른 보내드려야지!”
- __객관식 3__ “`성상`님은 꼭 나한테서 찾고싶으신거구나! ‘태혁’님께 따로 여쭤볼 필요가 없겠어~”
- __주관식 1__
    - 사실 10시 00분 00초 1마이크로세컨드에 바뀌었다...!
    - 최종 변경 시각은 리소스가 마지막으로 수정된 시각을 의미함에도 불구하고 약한 검사기로 간주되는데, 정확도가 최대 1초에 불과하기 때문이다. 리소스는 1초에 여러번 변경될 수 있고 서버는 1초에 수천 번의 요청을 처리하기 때문에, 최종변경 시각은 변경이 발생했음을 항상 반영해주지는 못한다.
- __주관식 2__
    - 캐시된 사본이 아니라 원서버의 사본을 새로 받는다.
    - If-None-Match 요청 유형은 ETag 검사기를 이용해 지난번 ETag 응답 헤더에 들어있던 것과 엔터티 태그가 다르다면, 그 리소스의 사본을 보내라는 의미의 조건부 요청이다.
    - Etag 헤더는 강한 검사기로 간주되는데, 서버는 ETag 헤더에 매 변경마다 구분되는 값을 넣어두기 때문이다. 버전번호와 요약체크섬은 ETag 헤더의 좋은 후보이지만, 그 외의 어떤 텍스트도 포함할 수 있다.
- __주관식 3__ : `성상`
    - 캐시된 사본을 받는다.
    - 클라이언트가 약한 엔터티 태그 (/W)를 보낸 경우, 서버는 콘텐츠가 w/ 뒤에 붙어있는 태그 이후로 의미있는 변경이 있었을 때만 본문을 반환할 것이다.

</div>
</details>
<br>

### __15.9__ 　  범위 요청　 `daelee`
그림은 범위를 수반한 HTTP 트랜젝션의 예를 보여줍니다.  (a), (b)가 의미하는 메시지 내용을 아래 보기에서 확인한 뒤 빈칸의 헤더를 채워보세요.

**(a) : 서버는 `byte` 단위로 범위 요청을 받아들일 수 있습니다.** 

**(b) : `20224 byte` 이후의 부분을 요청합니다.**

![범위요청](https://user-images.githubusercontent.com/37580034/92309919-69830e80-efe4-11ea-99dc-375192fe4b48.png)
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 그림은 범위를 수반한 HTTP 트랜젝션의 예를 보여줍니다.  (a), (b)가 의미하는 메시지 내용을 아래 보기에서 확인한 뒤 빈칸의 헤더를 채워보세요.

**(a) : 서버는 `byte` 단위로 범위 요청을 받아들일 수 있습니다.** 

**(b) : `20224 byte` 이후의 부분을 요청합니다.**

![범위요청](https://user-images.githubusercontent.com/37580034/92309919-69830e80-efe4-11ea-99dc-375192fe4b48.png)

> **정답**
>
> (a) : `Accept-Ranges: bytes` 
>
> (b) : `Range: bytes=20224-` 혹은 `Range: bytes=20224-65537` 
>
> 서버는 클라이언트에게 범위를 받아들일 수 있는지를 `Accept-Range` 헤더를 응답에 포함시키는 방법으로 알려줄 수 있다. 이 헤더의 값은 측정의 단위이며, 주로 `바이트`이다.
>
> 위 예에서 클라이언트는 리소스의 처음 20224바이트만을 받은 뒤 커넥션을 종료했다. 이후에는 Range 헤더를 통해 처음 20224바이트 이후의 부분을 요청한다. 문서의 크기를 모를때에는 몇 바이트까지인지 명시하지 않아도 된다.

</div>
</details>
<br>

### __15.10__ 　 델타 인코딩　 `daelee`
1. 델타 인코딩은 사본을 만들어 놓은 뒤 문서 전체를 빠르게 통신하여 **전송속도을 최적화**하는 HTTP 프로토콜의 확장이다. **(O / X)**

  
2. 아래 표는 델타 인코딩에 사용되는 헤더를 보여줍니다. 각 헤더와 설명을 바르게 짝지어보세요.

   ![델타인코딩](https://user-images.githubusercontent.com/37580034/92309915-6556f100-efe4-11ea-8abe-80b7a21aa314.png)

 


4. 델타 인코딩을 구현하기 어려운 이유는? (최소 25자)

  
<details>
<summary> <b> :page_facing_up: 답지 </b>  </summary>
<div markdown="1">
  
1. 델타 인코딩은 사본을 만들어 놓은 뒤 문서 전체를 빠르게 통신하여 **전송속도을 최적화**하는 HTTP 프로토콜의 확장이다. **(O / X)**

   > 정답 : X
   >
   > 클라이언트에게 최신 인스턴스를 제공할 때, 전체를 보내는 대신 사본의 변경 부분만을 서버가 보낸다면 클라이언트는 더 빠른 응답을 얻을 수 있을 것이다.
   >
   > 델타 인코딩은 이처럼 변경된 부분만 통신하여 **전송량을 최적화**하는 HTTP 프로토콜의 `확장`이다.

2. 아래 표는 델타 인코딩에 사용되는 헤더를 보여줍니다. 각 헤더와 설명을 바르게 짝지어보세요.

   ![델타인코딩](https://user-images.githubusercontent.com/37580034/92309915-6556f100-efe4-11ea-8abe-80b7a21aa314.png)

   > **정답** 
   >
   > ![델타_정답](https://user-images.githubusercontent.com/37580034/92309918-6720b480-efe4-11ea-897f-f128626834be.png)
   >
   > 클라이언트는 자신이 갖고 있던 버전에 대한 식별자인 `ETag` 헤더 값을 `If-None-Match` 헤더에 담아 조건부 요청을 한다. 동시에 클라이언트는 `A-IM` 헤더를 보내서 페이지에 대한 델타를 받아들일 수 있음을 알려줄 수도 있다.
   >
   > - `A-IM`은 `Accept-Instance-Manipulation`의 약자이다.
   >
   > 서버는 클라이언트에게 요청 객체 자체가 아닌 인스턴스 조작을 보내고 있음을 말해주는 `226 IM Used` 상태 코드, 델타를 계산하는데 사용한 알고리즘을 명시한 `IM`헤더, 새로운 `ETag`, 그리고 델타를 계산하는데 기반이 된 문서의 ETag를 지정한 `Delta-Base` 헤더를 되돌려준다.
   >
   > **422p의 그림 15-10 참고**

3. 델타 생성기는 `______` 헤더에 지정된 알고리즘를 이용하여 기저 문서와 최신 인스턴스 사이의 델타를 계산한다. 

   > 정답 : `A-IM` 헤더
   >
   > 클라이언트는 `A-IM` 헤더에 받아들일 수 있는 인스턴스 조작의 종류를 명시할 수 있다. 서버는 `IM` 헤더에 사용한 인스턴스 조작의 종류를 명시할 수 있다.

4. 델타 인코딩을 구현하기 어려운 이유는? (최소 25자)

   > 정답 : 페이지가 변경되는 **매 순간의 사본**을 모두 유지해야 하기 때문.
   >
   > 이를 지원하는 서버는 자신이 제공하는 페이지가 변경되는 **매 순간의 사본**을 모두 유지해야 하기 때문이다. 결국, 서버는 반드시 클라이언트가 가지고 있던 이전 버전의 사본들을 유지해고자 **저장 공간**을 늘려야한다. 이는 전송량 감소로 얻은 이득을 **무의미**하게 한다.

</div>
</details>
<br>
