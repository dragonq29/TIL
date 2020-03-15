## Java Script

* 자바스크립트에서는 코드 한줄 끝에 세미콜론은 (;) 붙여도 되고 붙이지 않아도 됨 (단, return 뒤에 반환할 값이 없을때는 ; 를 보통 씀)

* 자바스크립트 프로그램을 확장자가 .js인 자바스크립트 파일로 작성하고, HTML 파일에서 해당 자바스크립트 파일을 실행시키는 구문을 추가함

* var 는 자료형이 따로 없음. 문자 숫자 다들어감 (사실 3가지 자료형이 있음. Number, String, Boolean)

  * NaN와 Infinity 이란게 있고, 둘다 Number형임
  * undefined는 아예 사용자가 안건드린 변수, null은 사용자가 명시적으로 비어있음을 선언한 변수임

* 문자열에는 큰따옴표뿐("")와 작은따옴표('') 둘 중 무엇이든 사용할 수 있음. 단, 쌍은 맞춰줘야함

* 문자열의 Line Feed는 \n임

* 객체는 중괄호{} 로 만듬. 예)  var man = {name: "홍길동", age: 20, height: 180}

  * 객체 값을 가져오는 방법은 2가지 있음
    1. .을 씀. 예) man.name
    2. 대괄호[] 를 씀. 예) man["name"]
  * 객체 값 바로 바꿀수 있음. 예) man.name = "용용"; 

* 함수 만드는 법 (파라미터는 함수의 지역변수로 볼 수 있음)

  * ```
    function 함수이름(파라미터1, 파라미터2) {
        실행 코드
        return 결과값; // 결과값 반환이 필요 없을때는 결과값 생략(return만 씀)
    }
    
    이것은 var 함수이름 = function (파라1, 파라2) {~~~~} 로 된 것 처럼 개념적으로 볼 수 있음
    ```

* 문자열
  * 문자열 길이 구하는 법 : str.length 또는 str["length"]
  * 문자열 인덱스 접근 : str.charAt(0) (인덱스 범위를 벗어나면 ""을 반환)
  * 사실 문자열은 배열의 일종인 특수한 경우일 뿐임
* 배열
  * 배열 정의 var arr = [1, 2, 3, 4, 5];
  * 배열 접근 arr[3] : 4
  * 다양한 타입이 한 배열에 들어갈 수 있음 var mixed_arr = [1, true, 3.14, "string", {name: "object"}, [1, 2, 3]];
  * 배열 내 항목을 다루는 배열의 메소드
    * arr.pop() : 배열의 맨 뒤에 항목 빼서 반환
    * arr.push() : 배열의 맨 뒤에 항목 추가
    * arr.shift() : 배열의 맨 앞에 있는 항목 빼서 반환
    * arr.unshift() : 배열의 맨 앞에 항목 추가
    * arr.reverse() : 배열 순서 뒤집음 (반환값 뿐만 아니라 원본도 뒤집음)
    * arr.sort() : 오름차순 정렬
    * arr.concat(arr2) : arr에 arr2를 붙여서 반환 (원본에는 영향 없음)
    * arr.indexOf(7) : 7이 처음나오는 인덱스 반환
    * arrlastIndexOf(7) : 7이 마지막에 나오는 인덱스 반환

* if문, switch문, while문, for문 : 자바와 같음

  ```
  if (조건) {
  	// 코드
  }
  ```

* do while문 : 안의 코드가 적어도 한 번은 실행된다는게 while과 다름 (자바도 똑같을 듯?)

* for in문

  * ```
    var obj = {
    name: "object",
    weight: 30,
    isObject: true,
    arr: [1, 2, 3],
    obj: {property: 1}
    };
    Object.keys(obj); // ["name", "weight", "isObject", "arr", "obj"]
    var property_list = Object.keys(obj);
    for (var i = 0; i < property_list.length; i++ ) {
        var propertyName = property_list[i];
        console.log("\t", propertyName, ": ", obj[propertyName]);
    }
    for (var propertyName in obj) {
        console.log("\t", propertyName, ": ", obj[propertyName]);
    }
    ```

* in 연산자
  * 해당 속성의 이름이 객체에 존재하는지 검사하는 연산자
    * "name" in obj; -> ture
* let : var와 동일하게 변수를 선언 하는 것이지만, var와 다르게 생존주기가 블록('{', '}') 안임 (var는 범위가 function안임) 

* 만약 var로 생성한 변수명이 function 안에서 var로 생성한 변수명과 겹치면 새로 생성한 변수명이 생성되어 function을 빠져나갈때 까지 이전에 생성한 변수는 가려져서 그대로 있음

