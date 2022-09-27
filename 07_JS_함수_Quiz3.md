# JS 함수, Quiz3

> [부스트코스 자바스크립트의 시작](https://www.boostcourse.org/cs124) 강의를 듣고 정리했습니다.  
> 부스트코스 서포터즈 3기 활동으로 2021년 1월 23일에 다른 블로그에 정리한 글입니다.

## 3. Javascript 함수

### (24) 함수 예고

> 학습 목표: 함수란 무엇인지 이해하고, 함수를 사용할 때의 장점을 알 수 있습니다.

함수를 사용하면 코드의 유지보수가 쉬워진다는 장점이 있다. 또, 코드의 길이를 줄여서 인터넷을 통해 전송할 때 비용을 절감할 수 있다. 함수의 이름을 보고 어떤 역할을 하는지 예상할 수 있다.  

자바스크립트 함수는 `function nightDayHandler() {}`처럼 적는다.

생각해보기

1) 함수를 사용했을 때 편리한 상황을 한 가지 생각해보세요.

 : 반복되는 작업이 있는 경우, 함수를 사용하면 코드 길이가 줄어들어 이해하기가 쉬워진다.
​

### (25) 함수

> 학습 목표: 반복문으로 처리할 수 없는 상황에서 함수가 유용하게 쓰이는 예시를 알아보고, 함수의 기본 문법을 이해할 수 있습니다.

함수는 function인데, 이후 객체를 배우면 method라고 부르는 경우도 있다.

https://stackoverflow.com/questions/15285293/method-vs-functions-and-other-questions

https://dev.to/tiffany/what-is-the-difference-between-a-function-and-a-method-in-javascript-3mkj

반복문을 쓰기 어려운 상황일 때 함수를 사용하면 좋다.

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Function</h1>
    <h2>Basic</h2>
    <ul>
      <script>
        function two() {
          document.write("<li>2-1</li>");
          document.write("<li>2-2</li>");
        }
        document.write("<li>1</li>");
        two();
        document.write("<li>3</li>");
        two();
      </script>
    </ul>
  </body>
</html>

```

생각해보기

1) 중복된 코드가 여러 번 나타날 때, 반복문으로는 처리할 수 없지만, 함수로는 처리할 상황을 생각해 봅시다.

 : 계산기로 사용자가 덧셈을 반복할 때

​
### (26) 함수-매개변수와 인자

> 학습 목표: 매개변수와 인자를 이용한 함수를 구현할 수 있습니다.

함수는 입력(매개변수, 인자)과 출력(Return)으로 이루어져 있다.

`function sum(left, right){}`에서 left, right이 매개변수(Parameter)다.

`sum(2, 3)`에서 2, 3이 인자(Argument)다.

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Function</h1>
    <h2>Basic</h2>
    <h2>Parameter & Argument</h2>
    <script>
      function onePlusOne() {
        document.write(1 + 1 + "<br>");
      }
      onePlusOne();
      function sum(left, right) {
        // left, right가 매개변수 parameter
        document.write(left + right + "<br>");
      }
      sum(2, 3); // 2, 3이 인자 argument
      sum(3, 4);
    </script>
    <hr />
    <script>
      function hello(i, j, k) {
        document.write(i + j - k);
      }
      hello(2, 3, 1); // 2+3-1 = 4
    </script>
  </body>
</html>

```

생각해보기

1) 다음 코드의 실행 결과는 무엇일까요?

```js
function hello(i, j, k) {
  document.write(i + j - k);
}
hello(2, 3, 1);
```
 : 4


### (27) 함수-리턴

> 학습 목표: 리턴을 이용해서 함수의 출력을 구현해봅시다.

`1+1=2`에서 `1+1`은 `2`에 대한 표현식(Expression)이라고 볼 수 있다.

리턴(Return)은 함수의 결과를 단순히 출력하는 것이 아니라 값을 돌려준다.

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Function</h1>
    <h2>Basic</h2>
    <h2>Parameter & Argument</h2>
    <script>
      function onePlusOne() {
        document.write(1 + 1 + "<br>");
      }
      onePlusOne();
      function sum(left, right) {
        document.write(left + right + "<br>");
      }
      function sumColorRed(left, right) {
        document.write(
          '<div style="color:red;">' + left + right + "</div><br>"
        );
      }
      sum(2, 3);
      sumColorRed(2, 3); // 5
      sum(3, 4);
    </script>
    <h2>Return</h2>
    <script>
      function sum2(left, right) {
        return left + right;
      }
      document.write(sum2(2, 3) + "<br>");
      document.write('<div style="color:red;">' + sum2(2, 3) + "</div>");
      document.write('<div style="font-size:3rem;">' + sum2(2, 3) + "</div>");
    </script>
  </body>
</html>

```

생각해보기

1) 리턴을 사용했을 때의 이점이 무엇인지 생각해 보세요.

 : 불필요하게 변수를 할당할 필요가 없다.
​

### (28) 함수 활용

> 학습 목표: 함수의 입출력을 활용한 프로그램을 구현할 수 있습니다.

함수는 리팩토링에서 중요한 역할을 한다.

`onclick` 내에서는 `this`가 해당 버튼 등의 `element`를 의미하지만, 독립된 `function`에서의 `this`는 전역 객체로 웹브라우저에서 윈도우 전체를 의미한다. 따라서 이때는 `this` 대신 새로운 매개변수를 사용한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>WEB</title>
    <meta charset="utf-8" />
    <script>
      function nightDayHandler(self) {
        var target = document.querySelector("body");
        if (self.value === "night") {
          target.style.backgroundColor = "black";
          target.style.color = "white";
          self.value = "day";

          var alist = document.querySelectorAll("a");
          var i = 1;
          while (i < alist.length) {
            alist[i].style.color = "powderblue";
            i = i + 1;
          }
        } else {
          target.style.backgroundColor = "white";
          target.style.color = "black";
          self.value = "night";

          var alist = document.querySelectorAll("a");
          var i = 1;
          while (i < alist.length) {
            alist[i].style.color = "blue";
            i = i + 1;
          }
        }
      }
    </script>
  </head>
  <body>
    <h1>
      <a href="https://en.wikipedia.org/wiki/Web_(programming_system)">WEB</a>
    </h1>
    <input
      id="night_day"
      type="button"
      value="night"
      onclick="nightDayHandler(this);"
    />
    <input
      id="night_day"
      type="button"
      value="night"
      onclick="nightDayHandler(this);"
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

생각해보기

1) 오늘 배운 것처럼 함수를 활용하는 코드로 바꾸었을 때에 원래와 비교해서 어떤 장점이 있을까요?

 : 코드 길이가 줄어들고, 두 버튼이 모두 같은 일을 하는 것을 바로 알 수 있다.

