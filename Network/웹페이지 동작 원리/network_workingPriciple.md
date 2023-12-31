# 목차

# 웹페이지 동작 원리
우리는 하루에 수 십번도 웹페이지를 들락날락 거린다.<br/>
하지만 어떻게 데이터가 처리되는지 확인을 할 수 없는데,<br/>
이는 웹페이지 뒤에 숨어 처리를 하는 과정이 너무 빨리 일어나 우리가 알아차리지 못하기 때문이다.

우리가 요청한 웹페이지가 나오기까지 여러 단계를 거치는데,
그 중 일부를 머저 보도록 하겠다.<br/>
데이터는 어떻게 처리될까?<br/>

웹이 동작하기 위해선 여러 요소(행위)들이 필수적으로 필요한데,<br/>
**1. 페이지**<br/>
**2. 클라이언트**<br/>
**3. 서버**<br/>
**4. 요청 / 응답**<br/>
**5. DB** 이렇게 나뉘어진다.
<br/><br/>

어찌보면 객체가 행동하는지 구조와 나름 비슷해 보이는데,
1. 소비자가 클릭을 하면<br/>
2. 해당 클릭을 페이지에서 반응<br/>
3. 해당 반응을 클라이언트가 서버에게 전달<br/>
4. 전달 받은 서버는 응답하기 위해 준비를 한다.<br/>
*개별적으로 하나의 행동이 여러 이해 관계 및 요소들과 interaction을 이루는데,<br/> 그 중 자신이 처리 해야하는 일 이외를 바라보는 친구는 없다.*

<br/>

## 네트워크 통신 Customer Journey
***조금 더 세부적으로 어떻게 이루어져 있는지 따라가 보자!***<br/><br/>
먼저 사용자인 우리는 검색을 하기 위해 브라우저를 실행한다.<br/>
만일 실행된 브라우저에서 유튜브를 입력한다면 유튜브를 화면에 보여주기 전까지 어떤 과정을 거치게 될까??

### <U>1. 클라이언트</U>
<img src="asset/클라이언트 브라우저.png" width="400">

>클라이언트는 일반적으로 사용자가 웹에 접근하기 위해 사용하는 프로그램을 의미한다.<br/>
대부분은 웹을 접근할 때 웹 브라우저를 사용하기에 '웹 브라우저'가 웹 클라이언트라고 불리는데,<br/>
Safari, Chrome, Microsoft, FireFox 등 다양하게 분포되어 있다.
<br/>
위에 정리한 브라우저 중 하나라도 들어온 이상, 우리는 네트워크 상태에 들어가게 된다.<br/>

클라이언트에 유튜브 URL을 입력하고 엔터를 친 이상, <br/>
가장 먼저 DNS 서버를 통해 URL에 해당하는 IP를 검색하는 과정을 거친다.<br/>

### <U>2. DNS 서버</U>
<img src="asset/DNS 서버.png" width="400">

>사용자가 입력한 URL을 판독해주는 서버라고 생각하면 이해하기 쉽다.<br/>
딕셔너리 값 형태로 IP와 URL을 연결해두어 사용자가 URL을 입력하면 해당 URL에 매칭되는 IP를 서버에서 불러오는 과정을 거친다.<br/>
해당 IP는 웹 서버로 보내져 지정된 웹페이지를 구성하는데 필요한 요소들을 요청하게 된다.

DNS 서버에서 유튜브 URL이 유효한지, 알맞는 IP를 할당받은 이후<br/>
이전에 배운 TCP/IP 기술을 통해 내 컴퓨터와 웹 서버가 온전히 연결된다. (웹 서버는 이후 후술!)
<br/>
*이 과정에서 3way handshaking이 이루어진다면 이제 HTTP 통신이 진행된다.*

### <U>3. HTTP</U>
<img src="asset/HTTP 데이터.png" width="400">

> HTTP는 HyperText Transfer Protocol의 약자로 일종의 메시지 형태로 데이터를 전송하는 메서드를 의미<br/>
HTTP 메시지에는 입력한 URL, IP에 일치하는 페이지를 구성하기 위해 필요한 정보 내용이 보내진다.

HTTP 메시지는 아래와 같은 구조를 가진다.

```swift
// 메서드 (GET / POST) + URL + HTTP 버전
GET https://velog.io/@surim014 HTTP/1.1
// 헤더 - 요청에 대한 정보
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
// 본문 - 요청을 할 때 보내는 데이터
Upgrade-Insecure-Requests: 1
```

### <U>3.1 응답 / 요청</U>
> 위에 서술한 HTTP 메시지가 클라이언트에서 서버에서 보내질 때는 요청,<br/>
서버에서 데이터를 받아 클라이언트로 뿌려질 때를 응답이라 한다.
결국 HTTP는 양방향으로 메시지가 보내지는 것이라는 점!