* function은 변수로 선언될 수 있음

  ```
  function f( ) {
      console.log("f is called");
  }
  var o = {name: "object", method: f}; // f 함수를 가짐
  
  f( );        // f is called 출력
  o.method( ); // 객체의 속성에 바인드된 함수로 호출. f is called 출력
  ```

* 클로저 (=private 변수의 존재??) : 함수와 함수가 선언된 유효 범위 환경(변수 등)을 외부에서 접근 못하게 하나로 싼 변수???
  
  * 자바스크립트가 태생적으로 프라이빗 메소드를 지원하지 않아, 클로저로 비슷하게 같은 기능을 하는 것??

#### 써본 메소드

* alert("Hello Javascript");  // 알람 팝업 띄움
* console.log("Hello developer console");  // 개발자 도구 콘솔 탭에 로그 출력
* var name = prompt("이름을 입력해 주세요.")  // 사용자 입력 받음
* typeof(a)  // 변수 a의 타입을 String으로 출력 (보통 콘솔에서 많이 쳐봄)
* pasreInt(문자열 )  // 문자열의 앞부분에서 정수 부분을 추출 (문자열(="180입니다") 를 파싱하면 180으로 나옴)
* parseFloat(문자열)  // 문자열의 앞부분에서 실수 부분을 추출
* Math.pow(A, B): A의 B승을 구함
* Math.sqrt(A): sqrt는 제곱근(square root)의 약자로 A의 제곱근을 구함
* Math.random( ): 괄호 안에 아무런 값을 넣지 않으면 0~1 사이의 난수를 발생

#### 질문

객체 선언시 =와 :의 차이점을 모르겠음 (언제 언제 쓰는건지)

* 변수 선언시 "="

* 변수 내부 항목 선언 및 값 정의시 ":"

* 참고

  * ```
    > var obj = {
        "str": "문자열",
        "num": 3.14,
        "boolean": true,
        "null": null,
        "undefined": undefined,
        "method": function a( ) {console.log("method") }
    }
    ```

----------

##CSS

* 기본

  * p 태그에 스타일 지정

    ```
    p {	// p라는 태그에 대해 스타일을 지정
    font-size: 1em; // 글자 크기를 1em으로 지정. em: 상대 크기를 나타내는 단위. 1->2 2배로 커짐
    color: #FF0000; // 글자 색을 빨간색으로 지정
    }
    ```

  * 작성한 p 태그를 적용

    ```
    <html>
        <head>
            <meta charset = "utf-8">
            <link rel = "stylesheet" href = "css.css">
        </head>
        <body>
            This is a HTML page
            <p>이 글씨는 CSS에 의해 꾸며집니다.</p>
        </body>
    </html>
    ```


* HTML에 스타일 적용 방법

  * head 태그 안에서 link 태그를 이용해 외부 파일 불러오기 (우선순위 하)

    ```
    <html>
        <head>
            <meta charset = "utf-8">
            <!- - link 태그로 외부 파일 불러오기 - ->
            <link rel = "stylesheet" href = "css.css">
        </head>
        <body>
    ```

  * head 태그 안에서 style 태그를 이용해서 정의하기 (우선순위 중)

    ```
    <html>
        <head>
            <meta charset = "utf-8">
            <link rel = "stylesheet" href = "css.css">
            <style>
                #songwriter, #lyricist{ <!- - 작곡가와 작사가를 오른쪽 정렬 - ->
                    text-align: right;
                }
            </style>
        </head>
    ```

  * 태그 안에 직접 style 속성을 이용해서 정의하기 (우선순위 상)

    ```
    <p id = "songwriter">작곡: 안익태</p>
    <p id = "lyricist" style = "color: red;">작사: 미상</p>
    ```

--------------

##HTML, CSS, JavaScript 관계

* JavaScript의 가장 바깥에서 this는 window임 (window는 생략 됨)
  
  * var a =1 하고나서 window.a 하면 1임
* window 내부 요소들 몇가지
  * window.location: 현재 브라우저의 주소
  * window.location.href: 현재 브라우저의 주소 창에 입력된 주소. 이 값을 수정하면 입력된 주소로 페이지가 이동.
  * window.navigator: 현재 브라우저에 관한 정보
  * window.screen: 현재 디스플레이의 너비와 높이
  * window.document: 현재 웹 페이지를 구성하는 HTML과 CSS가 모두 저장, 이 객체를 이용하여 HTML과 CSS에 접근

