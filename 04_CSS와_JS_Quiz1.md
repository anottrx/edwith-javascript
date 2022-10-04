# CSS와 JS, Quiz1

> [부스트코스 자바스크립트의 시작](https://www.boostcourse.org/cs124) 강의를 듣고 정리했습니다.  
> 부스트코스 서포터즈 3기 활동으로 2021년 1월 16일에 다른 블로그에 정리한 글입니다.

<br />

### (9) CSS기초(style 속성)

> 학습 목표: CSS의 기본 문법을 이해할 수 있다.

style(HTML 문법) 속성 안에는 CSS를 입력한다. `color:red;`는 CSS의 속성(property)이라고 한다.

`color`는 글씨 색을, `background-color`는 글씨 배경색을 바꾼다. `background-color`는 `transparent`가 `default`다.

<img src="https://user-images.githubusercontent.com/59449215/193826061-5c4e0826-204f-42dc-bc6c-2e585b9d2f36.png" width=300/>

```html
<!DOCTYPE html>
<html>
    <head>
        <title>WEB</title>
    </head>
    <body>
        <h1>WEB</h1>
        <h2 style="background-color:coral; color:powderblue;">JavaScript</h2>
        <p style="background-color:green; color:white;">Hello World</p>
        <p>   
            <span style="font-size:large;">자바스크립트 상세 설명</span>
            <br>
            JavaScript (/ˈdʒɑːvəˌskrɪpt/), often abbreviated as JS, is a programming 
            language that conforms to the ECMAScript specification. JavaScript is 
            high-level, often just-in-time compiled, and multi-paradigm. It has 
            curly-bracket syntax, dynamic typing, prototype-based object-orientation, 
            and first-class functions.
        </p>
    </body>
</html>
```

참고자료
- [CSS background-color Property](https://www.w3schools.com/cssref/pr_background-color.asp)
​
<br />

**생각해보기**
1) 강의에서 배운 color와 background-color을 이용해서 배경이 초록색이고 글자가 흰색인 문단을 만들어 봅시다.
 : `<p style="background-color:green; color:white;">Hello World</p>`

2) CSS를 이용해서 글자 크기를 키워봅시다. (힌트 : CSS property font size 라고 검색해 보세요!)
 : `<span style="font-size:large;">자바스크립트</span>`

<br />

### (10) CSS기초(style 태그)

> 학습 목표: Div, span 태그와 class를 사용해서 CSS 디자인을 부분적으로 적용해볼 수 있습니다.

VSCode에서 커서 여러 개 만들기: option 버튼 누른 상태에서 원하는 곳을 마우스로 클릭

`<div>`는 줄바꿈이 되고 `<span>`은 줄바꿈이 되지 않는다.

`<style>`을  `<head>`안에 넣어서 `<body>`안의 여러 태그들을 한 번에 관리할 수 있는데, 이때 class를 사용한다.

<img src="https://user-images.githubusercontent.com/59449215/193826074-b9783713-f1f5-4c51-8bdb-8b89c40dddc7.png" width=500/>

([출처](https://en.wikipedia.org/wiki/HTML_element))

```html
<head>
    <style>
        .js {
            /* 클래스명이 js인 태그 안의 Content의 CSS 적용 */
            font-weight:bold;
        }
    </style>
</head>
<body>
    <span class="js">Hi</span>
</body>
```

<img src="https://user-images.githubusercontent.com/59449215/193826092-a1583ce5-016a-4f18-ab3a-ac220cefa7e6.png" width=300/>

```html
<!DOCTYPE html>
<html>
    <head>
        <title>WEB</title>
        <style>
            .js{
                font-size:x-large;
                font-weight:bold;
                font-style:italic;
                font-family: "Times New Roman";
                color:blueviolet;
            }
        </style>
    </head>
    <body>
        <h1>WEB</h1>
        <h2 style="background-color:coral; color:powderblue;">JavaScript</h2>
        <p>   
            span을 사용 <br>
            <span class="js">JavaScript</span> (/ˈdʒɑːvəˌskrɪpt/), often abbreviated 
            as JS, is a programming language that conforms to the ECMAScript 
            specification. <span class="js">JavaScript</span> is high-level, often 
            just-in-time compiled, and multi-paradigm. It has curly-bracket syntax, 
            dynamic typing, prototype-based object-orientation, and first-class 
            functions.
        </p>
        <p>   
            div를 사용
            <div class="js">JavaScript</div> (/ˈdʒɑːvəˌskrɪpt/), often abbreviated 
            as JS, is a programming language that conforms to the ECMAScript 
            specification. <div class="js">JavaScript</div> is high-level, often 
            just-in-time compiled, and multi-paradigm. It has curly-bracket syntax, 
            dynamic typing, prototype-based object-orientation, and first-class 
            functions.
        </p>
    </body>
</html>
```

<br />

**생각해보기**
1) js class에 다양한 스타일을 추가해서 Javascript라는 글자를 꾸며봅시다.
 : 
```css
.js{
  font-size:x-large;
  font-weight:bold;
  font-style:italic;
  font-family: "Times New Roman";
  color:blueviolet;
}
```

<br />

### (11) CSS기초(선택자)

> 학습 목표: id 선택자에 대해서 이해하고, 선택자들 사이의 우선순위를 이해할 수 있습니다.

class는 여러 개를 grouping하기 때문에 포괄적이다. 반면 id는 한 가지를 식별하기 때문에 유일해야 하고 예외적이다.

우선순위는 id 선택자 > class 선택자 > 태그 선택자 순서다.

```html
<head>
    <style>
        .js{
            /* class 선택자 */
            font-weight: bold;
            font-style: italic;
            color: red;
        }
        #first{
            /* id 선택자 */
            color: green;
        }
        span{
            /* 태그 */
            color: blue;
        }
    </style>
</head>
<body>
    <span>Hello <span class="js">World<span id="first">!</span></span></span>
<body>
```

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826120-4d395ffd-8f2b-4dec-a5f4-d62ee5e3703a.png" /></td>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826134-394b982d-125d-42f9-88b3-8ce052e274b8.png" /></td>
  </tr>
</table>

```html
<!DOCTYPE html>
<html>
    <head>
        <title>WEB</title>
        <style>
            .js{
                font-weight: bold;
                font-style: italic;
                color: red;
            }
            #first{
                color: green;
            }
            span{
                color: blue;
            }
            .hello{
                font-size: 12px;
                color: red;
            }
            #bye{
                font-size: 13px;
            }
        </style>
    </head>
    <body>
        <h1>WEB</h1>
        <span id="bye" class="hello">Javascript</span>
        <p>
            <span id="first" class="js">JavaScript</span> (/ˈdʒɑːvəˌskrɪpt/), 
            often abbreviated as JS, is a programming language that conforms 
            to the ECMAScript specification. <span class="js">JavaScript</span> 
            is high-level, often just-in-time compiled, and multi-paradigm. 
            It has curly-bracket syntax, dynamic typing, prototype-based 
            object-orientation, and first-class functions. Alongside 
            <span>HTML</span> and <span>CSS</span>, JavaScript is one of 
            the core technologies of the World Wide Web. JavaScript enables 
            interactive web pages and is an essential part of web applications. 
        </p>
    </body>
</html>
```

<br />

**생각해보기**
1) 다음과 같은 코드가 있을 때, Javascript라는 글자에는 어떤 색깔이 나타날까요? 글자의 크기는 얼마가 될까요?
```html
<style>
  span {
    color: blue;
  }
  .hello {
    font-size: 12px;
    color: red;
  }
  #bye {
    font-size: 13px;
  }
</style>
```
```html
<span id="bye" class="hello">Javascript</span>
```

