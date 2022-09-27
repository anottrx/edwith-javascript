# JS 활용, Quiz5

> [부스트코스 자바스크립트의 시작](https://www.boostcourse.org/cs124) 강의를 듣고 정리했습니다.  
> 부스트코스 서포터즈 3기 활동으로 2021년 1월 29일에 다른 블로그에 정리한 글입니다.

## 5. Javascript 활용

### (34) 파일로 쪼개서 정리 정돈하기

> 학습 목표: 파일을 이용해서 코드를 정리할 수 있고, 이렇게 정리하였을 때의 장점을 알 수 있습니다.

JavaScript 파일을 따로 만들고 HTML 파일에 적용하려면 해당 HTML 파일에 다음과 같이 적으면 된다.

```html
<script src="colors.js"></script>
```

`<script>`를 사용하면 코드 수정 및 재활용 등의 유지 보수가 편해진다. 또, 가독성이 좋아지고 코드의 의미가 파일명을 통해서 더 명확해진다.

`<script>`를 사용하면 웹페이지를 로드할 때 웹서버에 접속을 2번(`web.html`과 `colors.js`) 해야 한다. HTML 파일과 JS 파일 모두 다운로드해야 하기 때문이다. 그것이 웹서버 입장에서는 안 좋아 보일 수는 있지만 캐시를 생각하면 좋은 방법임을 알 수 있다. 캐시를 통해 컴퓨터에 저장해서 서버 입장에서는 비용 절감이, 사용자 입장에서는 시간 절약이 되기 때문이다.

`<script>` 코드는 body 태크를 닫기 직전(`</body>`)에 적는 것이 좋다고 한다. HTML 파일은 위에서 아래로 로드되기 때문에 `<head>` 먼저 전체를 로드하고 이후 `<body>`의 전체를 로드한다.

그런데 `<script>`가 `<head>` 안에 있게 되면 HTML이 모두 로드되기도 전에 JS 파일이 먼저 로드가 되고 이 때문에 몇 가지 문제가 발생할 수 있다. 첫째로는 JS 안에 HTML 요소를 변경할 일이 있을 경우, 아직 HMTL이 로드가 안 되었기 때문에 제대로 동작되지 않는다고 여길 수 있다. 둘째로는 JS 파일이 많을 경우 로딩 시간이 길어질 수 있다.

물론 항상 에러가 나는 것은 아니다. 또 jQuery에서 `document ready` 함수를 사용하면 HTML이 로딩 완료된 후에 JS를 실행하도록 할 수도 있다고 한다.

(출처: https://faqs.skillcrush.com/article/176-where-should-js-script-tags-be-linked-in-html-documents)


생각해보기

1) 여러 js 파일을 가져오고 싶다면 어떻게 하면 좋을지 알아봅시다. (힌트: html include multiple js files 라고 검색해보세요!)

 : 
```html
<script src="colors.js"></script>
<script src="fonts.js"></script>
```


### (35) 라이브러리와 프레임워크

> 학습 목표: 라이브러리와 프레임워크에 대해서 이해하고, jQuery 라이브러리를 사용할 수 있습니다.

라이브러리(Library)는 프로그램에 필요한 소프트웨어가 잘 정리되어 있는 것. 쉽게 땡겨쓴다고 생각하면 된다.

프레임워크(Framework)는 만들고자 하는 프로그램(게임, 웹, 해킹 등)에 따라 공통적으로 필요한 부분을 미리 만들어 놓은 것. 사용자는 기획 의도에 따라 조금씩 수정해서 사용하면 된다. 쉽게 프레임워크 안에 들어가서 수정해서 쓰는 거라고 생각하면 된다.

따라서 사용자는 처음부터 끝까지 혼자서 소프트웨어를 개발하지 않고 다른 사람들과 협업한다.

jQuery는 자바스크립트의 라이브러리 중 가장 유명하다. 이 라이브러리를 사용하면 생산성이 더 높아진다.

jQuery는 직접 파일을 다운로드해서 사용할 수도 있지만, CDN(Content Delivery Network)을 사용해서 더 편하게 사용할 수 있다. CDN는 jQuery 파일을 회사 측 서버에 보관하고, 사용자는 `<script src="">`를 통해 쉽게 사용할 수 있는 방법이다. (`<script>` 확인하는 곳: https://developers.google.com/speed/libraries#jquery)

jQuery를 사용하는 방법은 다음과 같다.

`$("a").css("color", color);`
이는 모든 `<a>`의 글씨 색을 color로 바꾸라는 뜻이다. jQuery 없이 사용할 때와는 다르게 반복문 없이 가능하다.

`<input type="button" onclick="funcA(); funcB();">`처럼 `onclick` 안에 여러 함수를 넣을 수 있다.


web.html
```html
<!DOCTYPE html>
<html>
  <head>
    <title>WEB</title>
    <meta charset="utf-8" />
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script src="colors.js"></script>
    <script src="fonts.js"></script>
  </head>
  <body>
    <h1>부스트코스</h1>
    <h1>
      <a href="https://en.wikipedia.org/wiki/Web_(programming_system)">WEB</a>
    </h1>
    <input
      id="night_day"
      type="button"
      value="night"
      onclick="nightDayHandler(this); nightDayHandlerFont(this);"
    />
    <ol>
      <li><a href="https://ko.wikipedia.org/wiki/HTML">HTML</a></li>
      <li><a href="https://en.wikipedia.org/wiki/CSS">CSS</a></li>
      <li><a href="https://en.wikipedia.org/wiki/JavaScript">JavaScript</a></li>
    </ol>
    <h2>JavaScript</h2>
    <p>
      JavaScript (/ˈdʒɑːvəˌskrɪpt/), often abbreviated as JS, is a programming
      language that conforms to the ECMAScript specification. JavaScript is
      high-level, often just-in-time compiled, and multi-paradigm. It has
      curly-bracket syntax, dynamic typing, prototype-based object-orientation,
      and first-class functions.
    </p>
  </body>
</html>

```
colors.js
```js
var Links = {
  setColor: function (color) {
    $("a").css("color", color);
  },
};
var Body = {
  setColor: function (color) {
    $("body").css("color", color);
  },
  setBackgroundColor: function (color) {
    $("body").css("backgroundColor", color);
  },
};
function nightDayHandler(self) {
  if (self.value === "night") {
    Body.setBackgroundColor("black");
    Body.setColor("white");
    self.value = "day";
    Links.setColor("powderblue");
  } else {
    Body.setBackgroundColor("white");
    Body.setColor("black");
    self.value = "night";
    Links.setColor("blue");
  }
}
```
fonts.js
```js
var H1 = {
  setSize: function (size) {
    $("h1").css("font-size", size);
  },
};
function nightDayHandlerFont(self) {
  if (self.value === "night") {
    H1.setSize("xx-small");
  } else {
    H1.setSize("x-large");
  }
}
```

생각해보기

1) jQuery를 직접 자신의 HTML 파일에 추가해보고, 이를 이용해서 모든 h1 태그의 글자 크기를 바꾸는 코드를 작성해 봅시다.

 : 

web.html
```html
<!DOCTYPE html>
<html>
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script src="colors.js"></script>
    <script src="fonts.js"></script>
  </head>
  <body>
    <h1>부스트코스</h1>
    <h1>WEB</h1>
    <input
      id="night_day"
      type="button"
      value="night"
      onclick="nightDayHandler(this); nightDayHandlerFont(this);"
    />
  </body>
</html>
```
fonts.js
```js
var H1 = {
  setSize: function (size) {
    $("h1").css("font-size", size);
  },
};
function nightDayHandlerFont(self) {
  if (self.value === "night") {
    H1.setSize("xx-small");
  } else {
    H1.setSize("x-large");
  }
}
```


### (36) UI vs API

> 학습 목표: UI와 API란 무엇인지 알고, 이 둘 사이의 관계에 대해서 알 수 있습니다.

프로그래밍을 배우기 전에는 UI만 사용했을 것이다. 이제 API를 결합 및 응용해서 응용프로그램을 만들 수 있다.

알림 경고 창인 `alert()`를 사용한 것이 API의 한 예라고 볼 수 있다.

UI(User Interface)는 시각적으로 눈에 보이는 사용자가 사용하는 것을 의미한다.

API(Application Programming Interface)는 애플리케이션 소프트웨어를 구축하고 통합하기 위한 정의 및 프로토콜이다. (출처: https://www.redhat.com/ko/topics/api/what-are-application-programming-interfaces)

UI는 사용자들이 시스템을 제어하기 위해 조작하는 장치고, API는 개발자가 사용하는 조작 장치다.

생각해보기

1) UI와 API는 어떤 관계를 가지고 있을까요?

 : 개발자가 API를 응용해서 만든 소프트웨어를 사용자는 UI를 통해 사용한다. 즉 서로 함께하는 관계다.


### (37) 수업을 마치며

> 학습 목표: 프로젝트를 진행할 때의 원칙과 다양한 검색어에 대해서 알 수 있습니다.

이제는 공부보다는 실습을, 실습보다는 프로젝트를 시작하는 것이 좋다. 프로젝트를 할 때 배운 것을 모두 사용하려는 것보다는 필수적인 것부터 시작하는 것이 좋다. 그러다가 부족해지면 배운 것들을 써먹으면 된다.

그러다가 한계에 부딪히게 되면 그때 다시 공부를 시작하면 된다.

이후 공부할 때 도움이 될 만한 추천하는 검색어는 다음과 같다.

| 키워드 | 설명 | 
|---|---|
| document | 태그 삭제 또는 자식 태그 추가 등. 필요한 메소드가 document 객체 안에 있을 것 |
| DOM(Document Object Model) | document 객체에서도 찾을 수 없을 경우. document는 DOM의 일부 |
| window | 현재 열려있는 웹페이지의 주소, 새창 열기, 웹페이지 화면 크기 등 웹브라우저 자체를 제어 |
| ajax | 웹페이지를 새로 고침하지 않고도 정보를 변경<br />ajax는 현대적인 웹앱을 만드는데 필수적인 기술 |
| cookie | 웹페이지를 새로 고침하고도 현재 상태를 유지<br />cookie를 사용하면 사용자를 위한 개인화된 서비스 제공 가능 |
| offline web application | 인터넷이 끊겨도 동작하는 웹페이지 |
| webRTC | 화상 통신 웹 앱 |
| speech | 음성 인식 및 처리 |
| webGL | 3차원 그래픽 등의 웹 게임 |
| webVR | 가상현실 |

생각해보기

1) 이제 여러분들이 강의를 통해서 배운 내용을 가지고 HTML+Javascript+CSS를 활용한 새로운 프로젝트를 진행하게 될 겁니다. 어떤 웹 서비스를 만들고 싶으신가요?

 : 다양한 기능을 가진 ToDoList를 우선 만들고 싶다.

​