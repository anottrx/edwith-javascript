# JS 객체, Quiz4

> [부스트코스 자바스크립트의 시작](https://www.boostcourse.org/cs124) 강의를 듣고 정리했습니다.  
> 부스트코스 서포터즈 3기 활동으로 2021년 1월 28일에 다른 블로그에 정리한 글입니다.

<br />

## 4. Javascript 객체

### (29) 객체 예고

> 학습 목표: 객체에 대한 개념과 필요성을 이해할 수 있습니다.

코드가 길어지면 함수로 정리한다. 그리고 함수가 많아지면 그 함수와 연관된 변수도 많아지면서 복잡해진다. 이렇게 연관된 함수와 변수들을 같은 이름으로 그룹핑해서 정리하는 것을 객체라고 한다.

객체는 함수의 기반 위에서 존재한다고 볼 수 있다.
​
`document.querySelector()`에서 document는 객체고, `querySelector()`는 document 객체에 속해 있는 함수다. 그리고 이렇게 객체에 속해 있는 함수들을 메소드(Method)라고 한다.

서로 다른 객체에 속해 있는 메소드들의 이름은 겹쳐도 된다.

<br />

**생각해보기**

1) 다음 코드에서 객체와 메소드를 찾아보세요.

```js
var fruits = ["apple", "banana"];
fruits.push("coconut");
```
 :  fruits가 객체고, `push()`가 메소드다.
​
<br />

### (30) 객체(쓰기와 읽기)

> 학습 목표: 객체의 기본 문법을 이해하고, 객체를 쓰고 읽을 수 있습니다.

객체는 이름이 있는 정리 정돈 상자라고 비유할 수 있다. 객체는 순서가 없다. 

객체(Object)는 `{}`로 표현한다.

객체에 요소를 추가하는 방법은 우선 2가지가 있다.

```js
// 방법 1) 
obj.programmer = "egoing"

// 방법 2) 
obj["programmer"] = "egoing" 
// (이 방법을 사용하면 key 값에 띄어쓰기 포함되게 사용할 수 있다.)
```

객체(obj)의 어떤 키값(programmer)에 해당되는 요소를 출력하려면 `obj.programmer`라고 쓰면 된다.

객체에 있는 모든 내용을 화면에 출력할 때 `JSON.stringify(obj)`를 사용한다.

콘솔에서 출력할 때는 `obj`만 입력해도 가능하다.