- 관련 내용은 후술

### <U>4. 웹 서버</U>
<img src="asset/웹 서버.png" width="400">

> 웹 페이지, 사이트 또는 앱 등을 저장하는 프로그램이다.<br/>
서버는 페이지에서 일어난 사용자의 행동을 가져온 클라이언트 요청에 따라<br/>
페이지를 구성하는데 필요한 HTML, CSS, JS, Image 등을 가져와서 클라이언트에게 보내주는 역할을 한다.<br/>
여기에도 다양한 종류가 존재하는데, 웹서버(Apache Web Server), GWS, IIS 등이 존재한다.

3 단계에서 유튜브 IP에 필요한 데이터를 받기 위해 HTTP 요청 메시지를 클라이언트가 보냈다.<br/>
해당 메시지를 받고나면 웹 서버에서는 여러가지 일을 처리하는데,<br/>

**1. 빠른 데이터 처리를 위해 역할 분할**<br/>
**2. DB에서 필요한 데이터를 서치**
<br/>

### <U>4.1 WAS (Web Application Server) - 데이터 처리</U>
> 웹 서버는 정적 자료 처리, WAS는 동적 자료 처리를 담당한다.<br/>
정적인 데이터라면 HTML, CSS, Javascript 등인 화면을 구상하는데 사용되는 이미지, 글 등이라 볼 수 있다.<br/>
WAS가 담당하는 동적인 자료는 사용자 입장에서 발생하는 데이터라 볼 수 있다.<br/>
<br/>
결국 Web 서버는 HTTP 요청에 맞게 뿌리는 역할만 처리하고 - <br/>WAS는 Web 서버에서 가져 온 데이터를 사용자 추가 인터렉션에 맞게 데이터들이 반응하도록 만드는 역할이라 볼 수 있다.

*웹 서버의 보조 역할로 이해할 수 있을 것 같다.*<br/>
웹 서버는 요청을 받아서 하달만 했을 뿐, 실제 사용자 입장에서 데이터 처리는 WAS에서 하는 구조.<br/>
이 이유는 서버에서 모든 일을 처리할 경우, 과부하가 발생할 가능성이 높아지기에 WAS와 나누는 것.


### <U>4.2 DB (DataBase)</U>
> 데이터베이스는 필요한 자원들을 저장한 저장소이다.<br/>
데이터베이스는 따로 응답하는 구조가 아닌 데이터의 정보만 저장하는 공간이라고 이해할 수 있다.

따라서 HTTP 요청에 맞는 데이터를 웹서버는 DB에서 찾아 매칭을 시키고<br/>
HTTP 응답을 할 때 해당 데이터를 넘기는 동시에 WAS에게 구성된 화면에 대한 응답을 처리하도록 한다.

### <U>5. 웹 페이지</U>
해당 과정을 거치면 우리는 클라이언트 페이지가 유튜브 페이지로 새로고침 되면서 콘텐츠를 볼 수 있게 되는 것이다.


### <U> 6. 웹 페이지 구성 요소</U>
<img src="asset/HTML CSS JS.png" width="400">

- **HTML(HyperText MarkupLanguage)**<br/>
웹사이트 자체의 구조를 구성하는데, 웹사이트의 디테일을 채우기보다 무엇이 버튼인지, 이미지인지 등의 영역을 지정한다.<br/>
- **CSS (Cascading Style Sheets)**<br/>
지정된 구조에 해당하는 Component를 이쁘게 만드는 작업을 한다.<br/>
- **JavaScript**<br/>
해당 Component들에 대한 로직을 구성한다고 한다.<br/>
다른 말로 서버에서 초기 웹 페이지를 load를 한 이후, 변경되는 모든 요소들에 대한 작업을 JavaScript에서 처리한다고 할 수 있다.<br/>
<br/><br/><br/>


### <U> 7. HTTP Request 분해하기</U>
HTTP 응답과 요청에는 크게 3가지가 존재한다.
1. Status Line
2. HTTP Header
3. Message Body

자세한 내용은 [링크](https://www.notion.so/fff65262b1d94fbbb5d5435634647dfd?pvs=4)를 확인하자


### 참고<br/>
- https://swimjiy.github.io/2019-11-03-How-Web-Works
- https://www.youtube.com/watch?v=hJHvdBlSxug
- https://stackoverflow.com/questions/51429617/http-requests-body-vs-param-vs-headers-vs-data
- https://www.ibm.com/docs/en/cics-ts/5.2?topic=protocol-http-responses
