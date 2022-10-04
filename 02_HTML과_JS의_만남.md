# HTML과 JS의 만남

> [부스트코스 자바스크립트의 시작](https://www.boostcourse.org/cs124) 강의를 듣고 정리했습니다.  
> 부스트코스 서포터즈 3기 활동으로 2021년 1월 12일에 다른 블로그에 정리한 글입니다.

<br />

## 1. 웹과 Javascript

### (3) HTML과 JS의 만남: script 태그

> 학습 목표: HTML에서 Javascript 코드를 사용하기 위해서 script 태그를 사용할 수 있습니다.

웹브라우저는 `<script>` 안쪽의 코드를 자바스크립트로 인식한다.
`document.write()`는 글씨를 출력할 때 사용한다.

<img src="https://user-images.githubusercontent.com/59449215/193825607-4b681b88-fa48-4bd9-a4a0-8d1a9f05d3fc.png" width=300/>

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>WEB example</title>
    </head>
    <body>
        <h1>JavaScript</h1>
        <script>
            document.write('<p>hello world</p>');
            document.write(1+1);
        </script>
        <h1>html</h1>
        1+1
    </body>
</html>
```

<br />

**생각해보기**
1) 어떤 경우에 HTML 코드를 사용하고, 어떤 경우에 Javascript 코드를 사용하면 좋을까요?
 : HTML 코드는 정적으로 정보를 표현할 때, Javascript 코드는 동적으로 웹브라우저를 바꾸는 등 사용자와 상호작용을 하기 위해 사용하면 좋다.

<br />

### (4) HTML과 JS의 만남: 이벤트

> 학습 목표: Javascript 이벤트란 무엇이고, 어떻게 사용할 수 있는지 이해합니다.

웹브라우저 위에서 일어나는 사건을 이벤트(Event)라고 하고, 그 이벤트를 이용해서 사용자와 상호작용하는 웹사이트를 만들 수 있다.
`onclick`의 속성값은 자바스크립트로 이루어져야 한다. 웹브라우저는 onclick이 할 일을 기억하고 있다가 해당 사건이 일어나면 속성값대로 실행한다.
`onclick`은 버튼을 클릭했을 때,
`onchange`는 해당 `HTML element`가 변했을 때(아래 코드에서는 텍스트 창에 키보드로 입력한 뒤에 마우스 커서로 텍스트 창밖 아무 데나 클릭했을 때),
`onkeydown`은 사용자가 입력하면서 키보드를 하나 누른 순간(capslock, 백스페이스 등을 포함한 대부분의 키보드, fn은 제외),
`onmouseover`는 해당 `HTML element` 위에 마우스 커서를 올려놓았을 때,
`onmouseout`은 해당 `HTML element`에 마우스 커서를 올려놓았다가 밖으로 이동했을 때,
`onload`는 해당 페이지 로딩이 끝났을 때 사용자가 원하는 이벤트가 실행된다.

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/59449215/193825625-83f93461-adaa-4e66-84c0-01fd461d3d5a.png" /></td>
    <td><img src="https://user-images.githubusercontent.com/59449215/193828456-08305b91-3f9e-4a19-8731-023aed4429c7.gif" /></td>
  </tr>
</table>

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
    </head>
    <body onload="alert('loaded')">
        <input type="button" value="hi" onclick="alert('hi')">
        <input type="button" value="경고" onmouseover="alert('warning')"> 
        <input type="button" value="out" onmouseout="alert('out')">
        <input type="text" onchange="alert('change')">
        <input type="text" onkeydown="alert('key down')">
    </body>
</html>
```

참고자료
- [JavaScript Events](https://www.w3schools.com/js/js_events.asp)

<br />

**생각해보기**
1) 버튼 위에 마우스를 올리면 경고창이 뜨는 웹 사이트를 만드는 개발자가 되었다고 상상해 봅시다. 어떤 이벤트를 사용하면 좋을지 알아보세요. (힌트: javascript mouseover event라고 검색해보세요!)
 : 
 ```html
 <input type="button" value="경고" onmouseover="alert('warning')">
 ```

<br />

### (5) HTML과 JS의 만남: 콘솔

> 학습 목표: 콘솔을 통해서 간단한 Javascript 코드를 실행시킬 수 있다.

`fn+f12` 또는 `오른쪽 마우스 버튼+검사`: 콘솔(Console) 창 열기

Elements가 선택된 상태로 esc버튼을 누르면 콘솔창이 아래에 생긴다.

콘솔창을 이용하면 파일을 열지 않고도 자바스크립트 코드를 실행할 수 있다(계산, 데이터 처리 등).

<img src="https://user-images.githubusercontent.com/59449215/193825659-ea51c3a6-e427-431d-b6f5-6c436b5b34a2.png"/>

```js
alert('words'.length)
```

<br />

**생각해보기**
1) 현재 페이지에서 콘솔을 이용해서 '생각해보기' 라는 경고창을 띄워봅시다.
 : `alert('생각해보기')`

<br />
<br />