`Object.keys(obj)`는 객체 안의 모든 키값을,
`Object.values(obj)`는 객체 안의 모든 속성의 값들을,
`Object.entries(obj)`는 객체 안의 모든 `[key, value]` 값들을 배열로 반환한다.([출처](https://ko.javascript.info/keys-values-entries))

<img src="https://user-images.githubusercontent.com/59449215/193826665-39f91dbe-b004-455a-8a1a-4cf4a1f7b940.png" />

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Object</h1>
    <h2>Create</h2>
    <script>
      var coworkers = {
        // 객체 생성
        programmer: "egoing",
        designer: "leezche",
      };
      document.write("programmer : " + coworkers.programmer + "<br> ");
      document.write("designer: " + coworkers.designer + "<br>");
      coworkers.bookeeper = "duru"; // 객체에 요소 추가
      document.write("bookeeper :  " + coworkers.bookeeper + "<br>");
      coworkers["data scientist"] = "taeho"; // 객체에 요소 추가
      document.write(
        "data scientist : " + coworkers["data scientist"] + "<br>"
      );
    </script>
    <hr />
    <script>
      var countries = {};
      countries.asia = "korea";
      countries["europe"] = "england";
      console.log(countries);
      document.write(JSON.stringify(countries) + "<br>");
      document.write(Object.keys(countries) + "<br>");
      document.write(Object.values(countries) + "<br>");
      document.write(Object.entries(countries) + "<br>");
    </script>
  </body>
</html>
```

<br />

**생각해보기**
1) countries라는 이름의 빈 객체를 만들고, asia라는 이름을 가진 korea라는 값과, europe이라는 이름을 가진 england라는 값을 추가해봅시다.
 : 
```js 
var countries = {};
countries.asia = "korea";
countries["europe"] = "england";
```
<br />

### (31) 객체(순회)

> 학습 목표: for in을 사용해서 객체의 모든 요소에 접근하는 코드를 만들 수 있습니다.

iteration은 반복을 뜻한다. for문 같은 반복문을 사용하는 것을 iterate(순회)라고 표현할 수 있다.

객체에서는 `for...in`을 사용하여 객체 안의 모든 요소들을 출력할 수 있다. 다음 예시와 같은 방법으로 key와 value 모두를 출력할 수 있다.

```js
for(var key in obj) {
    document.write(key + obj[key];
}
```
객체는 순서가 없기 때문에 출력되는 순서가 정해져 있지 않다.

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Object</h1>
    <h2>Create</h2>
    <script>
      var coworkers = {
        // 객체 생성
        programmer: "egoing",
        designer: "leezche",
      };
      document.write("programmer : " + coworkers.programmer + "<br> ");
      document.write("designer: " + coworkers.designer + "<br>");
      coworkers.bookeeper = "duru"; // 객체에 요소 추가
      document.write("bookeeper :  " + coworkers.bookeeper + "<br>");
      coworkers["data scientist"] = "taeho"; // 객체에 요소 추가
      document.write(
        "data scientist : " + coworkers["data scientist"] + "<br>"
      );
    </script>
    <h2>Iterate</h2>
    <script>
      for (var key in coworkers) {
        document.write(key + " : " + coworkers[key] + "<br>");
      }
    </script>
    <hr />
    <script>
      var countries = {};
      countries.asia = "korea";
      countries["europe"] = "england";
      for (var key in countries) {
        document.write(key + " : " + countries[key] + "<br>");
      }
    </script>
  </body>
</html>
```

<br />

**생각해보기**
1) 지난 강의의 <생각해보기>에서 만들었던 countries라는 객체에서, 모든 객체의 이름과 값을 한 줄씩 출력하는 코드를 만들어 봅시다.
 : 
```js 
for (var key in countries) {
  document.write(key + " : " + countries[key] + "<br>");
}
```
<br />

### (32) 객체(프로퍼티와 메소드)

> 학습 목표: 객체의 메소드와 프로퍼티를 이해할 수 있습니다.

객체에는 배열, 숫자, 문자열, 함수를 담을 수 있다. 객체에 소속된 함수를 메소드(Method)라고 한다.

`obj.showAll = function() {}`은 obj라는 객체에 `showAll()`이란 메소드를 추가한 것이다. 이는 `function showAll()`과 유사하다. 그리고 그렇게 추가된 `showAll()`도 obj에 소속된 요소가 된다.

메소드 내에서의 this는 해당 메소드가 쓰인 객체를 가리킨다.

객체에 해당하는 변수들은 프로퍼티(Property)라고 한다. `obj.programmer`에서 programmer가 그 예시이다.

<img src="https://user-images.githubusercontent.com/59449215/193826734-d6571f1a-e579-4c09-886a-0e5979db97b5.png" width=300/>

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Object</h1>
    <h2>Create</h2>
    <script>
      var coworkers = {
        programmer: "egoing",
        designer: "leezche",
      };
      document.write("programmer : " + coworkers.programmer + "<br> ");
      document.write("designer: " + coworkers.designer + "<br>");
      coworkers.bookeeper = "duru";
      document.write("bookeeper :  " + coworkers.bookeeper + "<br>");
      coworkers["data scientist"] = "taeho";
      document.write(
        "data scientist : " + coworkers["data scientist"] + "<br>"
      );
    </script>
    <h2>Property & Method</h2>
    <script>
      coworkers.showAll = function () {
        for (var key in this) {
          if (key !== "showAll") {
            document.write(key + " : " + this[key] + "<br>");
          }
        }
      };
      coworkers.showAll();
    </script>
    <hr />
    <script>
      coworkers.printProgrammer = function () {
        for (var key in this) {
          if (key === "programmer") {
            document.write(key + " : " + this[key] + "<br>");
          }
        }
      };
      coworkers.printProgrammer();
    </script>
  </body>
</html>
```

<br />

**생각해보기**
1) 조건문을 사용해서 key가 programmer일 때만 출력하는 메소드 printProgrammer()을 만들어 봅시다.
 : 
```js
coworkers.printProgrammer = function () {
  for (var key in this) {
    if (key === "programmer") {
      document.write(key + " : " + this[key] + "<br>");
    }
  }
};
```

<br />

### (33) 객체의 활용

> 학습 목표: 객체를 적절하게 활용할 수 있습니다.

객체를 활용해서 메소드를 만드는 방법이 우선 2가지가 있다.

```js
// 방법 1)
obj.showAll = function () {};
showAll();

// 방법 2)
var obj = {
  showAll: function () {},
};
```

객체 내에서 프로퍼티와 프로퍼티 사이는 `,`로 구분한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>WEB</title>
    <meta charset="utf-8" />
    <script>
      var Links = {
        setColor: function (color) {
          var alist = document.querySelectorAll("a");
          var i = 0;
          while (i < alist.length) {
            alist[i].style.color = color;
            i = i + 1;
          }
        },
      };
      var Body = {
        setColor: function (color) {
          document.querySelector("body").style.color = color;
        },
        setBackgroundColor: function (color) {
          document.querySelector("body").style.backgroundColor = color;
        },
      };
      function nightDayHandler(self) {
        var target = document.querySelector("body");
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

<br />

**생각해보기**

1) 이번 강의에서 수정한 코드가 이전의 코드에 비해서 더 좋아진 점은 무엇일까요?

 : 객체마다 서로 연관된 메소드들을 정리해놓아 보기 깔끔해졌다. 서로 다른 객체 내의 메소드 이름은 중복되어도 되기 때문에 이름이 간단해졌다. 

<br />

### Quiz4

<img src="https://user-images.githubusercontent.com/59449215/193826756-ae6e25be-519c-4374-8f55-282912b35760.png" width=500/>

<br />
<br />
