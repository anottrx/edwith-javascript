# 배열과 반복문, Quiz2

> [부스트코스 자바스크립트의 시작](https://www.boostcourse.org/cs124) 강의를 듣고 정리했습니다.  
> 부스트코스 서포터즈 3기 활동으로 2021년 1월 18일에 다른 블로그에 정리한 글입니다.

<br />

### (19) 반복문 예고

> 학습 목표: 반복문이란 무엇인지 이해할 수 있습니다.

자바스크립트의 반복문의 예시로는 for문, do...while문, while문, continue;, break; 등이 있다. ([출처](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Loops_and_iteration))

<br />

**생각해보기**
1) 반복문을 사용했을 때 편리한 상황을 한 가지 생각해보세요.
 : 로그인을 5회 실패할 경우 일정 시간 동안 계정 잠김 처리를 할 수 있다.

<br />

### (20) 배열

> 학습 목표: 배열의 개념과 기본적인 문법을 이해할 수 있습니다.

배열(Array), 문자열(String)

`push()`는 배열 마지막에 요소를 넣고, `pop()`은 배열 마지막 요소를 빼내는 것이다. `unshift()`는 배열 맨 앞에 요소를 넣는다.

`splice()`를 통해 배열 안의 요소를 제거할 수 있다. `splice(m, n`은 `m`번째 요소부터 총 `n`개의 요소를 제거하는 것이다. ([출처](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array))

```html
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <h1>Array</h1>
    <h2>Syntax</h2>
    <script>
      var coworkers = ["egoing", "leezxhe"];
    </script>
    <h2>get</h2>
    <script>
      // 배열의 n번째 요소 구하기
      document.write(coworkers[0], "<br>"); // egoing
      document.write(coworkers[1]); // leezxhe
    </script>
    <h2>add</h2>
    <script>
      // push 안의 요소를 배열 마지막에 넣는 것
      coworkers.push("duru");
      coworkers.push("taeho");
    </script>
    <h2>count</h2>
    <script>
      // 배열 안의 요소 개수 구하기, 문자열 길이 구하는 방법과 동일
      document.write(coworkers.length); // 4
    </script>
    <hr />
    <script>
      var animals = ["ant", "bee"];
      animals.push("camel");
      document.write(animals[1]); // bee

      // animals 배열 안의 ant 요소부터 1개 지우기
      animals.splice(animals["ant"], 1);
      document.write("<br>", animals); // bee, camel
    </script>
  </body>
</html>

```

<br />

**생각해보기**
1) 다음과 같은 코드를 실행했을 때 화면에 어떻게 출력될지 생각해보세요.
```js
var animals = ["ant", "bee"];
animals.push("camel");
document.write(animals[1]);
```
 : bee

2)  배열에서 어떤 값을 삭제하기 위해서는 어떤 코드를 사용하면 될까요? (힌트: Javascript array remove value라고 검색해보세요!)
 : `animals.splice(animals["ant"], 1);`

<br />

### (21) 반복문

> 학습 목표: while 반복문의 작동 방식을 이해하고 적절히 사용할 수 있습니다.

`while(조건) {}`에서 조건이 true일 때 실행되고 false가 되면 중단된다. 이때 반복문 안의 코드는 끝까지 진행된다.

<img src="https://user-images.githubusercontent.com/59449215/193826383-6b23ffdd-74d9-48cf-b56a-cb1507c61954.png" width=300/>

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Loop</h1>
    <ul>
      <script>
        document.write("<li>1</li>");
        var i = 0;
        while (i < 3) {
          document.write("<li>2</li>");
          document.write("<li>3</li>");
          i = i + 1;
        }
        document.write("<li>4</li>");
      </script>
      <hr />
      <script>
        var j = 0;
        while (j < 3) {
          j = j + 2;
        }
        document.write(j);
      </script>
    </ul>
  </body>
