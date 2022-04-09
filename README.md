# momentum note
JS Study - 바닐라 JS로 크롬 앱 만들기

### 1.4
JS를 배워야 하는 이유
- 프론트엔드에 쓸 수 있는 유일한 프로그래밍 언어
    - 브라우저에 내장
- socket.io
    - 채팅, 실시간 기능

### 2.0
vscode tip
- code project_name
- !
- link:css
JS는 맨 끝에서 link

### 2.2
console.log()
variable
- const (always)
- let (sometimes)
- var (never)
    - 구버전
    - 언어를 통한 보호를 받지 못함
    - 실수로 값을 업데이트 해도 알아차릴 수 없음
- naming
    - camelCase
        - 공백이 필요하다면 다음 단어의 첫 문자를 대문자로 씀

### 2.4
- null : 값이 없음이 선언됨
- undefined : 값이 선언되지 않음

### 2.5
- const array에 item 추가, 수정, 삭제 가능

### 2.6
- object
    - player.name
    - player["name"]
    - {}
    - 콤마(,)
    - constant object의 property 추가, 수정, 삭제 가능
        - 전체를 바꾸려 할 때 오류 발생

### 2.7
- function
    - 캡슐화
    - argument(인수)
    - press play: ()

### 2.8
- parameter(매개변수, 임의의 값)
    - type 쓸 필요 없음
```
// function 선언
function function_name(){}

// object 안에 function 선언
function_name: function(){}
```

### 2.12
- return시 function 종료

### 2.13
- prompt() // 안씀
- typeof 변수
- parseInt()
    - 숫자가 아닌 것
        - NaN(Not a Number)
- function: 내부에서부터 외부로 실행됨

### 2.14
- isNan()
- if(condition){}
    - else if(condition), else
    - boolean

### 2.16
- === (is)
- !== (is not)
    - type까지 비교
- if: 작은 괄호로부터 큰 괄호로 넘어감

### 3.0
- document

### 3.1
- const title = document.getElementById("title")
    - title은 HTML element, DOM(Document Object Model)
    - title.id
    - title.className
    - title.innerText
    - ...
- console.dir(title)

### 3.2
- getElementsByClassName, getElementsByTagName
    - array 반환
- **document.querySelector(".hello h1:first-child")**
    - CSS 방식으로 element 검색
    - 여러개일 때: the first element 반환
- querySelectorAll
    - array 반환

### 3.3
- title.style.color
    - style에 접근 가능
    - style은 CSS를 통해 변경되는 것이 좋음
- event
    - listener
    - title.addEventListener("click", handleTitleClick)
        - function 이름에 () 붙지 않음

### 3.4
- event
    - mouseenter
    - mouseleave
- event 찾기
    - 구글링
        - tag명 html element mdn 검색
        - "Web APIs"가 포함된 페이지 접속
    - console.dir
        - on으로 시작하는 것들

### 3.5
- title.onclick = handleTitleClick;
    - 요소.on이벤트명 = 함수명;
- addEventListener는 나중에 removeEventListener를 통해 event listener를 제거할 수 있다는 장점이 있다.
- window.addEventListener(이벤트명, 함수명)
    - resize
    - copy
    - offline
    - online
- document.body.style.backgroundColor
    - body, head, title

### 3.6
1. find the element
2. listen for an event
3. react to that event

### 3.7
- h1.className = "clicked";
    - css에서 clicked class의 속성을 지정한 뒤,
    - js에서 html 요소의 class 이름을 clicked로 부여하는 방식
```
function handleTitleClick() {
    const clickedClass = "clicked";
    if (h1.className === clickedClass) {
        h1.className = "";
    } else {
        h1.className = clickedClass;
    }
}
```
- raw string 대신 constant 사용하기

### 3.8
- classList
    - contains(token), add, remove, replace, ...
```
function handleTitleClick() {
    const clickedClass = "clicked";
    if (h1.classList.contains(clickedClass)) {
        h1.classList.remove(clickedClass);
    } else {
        h1.classList.add(clickedClass);
    }
}
```
- **toggle(token)**
    - 위 코드와 같은 역할
```
function handleTitleClick() {
    h1.classList.toggle("clicked");
}
```

### 4.0
```
// document 또는 하나의 element에서 검색 가능
const loginInput = document.querySelector("#login-form input");
const loginButton = document.querySelector("#login-form button");

function onLoginBthClick() {
    // console.dir(loginInput); // value property
    console.log(loginInput.value);
}

loginButton.addEventListener("click", onLoginBthClick);
```

### 4.1
- 문자열.length
- input의 유효성 검사 기능을 쓰기 위해서는 input이 form안에 있어야 함
    ```
    <form id="login-form">
    <input
        required
        maxlength="15"
        type="text"
        placeholder="What is your name?"
    />
    <button>Log In</button>
    </form>
    ```