* DOM (Document Object Model)

  * 자바스크립트의 document 객체 구조

    * 이것으로 여러 HTML 엘리먼트에 접근 할 수 있음

    * document가 자식으로 head와 body를 가지고 있어서 타고 들어갈 수 있음

    * document를 이용한 id 로 객체 가져오는 법

      ```
      <p id = "lyricist" style = "color: red;" src = "test">
         <strong>작사:</strong> <i>미상</i>
      </p> // 이런식으로 만들면
      ```

      ```
      document.getElementById("lyricist") // 자바스크립트 내에서 id로 객체 가져올 수 있음
      var t = document.getElementById("lyricist");
      t.innerHTML;  // "<strong>작사:</strong> <i>미상</i>"
      t.innerText;  // "작사: 미상"
      ```

      여기서 값, 텍스트 변경 및 CSS 변경도 가능함

  * p 태그 같이 src에 접근 불가능한 것들은 getAttribute('src')를 이용하면 됨

    ```
    > t;
    < ▶<p id="lyricist" style="color: blue; font-size: 15pt;" src="test"><i>hello</i></p>
    > t.src;
    < undefined
    > t.getAttribute("src");
    < "test"
    
    // 값 바꿀때
    t.setAttribute("src","test2");
    ```

  * 조건에 맞는 엘리먼트 가져오는 법

    * ```
      document.getElementsByTagName("p");
      document.getElementsByClassName("lyric");
      document.getElementsByName("author"); // input태그 반환
      
      var a = document.getElementsByTagName("p");
      a[0] // 배열 형태로 접근 가능
      ```

    * querySelector 이용해서(CSS 선택자 기반) 가져오는 법 (입력 파라미터 종류)

      * \#idddd : idddd로 검색
      * taggggg : 그냥 적으면 태그 종류로 검색
      * .classss : 클래스 이름이 classss인 엘리먼트 검색
      * 기타
        * 대괄호([ ])를 이용해서 속성에 대한 필터를 넣을 수 있음
        * 오른쪽 꺾쇠( >)를 이용해서 자식(child) 중에서 검색할 수 있음
        * 쉼표(,)를 이용해서 엘리먼트를 여러 개 선택할 수 있음

      ```
      document.querySelector("#songwriter");	// id songwriter로 1개 엘리먼트 가져옴
      document.querySelectorAll("#songwriter") // id songwriter로 여러개(배열) 엘리먼트 가져옴
      document.querySelectorAll("h1, h2") // 쉼표로 여러 조건 넣을 수 있음
      ```

    * 엘리먼트 추가 복제 삭제

      * createElement( )
      * cloneNode( )
      * appendChild( )
      * insertBefore(hr, document.body.children[1] )
      * removeChild()

      ```
      hr = document.createElement("hr");	// <hr>(가로줄) 태그 엘리먼트 생성
      document.body.appendChild(hr);	// 생성한 엘리먼트를 적용 : body의 마지막 엘리먼트로 추가
      ```

* 콜백 함수

  * ```
    setTimeout(함수, 3000);	// 3초 뒤에 함수 콜
    setInterval(함수, 5000); // 5초마다 함수 콜 (리턴으로 인터벌ID 나옴)
    clearTimeout(); // 타임아웃 취소 (타임아웃 전에만 사용 가능)
    clearInterval(인터벌ID); // 인터벌 취소 (인터벌ID 넣어야함)
    ```

* 이벤트 종류

  * 폼 이벤트(Form Event): HTML 문서의 폼 엘리먼트에 변화가 생겼거나 제출(submit) 버튼 등이 눌렸을 때 발생하는 이벤트
  * 윈도 이벤트(Window Event): 페이지가 모두 로드되었을 때 발생하는 이벤트로 onload event가 대표적
  * 마우스 이벤트(Mouse Event): 사용자가 마우스를 조작했을 때 발생하는 이벤트
  * 키 이벤트(Key Event): 사용자가 키보드를 조작했을 때 발생하는 이벤트

* HTML 태그 속성에 이벤트 핸들러 등록 방법 (예시는 onclick, onchange, onkeydown의 사용을 보여줌)

  * ```
    <h1 onclick = "console.log('clicked');"> HTML 태그 속성에 이벤트 핸들러 추가하기 </h1>
    <input type = "text" onchange = "console.log('changed');" onkeydown = "console.log('typed');">
    ```