<br />

### (12) 제어할 태그 선택하기

> 학습 목표: Javascript 코드를 통해서 제어할 태그를 선택하는 방법에 대해서 이해합니다.

`querySelector`를 사용해서 사용자가 원하는 선택자를 제어할 수 있다. 위와 같은 방법으로 단순한 태그는 `body`처럼, `class`는 `.name`으로, `id`는 `#name`으로 입력한다.

HTML 태그 안에서는 `background-color`였다면, 자바스크립트에서는 `backgroundColor`를 사용한다는 차이점이 있다.

`getElementById()`는 id가 있을 경우 사용하고 그렇지 않을 경우는 주로 `querySelector`를 사용한다. ([출처](https://developer.mozilla.org/ko/docs/Web/API/Document/getElementById))

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826152-01215124-f9fc-477e-905b-1a5708b97fca.png" /></td>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826167-fbdec240-c84a-409d-ba5f-1345f7e8bde5.png" /></td>
    <td><img src="https://user-images.githubusercontent.com/59449215/193826176-f85382af-4eb1-4b28-84a1-b07fd3f0f084.png" /></td>
  </tr>
  <tr>
    <td>마우스 커서를 night 버튼 위에 올린 후</td>
    <td>night 버튼을 누른 후</td>
    <td>day 버튼을 누른 후(id 선택자로 바꾼 CSS는 취소되지 않는다)
</td>
  </tr>
</table>

```html
<!DOCTYPE html>
<html>
    <head>
        <title>WEB</title>
        <meta charset="utf-8">
    </head>
    <body>
        <h1>WEB</h1>
        <input type="button" value="night" onclick="
            document.querySelector('body').style.backgroundColor='black';
            document.querySelector('body').style.color='white';
            document.querySelector('#list').style.color='red';" 
            onmouseover="document.querySelector('body').style.backgroundColor='gray';">
        <input type="button" value="day" onclick="
            document.querySelector('body').style.backgroundColor='white';
            document.querySelector('body').style.color='black';
            document.querySelector('.title').style.color='green';">
        <ol id="list">
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ol>
        <h2 class="title">JavaScript</h2>
        <p>
            JavaScript (/ˈdʒɑːvəˌskrɪpt/), often abbreviated as JS, 
            is a programming language that conforms to the ECMAScript 
            specification. JavaScript is high-level, often just-in-time 
            compiled, and multi-paradigm. It has curly-bracket syntax, 
            dynamic typing, prototype-based object-orientation, and 
            first-class functions.
        </p>
    </body>
</html>
```

참고자료
- [Document.querySelector()](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector)

<br />

**생각해보기**
1) night 버튼 위에 마우스를 올렸을 때, 배경 색이 회색으로 바뀌도록 만들어봅시다.
: 
```html
<input type="button" value="night" onmouseover="document.querySelector('body').style.backgroundColor='gray';">
```

<br />

### Quiz1

<img src="https://user-images.githubusercontent.com/59449215/193826192-1fe7fcf1-12d1-45c1-8eaf-ffb266a93c0a.png" width=500/>

<br />
<br />