### 4.2
- EventListener function의 첫번째 argument: event에 대한 정보가 들어있는 object
    - event로 작성
    - event.preventDefault(): event의 기본 행동이 발생되지 않도록 막음
        - ex) form submit -> page refresh

### 4.3
- console.dir(event)
    - path
        - a: anchor
    - type
    - defaultPrevented

### 4.4
- display: none;
```
// 이름을 제출했을 때 form은 숨기고 h1은 나타나게 하기
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");
const greeting = document.querySelector("#greeting");

const HIDDEN_CLASSNAME = "hidden"; // string을 저장할 때 upper case 표기 (convention), 실수를 만들고 싶지 않은 string

function onLoginSubmit(event) {
    event.preventDefault();
    loginForm.classList.add(HIDDEN_CLASSNAME);
    const userName = loginInput.value;
    // greeting.innerText = "Hello " + userName;
    greeting.innerText = `Hello ${userName}`; // backtick(`): 영어 입력 ` or option + ₩
    greeting.classList.remove(HIDDEN_CLASSNAME)
}

loginForm.addEventListener("submit", onLoginSubmit); // enter or click btn
```

### 4.5
- Inspect - Application - Local Storage (API)
- localStorage
    - setItem(key, value)
    - getItem(key)
    - removeItem(key)

### 4.6
- vscode tip
    - option + up / down: 코드 위치 변경
    - double click: drag
- loading username
```
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");
const greeting = document.querySelector("#greeting");

const HIDDEN_CLASSNAME = "hidden";
const USERNAME_KEY = "username";

function onLoginSubmit(event) {
    event.preventDefault();
    loginForm.classList.add(HIDDEN_CLASSNAME);
    const username = loginInput.value;
    localStorage.setItem(USERNAME_KEY, username);
    paintGreetings(username);
}

function paintGreetings(username) {
    greeting.innerText = `Hello ${username}`;
    greeting.classList.remove(HIDDEN_CLASSNAME);
}

const savedUsername = localStorage.getItem(USERNAME_KEY);

if (savedUsername === null) {
    loginForm.classList.remove(HIDDEN_CLASSNAME); // show form
    loginForm.addEventListener("submit", onLoginSubmit);
} else {
    paintGreetings(savedUsername);
}
```

### 5.0
- divide and conquer
- interval
    - ex) every 2s 마다 실행
    - setInterval(함수명, ms); // 1000ms = 1s

### 5.1
- timeout
    - setTimeout(함수명, ms); // 한번만 실행
- Date (object)
    - const date = new Date();
    - date.getDate()
    - date.getFullYear()
    - ...
```
const clock = document.querySelector("#clock");

function getClock() {
    const date = new Date();
    const hours = String(date.getHours()).padStart(2, "0");
    const minutes = String(date.getMinutes()).padStart(2, "0");
    const seconds = String(date.getSeconds()).padStart(2, "0");
    clock.innerText = `${hours}:${minutes}:${seconds}`;
}

getClock(); // website가 load되자마자 실행
setInterval(getClock, 1000);
```

### 5.2
- padStart
    - 문자열.padStart(2, "0")
        - 문자열의 길이가 2보다 작으면 문자열 앞에 "0"를 채워서 2로 만들기
- padEnd
    - 뒤쪽에 문자 추가
- String(number)
    - number -> string
    - ex) String(new Date().getHours())

### 6.0
- Math module
    - random() // 유사난수 [0, 1)
    - round() // 반올림
    - ceil() // 천장
    - floor() // 마루
- Math.floor(Math.random() * quotes.length);
    - [0, len-1]

### 6.1
- document.createElement(HTML tag)
- appendChild()
- prepend() // 앞에 추가

### 7.1
1. listen submit event
2. prevent default
3. get the value from the input

### 7.2
- event.target // click된 HTML element
    - parentElement
- remove()

### 7.3
- JSON.stringify()

### 7.4
- JSON.parse()
- forEach
    - item
- arrow function
```
(param1, param2, …, paramN) => { statements }
(param1, param2, …, paramN) => expression
// 다음과 동일함:  => { return expression; }

// 매개변수가 하나뿐인 경우 괄호는 선택사항:
(singleParam) => { statements }
singleParam => { statements }

// 매개변수가 없는 함수는 괄호가 필요:
() => { statements }
```

### 7.6
- Date.now() for random ID

### 7.7
- 지우고 싶은 item을 제외
    - filter(function)
        - filter한 새 array를 반환
        - item // forEach와 비슷
        - function이 true를 반환하면 포함

### 8.0
- navigator.geolocation.getCurrentPosition()
    - 성공했을 때 함수, 에러가 났을 때 함수
    - GeolocationPosition obj
- https://openweathermap.org/
    - API
- fetch(url);
    - call url
    - then()
    - fetch(url).then(response => response.json());