</html>
```

<br />

**생각해보기**
1) 다음 코드의 실행 결과는 무엇일까요?
```js
var i = 0;
while (i < 3) {
  i = i + 2;
}
document.write(i);
```
 : 4

<br />

### (22) 배열과 반복문

> 학습 목표: 반복문과 배열을 함께 사용한 프로그램을 만들 수 있습니다.

`document.write()`는 줄바꿈이 되지 않는다.

`<ol>`은 ordered list, `<ul>`은 unordered list, `<li>`는 list라고 볼 수 있다.

VSCode에서 `li*3`라고 입력하면 `<li></li>`가 3개 출력된다.

<img src="https://user-images.githubusercontent.com/59449215/193826417-5bce20dd-2247-4f6d-af1f-887ce7477131.png" width=300/>

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Loop & Arrays</h1>
    <script>
      var coworkers = ["egoing", "leezche", "duru", "taeho"];
    </script>
    <h2>Coworkers</h2>
    <ul>
      <script>
        var i = 0;
        while (i < coworkers.length) {
          document.write("<li>" + coworkers[i]);
          document.write(": http://alink.com/" + coworkers[i] + "</li>");
          i = i + 1;
        }
      </script>
    </ul>
    <hr />
    <script>
      fruits = ["apple", "banana", "coconut"];
      var i = 0;
      while (i < fruits.length) {
        document.write(i + 1 + ". " + fruits[i] + "<br>");
        i = i + 1;
      }
    </script>
  </body>
</html>
```

<br />

**생각해보기**
1) 반복문과 배열을 적절히 활용해서 fruits 배열을 다음과 같이 숫자와 함께 출력하려면 어떻게 해야할지 생각해보세요.
```
1. apple
2. banana
3. coconut
```
 : 
```html
<script>
  fruits = ["apple", "banana", "coconut"];
  var i = 0;
  while (i < fruits.length) {
    document.write(i + 1 + ". " + fruits[i] + "<br>");
    i = i + 1;
  }
</script>
```
​
<br />

### (23) 배열과 반복문의 활용

> 학습 목표: 배열과 반복문을 활용해서 웹사이트의 특정 태그 스타일을 바꿀 수 있습니다.

검색을 많이 하자.

`shift+enter`: 개발자 도구 내 Console 창에서 줄바꿈만 하기

`querySelector()`는 첫 번째 해당 요소만 출력하지만, `querySelectorAll()`는 해당되는 모든 요소를 출력한다. 

`var alist = document.querySelectorAll('a');`는 `<a>`에 해당되는 모든 요소를 alist에 넣어준다.

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826434-4f4f733f-8ead-486e-bbd6-9c496d051cae.png" /></td>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826443-ed9fabd7-3995-43f3-bc99-21373b331aee.png" /></td>
  </tr>
</table>

```html
<!DOCTYPE html>
<html>
  <head>
    <title>WEB</title>
    <meta charset="utf-8" />
  </head>
  <body>
    <h1>
      <a href="https://en.wikipedia.org/wiki/Web_(programming_system)">WEB</a>
    </h1>
    <input
      type="button"
      value="night"
      onclick="
            var target = document.querySelector('body');
            if(this.value === 'night') {
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                this.value = 'day';

                var alist = document.querySelectorAll('a');
                var i = 1;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    i = i + 1;
                }
            }
            else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                this.value = 'night';

                var alist = document.querySelectorAll('a');
                var i = 1;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    i = i + 1;
                }
            }
        "
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
1) 이번 강의에서 배운 코드를 약간 수정해서 첫 번째 하이퍼링크를 제외한 나머지 세 개의 하이퍼링크만 색깔이 바뀌도록 만들어보세요.
: 
```js
var alist = document.querySelectorAll("a");
var i = 1;

while (i < alist.length) {
  alist[i].style.color = "powderblue";
  i = i + 1;
}
```

​<br />

## Quiz2

<img src="https://user-images.githubusercontent.com/59449215/193826468-9cdc00eb-38ae-4e62-ab39-8fc4d93b2212.png" width=500/>

​<br />
<br />