* 자바스크립트 코드에서 DOM 엘리먼트 속성에 직접 핸들러 등록 방법 (HTML 태그 속성에 이벤트 핸들러를 등록하는 것이 아님

  * 방법 1: t.onsubmit = function a() ~~ 처럼 메소드에 바로 연결하는 방법 (앞에 정의 된 것이 있으면 덮어 써버림)
  * 방법 2: addEventListener를 이용하여 붙이는 방법 (다른 이벤트 핸들러를 덮어쓰지 않으므로 이벤트 핸들러를 여러 개 추가할 때 쓸 수 있음)
    * removeEventListener로 삭제 가능

* ```
  <form method = "GET" action = "b.html" id = "form1" onsubmit = "console.log('form tag'); return false;">
      이름 : <input type = "text" name = "id"><br>
      메시지 : <input type = "text" name = "msg"><br>
      <input type = "submit">
  </form>
  <script>
      var t = document.getElementById("form1");
      t.onsubmit = function a( ) {
          console.log("from property");
          return false;
      } // 위에 console.log('form tag')이 있음에도 console.log("from property")이 실행됨
      
      function b( ) {
          console.log("from addEventListener");
          return false;
      }
      t.addEventListener("submit", b);
  </script>	
  
  ```

* 예제) 이름과 메세지를 작성한 다음 제출 버튼을 누르면 아이디와 메시지 정보가 GET 메서드를 통해 blhtml로 전달되는 코드

  * Form 태그
    * form 태그는 사용자 입력을 수집하는 데 사용되는 양식을 정의하고, HTML에서 다른 페이지(서버)에 정보를 보낼 때 사용
    * form 태그는 text, checkbox, submit 등과 같은 <input>요소를 포함하고, textarea, select 등과 같은 Form elements들도 포함

  ```
  <html>
      <head>
          <meta charset = "utf-8">
      </head>
      <body>
          <form method = "GET" action = "b.html" id = "form1">
              이름 : <input type = "text" name = "id"><br>
              메시지 : <input type = "text" name = "msg"><br>
              <input type = "submit">		// type이 submit이면 제출 버튼이 생기고, 누르면 해당 form에 name이 있는 input태그들을 action 타겟으로 전달
          </form>
      </body>
  <html>
  ```

------

###Ajax (Asynchronous Javascript and XML)

브라우저에서 페이지를 이동하지 않고 자바스크립트를 통해 HTTP 요청을 보낸 후 그 응답을 받아 처리할 수 있는 기술(비동기로 처리됨)

* 간단한 예제
  * 여기서 req.readyState 값 설명
    * 0: open( ) 메서드가 호출되기 전
    * 1: open( ) 메서드가 호출된 후
    * 2: 보낸 요청에 대해 응답에 헤더가 수신된 후
    * 3: 응답 메시지에 body 부분이 수신 중일 때
    * 4: 모든 응답이 완료되었을 때
  * 참고
    * this(XMLHttpRequest).status 값 설명
      * 200: Okay, 클라이언트의 요청이 올바르게 처리되어 정상으로 응답했을 때
      * 403: Forbidden, 클라이언트의 요청이 권한 문제로 인해 거절되었을 때
      * 404: Not found, 클라이언트가 요청한 자료가 서버에 없을 때
      * 500: Internal Server Error, 기타 이유로 서버에서 오류가 발생해 정상으로 응답할 수 없을 때

```
<html>
    <head>
        <meta charset = "utf-8">
        <script>
            var req = new XMLHttpRequest( );
            req.open("GET", "[원격 데이터 위치]");
            req.onreadystatechange = function a( ) {	// req.readyState의 변화에 따른 핸들러 추가
    					console.log(this.readyState, this.status);
						    if (this.readyState == 4 && this.status == 200) {
					        console.log(this.response);
    						}
            	}
            req.send( );
        </script>
    </head>
    <body>
        AJAX
    </body>
</html>
```

-----

### JSON (Javascript Object Notification)

자바스크립트의 객체를 문자열로 표현하는 방법

#### !!!!주의!!! 값이 undefined인 변수나, 함수를 값으로 가진 변수는 파싱 되지 않음

* 기본 사용법

* ```
  > var pi = 3.14;
  < undefined
  > JSON.stringify(pi);
  < "3.14"
  > JSON.parse("3.14");
  < 3.14
  ```


-----

##번외

* HTML엘리먼트를 자바스크립트가 사용하려면, 1 쓰레드가 도는 자바스크립트 특성상 사용하려는 HTML엘리먼트가 나온 코드 이후에 사용하는 자바스크립트 코드가 나와야함. (document.onload나 최근에는 async 또는 defer속성을 추가하여 문제를 해결할 수도 있음)
* 자바스크립트도 try-catch 쓸수 있음. 대신 Exception은 throw "error" 처럼, 일반적으로 쓰는건 따로 없고 스트링을 날리는 것임



참고 : https://thebook.io/006894/