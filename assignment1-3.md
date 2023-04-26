# 🏅 심화 이론 문제

## 라벨 태그의 역할 + React에서 htmlfor의 쓰임

우선 label tag는 무엇일까?

> 간단하게 설명하면 <br> > `<label>` tag는 무언가의 이름표 역할을 해주는 태그다.
>
> > 특히 input의 이름표 역할을 해주는 태그 / input 태그를 도와주는 역할을 하는 태그다.

MDN에서 보면

- label 텍스트는 텍스트 입력과 시각적으로 관련이 있을뿐만 아니라 프로그래밍적으로도 관련이 있다. 쉽게 input 태그에 label 태그로 이름을 붙이면서 input에 대한 부가적인 설명이 될 수 있도록 하는 것.
- 관련 label 을 클릭해서 input 자체에 초점을 맞추거나 활성화를 시킬 수 있다. (활성되어서)늘어난 / 누를 수 있는 영역(hit area)은 터치스크린 사용자를 포함해 입력하려하는 모든 사람에게 자신이 선택한 것의 이해를 도울 수 있도록 한다.

> 요약하면, input 태그에 대한 부가적 설명 기능 + input의 클릭 영역 확대와 같은 기능

링크 : <https://developer.mozilla.org/ko/docs/Web/HTML/Element/label>

>`<label>` 태그의 for 속성은 레이블이 연결된 입력 요소의 id 속성을 지정하는 데 사용된다. 사용자가 레이블 텍스트를 클릭하면 연결된 입력 요소가 활성화되어 지정된 작업이나 이벤트가 트리거된다.

링크 : ChatGpt
<br>

단순하게

```html
<label>text</label>

<input type="text" name="id" value="default value" />
```

단순하게 이러면 저 label 태그는 어떤 것의 이름표의 역할로 남아 있다.<br>
여기서 input의 이름표로 text라는 글자를 쓰기 위해서라면 `for`속성을 사용해서<br>
`<input>`의 `id`속성과 연계해서 사용하면 된다.

<br>

여기서 중요한 것은 `<input>`의 **id**와 `<label>`의 **for** 속성의 값을 동일하게 해주는 것이다.

```html
<label for="this">text</label>

<input id="this" type="text" name="id" value="default value" />
```

### But! React에서 for을 쓰면 Error가 발생한다.

Because React에서의 for는 for문(반복문)을 의미하기 때문이다.<br>

그럼 React에서 `<label>`의 `for` 속성을 쓰려면 어떻게 해야할까?
<br>

> `htmlfor` 라는 속성을 통해 input의 id 속성과 연결한다.

링크 : <https://jnarin-development-story.tistory.com/152>

전반적으로 for 속성은 레이블을 입력 필드와 연결하기 위해 HTML에서 사용될 수 있지만 JavaScript 키워드와의 충돌을 피하고 JSX 구문과의 호환성을 보장하기 위해 React에서 htmlFor를 사용하는 것이 중요하다.

링크 : ChatGpt

<br>
<hr>
<br>

## Javascript의 비구조화 할당 방식

**비구조화할당**이란, 배열이나 객체 속성을 해체하여 개별 변수에 값을 담을 수 있는 JavaScript 표현식을 말한다. 또는 **구조 분해 할당**

> 뜻 : 배열이나 객체에서 요소를 해체해서 개별 변수에 그 값을 담는 것.<br>
>> 왜 쓸까?  : 그렇게 변수로 관리하면 사용할 때 간결하고 읽기 쉬우니까!

1. 배열 구조 분해 할당

```javascript
ex)
let arr = [1, 2, 3];
let [one, two, three] = arr;
```

2. 객체 구조 분해 할당

```javascript
ex)
let person = {
 name: "이정환",
 age: 25,
 location: "경기도"
};

let { name, age, location } = person;
```

-> 객체를 구조 분해 할당할 때는 데이터 저장 순서가 아니라 `key`를 기준<br>
-> person 객체의 value가 키를 기준으로 왼쪽 변수에 할당된다.<br>
-> 이 때 변수의 이름을 바꾸고 싶다면 `name : n ` 이런 식으로 바꾸면 된다.

링크 : <https://reactjs.winterlood.com/>

### 어! 그런데 만약에 객체 속성이 갖고 있는 값이 여러개면 어떻게 하죠?!

```javascript
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  address: {
    city: 'New York',
    state: 'NY',
    country: 'USA'
  }
};

const { firstName, lastName, age, address: { city, country } } = person;

console.log(firstName); // 'John'
console.log(lastName); // 'Doe'
console.log(age); // 30
console.log(city); // 'New York'
console.log(country); // 'USA'
```

대괄호 열어서 처리해주시면 됩니다~

<br>
<hr>
<br>

## 컴파일러와 인터프리터

<br>

**컴파일러** : 특정 프로그래밍 언어로 쓰여있는 문서를 다른 프로그래밍 언어로 옮기는 언어 변역 프로그램

> 우리가 작성한 프로그래밍 언어를 컴퓨터가 알아들을 수 있는 어셈블리 언어로 번역

즉, 원시코드(Source Code / 컴파일러의 input)을 목적코드(Ojbect Code / 컴파일러의 output)로 번역.

<br>

**인터프리터** : 프로그래밍 언어의 원시코드를 바로 실행하는 컴퓨터 프로그램<br>

> 원시 코드의 내용을 한 번에 한 줄씩 읽어들여서 바로 실행

<br>

공통점 : 고급 프로그래밍 언어를 저급 프로그래밍 언어로 변환해준다는 것.

|                                컴파일러                                 |            인터프리터             |
| :---------------------------------------------------------------------: | :-------------------------------: |
| 전체 프로그래밍 코드를 스캔하고 <br> 코드 전체를 통째로 목적코드로 변환 |      소스코드를 한 줄씩 해석      |
|                   해석 시간이 길지만, 실행시간이 짧음                   | 해석 시간이 짧지만, 실행시간이 김 |

<br>

### 그럼 JavaScript는 단순 인터프리터 언어일까?

> 자바스크립트는 interpreter 언어다. 개발자도구 콘솔에서 스크립트를 작성해 실행하는데 컴파일이 필요하지 않기 때문이다. **하지만, 결론부터 이야기하면 자바스크립트도 컴파일 과정을 거친다.** 다만 자바스크립트 엔진 내부에서 실행중 컴파일이 필요한 경우에 내부에서 컴파일 한다.

자바스크립트의 성능을 비약적으로 향상시킬 수 있었던 이유는 엔진 내부에서 **컴파일 과정**을 거치기 때문이다.

엔진이 작동하는 원리

1. 엔진이 실행할 JS 파일을 받게 된다.
2. 그리고 파싱, AST(Abstract Syntax Tree)를 구축하는 과정을 거친다.
3. 다음으로 Interpreter가 코드를 읽으며 실행한다.
   - 코드를 수행하는 과정에서 프로파일러가 지켜보며 최적화 할 수 있는 코드를 컴파일러에게 전달해준다. 주로 반복해서 실행되는 코드 블록을 컴파일(최적화)한다.
   - 아 그니까 읽다가 **어? 이거 반복되는데?**하면 이걸 코드 블록으로 가져가서 컴파일을 해. 
4. 그리고 원래 있던 코드와 최적화된 코드를 바꿔준다.
   - 코드를 우선 인터프리터 방식으로 실행하고 필요할 때 컴파일 하는 방법을 JIT(Just-In-Time) 컴파일러 라고 부른다.
   - 크롬의 V8 엔진을 포함해 Mozilla의 Rhino, Firefox의 SpiderMonkey도 같은 방법을 사용한다.

> 결론은, 자바스크립트는 실행되는 플랫폼에 따라 인터프리팅과 컴파일이 혼합되어 사용된다. 이 방식은 자바스크립트의 성능을 크게 향상시켰다.

so, 요약하자면

- 자바스크립트는 인터프리터 언어다
- 하지만 플랫폼에 따라 엔진 내부에서 컴파일 과정을 거친다

<br>

링크 : <https://www.oowgnoj.dev/review/advanced-js-1>

<br>
<hr>
<br>

## JavaScript에서 var보다 let,const를 사용해야 하는 이유

var를 쓰지 않는 이유:

- let과는 다르게 이름 중복이 가능함. (혼란 야기)
- let, const는 block scope지만, var는 function scope
  - 이 말은 변수를 선언한 블록에 따라 지역 스코프가 정해지는 것이 아니라, 함수 내부에서 선언한 변수만 지역 스코프를 갖는다는 의미.

그래서 JS에서는 대개 2가지 종류로 변수를 선언한다.<br>

1. let -> 변할 수 있는 값에 대해서 저장
2. const -> 상수 저장
   - let과는 다르게 const에서는 변수 초기화를 해줘야 한다.

<br>

`호이스팅(Hoisting)`이란, var 선언문이나 function 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 말한다.<br>

자바스크립트는 ES6에서 도입된 let, const를 포함하여 모든 선언(var, let, const, function, function, class)을 호이스팅한다.

하지만, var 로 선언된 변수와는 달리 let 로 선언된 변수를 선언문 이전에 참조하면 참조 에러(ReferenceError)가 발생한다.

```javascript
console.log(it); // undefined
var it;

console.log(ti); // Error: Uncaught ReferenceError: bar is not defined
let ti;
```

여기서 보면 `var` 변수 같은 경우는 후에 선언되었음에도 불구하고 선언과 동시에 초기화가 되기 때문에 값이 아직 할당되지 않았다는 `undefined`가 출력이 된다.<br>
But, `let`변수는 선언과 초기화 단계가 분리되어 진행한다.

> 간단하게 말하면<br>
> var 변수를 무분별하게 사용해버리면 엄청 지저분한 코드가 나올 것이다.<br>
> 이름도 중복 가능해서 혼란을 야기할 뿐만 아니라 fucntion scope를 가지기 때문에 갑자기 호이스팅이 되어서 "왜 이게 출력이 되지"라는 혼란을 야기할 수도 있다.

그니까 선언을 안했는데 불러오면 초기화는 안되어있지만 선언을 한 상태가 되버리는거야. 그래서 undefined가 출력이 돼. 

링크 : <https://reactjs.winterlood.com/>

<br>
<hr>
<br>

## 함수 호이스팅 (Hoisting)

> Hoisting : 프로그램에서 변수나 함수를 호출하거나 접근하는 코드가 함수 선언 코드보다 위에 있음에도 불구하고, 마치 선언 코드가 위에 있는 것처럼 동작하는 것.
>
> > 쉽게 설명하면, 순서에 상관없이 함수를 불러오는 것.

원래 JS에서는 위에서 아래로 Parsing하는데, 함수 호이스팅덕분에 함수 호출이 선언보다 먼저 선행되어도 함수가 실행이 가능해.<br>
-> `단! 함수표현식으로 선언된 함수는 호이스팅되지 않아!`<br>

**함수선언식**

```javascript
function functionName() {
  실행식;
}
```

**함수표현식**

```javascript
let functionName = function () {
  실행식;
};
```

그래서 호이스팅한다면

```javascript
functionName();

function functionName() {
  실행식;
}
```

> But, 함수표현식은 호이스팅되지 않는다.

링크 : <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/function>

<br>
<hr>
<br>

## ☠️ 콜백 함수 그리고 비동기 처리

> 인수로 전달되는 함수 = 콜백함수!
>
> > 중복 코드 문제를 해결하기 위해 쓰임. <br>
> > 기능 하나를 만들어서 사용하는 느낌임.

```javascript
ex)
function repeat(count, callBack) { ③
 for (let idx = 0; idx < count; idx++) {
 callBack(idx + 1);
 }
}
function origin(count) {
 console.log(count);
}
function double(count) { ①
 console.log(count * 2);
}
repeat(5, double); ②
```

위 코드를 보면

- 그냥 count를 출력하는 코드 한 놈
- count \* 2를 수행하고 출력하는 놈 한 놈

이렇게 기능적인 부분을 수행하는 함수를 만들고, 그것을 <br>
반복문에 callback함수로 받아와서 사용하는 것.

링크 : <https://reactjs.winterlood.com/>

<br>

Example.

```javascript
function calculate(num1, num2, operation) {
  return operation(num1, num2);
}

function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

console.log(calculate(10, 5, add));      // Output: 15
console.log(calculate(10, 5, subtract)); // Output: 5
```

정말 직관적으로 이해가 가능함. 
- 계산을 하는 특정 함수를 만들 것이고, 거기에 계산식과 숫자 2개를 불러올거임
- 그리고 계산식의 값이 return값이 됨
- 해당 계산식으로 들어갈 함수 더하기, 빼기를 기능적으로 밖에 빼놔서 따로 선언함
  - 이를 통해 내가 만들 계산 함수도 깔끔하게 작성이 가능하고 간결하며 가독성이 좋음
  - 전체 코드의 입장에서도 add와 subtract함수를 언제든지 재사용할 수 있음
  - 내가 특정 함수를 만들 때 원하는 단계에 원하는 함수를 불러와서 사용할 수 있음(매우 유연한 코드 작성이 가능함!)

<hr>

## 비동기 처리

Javascript는 기본적으로 위에서부터 아래로 순차적으로 실행이 됨.

> 간단하게 이해하자!<br>
> 동기 처리 : 순차적으로 실행 // 말 그대로 순서대로 융통성 없이 진행<br>
> 비동기 처리 : 별도로 작업을 진행하게 해서 독립적으로 동작이 가능하도록
>
> > 즉, 순차적으로 실행할 필요 없이 융통성 있게 작업 처리하는 것.

1. setTimeOut() 함수

```javascript
setTimeout(() => { ①
 console.log("1번!");
}, 3000);
console.log("2번!"); ②

output : 2번! 1번!
```

원래 순차적으로 했으면 1번이 될 때까지 기다리고 1번이 호출되고 2번이 호출되겠지만, 비동기 처리를 통해 오래 걸리는 작업은 독립적으로 실행되도록 했다.

<br>

2. 콜백함수로 비동기 처리

```javascript
ex)
function double(num, cb) {
 setTimeout(() => {
 const doubleNum = num * 2;
 cb(doubleNum); ②
 }, 1000);
}
double(10, (res) => { ①
 console.log(res);
});
console.log("마지막"); ③

output : 마지막 20
```

콜백함수로 비동기 처리는 결국 비동기 처리된 값을 콜백 함수가 처리한다는 의미로 이해하면 편함.

<br>

3. Promise 객체를 사용해서 비동기 처리<br>

Promise : 비동기 처리를 목적으로 제공된 객체 (비동기 작업을 진행에 따라 3단계로 나누어 관리)

- 대기(pending) : 작업 미완료
- 성공(Fulfilled) : 작업 완료
- 실패(Rejected) : 작업 실패

<br>

우선, Promise 객체를 만들어봅시다

```javascript
const promise = new Promise(실행 함수);
```

여기서 실행 함수 -> 비동기 처리를 하는 함수입니당

```javascript
ex)
const promise = new Promise(
 function (resolve, reject) { ①
 setTimeout(() => {
 resolve("안녕");
 }, 500);
 }
);

output : 안녕
```

이 output -> 비동기 결과값을 비동기 작업이 아닌 곳에서 이용하려면<br>
Promise 객체의 then Method 사용

<br>

> then Method : 인수로 전달한 콜백 함수의 비동기 작업이 성공했을 때 실행됨 (resolve시 실행)

```javascript
ex)
const promise = new Promise(
 function (resolve, reject) {
 setTimeout(() => {
 resolve("안녕") ①
 }, 500);
 }
);
promise.then(function (res) { ②
 console.log(res);
});

output : 안녕
```

여기서 function의 매개변수 res에는 resolve값이 인수로 전달됨.

> catch Method : Reject시 실행

```javascript
ex)
const promise = new Promise(
 function (resolve, reject) {
 setTimeout(() => {
 reject("실패") ①
 }, 500);
 }
);
promise.catch(function (res) { ②
 console.log(res);
});

output : 실패
```

링크 : <https://reactjs.winterlood.com/>

<br>
<hr>
<br>

## 바벨 (Babel)

> 정말 간단하게 설명하자면<br>
> 최신 자바스크립트 문법을 구형 브라우저에서도 돌 수 있도록 코드 자체를 변환해주는 기능

왜 사용하느냐? : 최신 구문으로 코드를 작성하고 최신 기능과 성능 향상을 활용하는 동시에 코드가 이전 브라우저 및 환경과 호환되도록 할 수 있기때문에!!

<br>

Babel

- 바벨을 사용하면 JSX를 브라우저가 읽기 쉬운 ES5 코드로 변환
- 이를 바탕으로 개발자는 최신 문법을 사용하면서도 여러 브라우저에서 작동될 수 있는 코드 작성 가능

링크 : <https://brunch.co.kr/@skykamja24/576>

그럼 어떻게 해야 바벨을 사용할 수 있어?
-  npm 또는 yarn과 같은 패키지 관리자를 사용하여 Babel과 필요한 플러그인 또는 사전 설정을 설치
   1. `@babel/preset-env`: 이 사전 설정은 최신 JavaScript 구문(예: ES6+)을 이전 브라우저 및 환경과 호환되는 코드로 변환하는 데 사용된다.
   2. `@babel/preset-react`: 이 사전 설정은 JSX 구문(React에서 사용됨)을 브라우저에서 실행할 수 있는 JavaScript로 변환하는 데 사용된다.
   3. `@babel/plugin-proposal-class-properties`: 이 플러그인은 클래스 속성(ES6에 도입된 기능)을 브라우저에서 실행할 수 있는 JavaScript로 변환하는 데 사용된다.
   4. `@babel/plugin-transform-runtime`: 이 플러그인은 regenerator-runtime으로 폴리필링하여 이전 브라우저에서 async 및 await 키워드 지원을 활성화하는 데 사용된다.
   5. ```npm install --save-dev @babel/preset-env @babel/preset-react``` 이런 식으로 설치하면 된다.
- 설치되면 터미널에서 babel src -d dist와 같은 명령을 실행하여 Babel을 사용하여 코드를 번역할 수 있어.
- 여기서 src는 소스코드가 포함된 디렉토리 / dist는 번역된 코드가 있을 디렉토리야.
<br>
<hr>
<br>

## React Element / JSX

React에서 요소는 React 애플리케이션 사용자 인터페이스의 가장 작은 빌딩 블록입니다. 가상 DOM 노드를 나타내는 일반 JavaScript 개체로, 화면에 무엇을 렌더링해야 하는지 설명합니다.


요소는 세 가지로 구성됩니다.


1. HTML 태그를 나타내는 문자열이거나 사용자 지정 React 구성 요소에 대한 참조일 수 있는 요소 유형입니다.
2. 요소에 필요한 모든 데이터 또는 구성을 포함하는 props 객체.
3. 다른 React 요소 또는 일반 텍스트일 수 있는 자식 요소 목록.

React 요소는 일반적으로 개발자가 JavaScript 코드 내에서 HTML과 유사한 코드를 작성할 수 있도록 하는 JavaScript의 구문 확장인 JSX 구문을 사용하여 생성됩니다. 생성된 요소는 실제 DOM에 렌더링되도록 ReactDOM.render() 메서드로 전달됩니다.


요소는 변경할 수 없습니다. 즉, 일단 생성되면 해당 속성을 변경할 수 없습니다. 대신 새 요소를 만들고 렌더링 메서드에 전달하여 UI를 변경합니다.

링크 : chatGpt

## JSX : 자바스크립트와 HTML 태그를 섞어 사용하는 문법

```javascript
function Something() {
  const number = 1;
  return (
    <div>
      <h1>Something</h1>
      <h2>{number}</h2>
    </div>
  );
}
export default Something;
```

요런 식으로 html 태그 내에 javascript의 표현식을 직접 사용할 수 있다.

링크 : <https://reactjs.winterlood.com/>

<br>
<hr>
<br>

## Dom 그리고 React의 Virtual Dom

<br>

Dom : 문서 객체 모델 || HTML 코드를 트리 형태로 변환한 구성물<br>
-> 역할 : 돔은 웹 브라우저가 직접 생성하며, HTML 코드를 렌더링

```javascript
ex)
<!DOCTYPE html>
<html>
 <head>
 <meta charset="UTF-8" />
 <script>
 function onClickButton() {
 const h1Elm = document.getElementById("h1"); ②
 h1Elm.innerText = "반가워요!"; ③
 }
 </script>
 </head>
 <body>
 <h1 id="h1">안녕하세요!</h1>
 <button onclick="onClickButton()">인사말 바꾸기</button> ①
 </body>
</html>
```

-> javascript에서 DOM에 접근하는 방법<br>
-> document를 통해 접근

<br>

Update : 결국 페이지를 다시 렌더링하는 행위.

<br>

기본적인 브라우저의 렌더링 과정

1. HTML 코드를 해석해서 트리 형태의 DOM으로 전환<br>
   CSS코드도 Style RUles로 전환
2. 페이지에 어떤 요소가 어디에 있는 지를 아는 DOM과 DOM 각각의 요소에 <br>스타일을 정의하는 Style Rules가 합쳐져 **렌더 트리**가 만들어짐
3. 렌더 트리 정보를 바탕으로 요소의 위치를 px 단위로 계산 <br>
   -> 이 과정이 **레이아웃**
4. 해당 정보를 바탕으로 페이지에 그림 -> 페인팅

그래서 업데이트를 하면 이 렌더링 과정이 계속 반복되는 것임<br>
-> 심지어 단순한 버튼 클릭으로 색깔을 바꾸는 작업 하나도 다시 렌더링 과정을 거쳐서 실행이 됨.

<br>

그럼 어떻게 하면 효율적으로 업데이트를 할 수 있을까? <br>

😎 바로 한꺼번에 모아서 업데이트를 해버리는 것!
<br>

리액트는 이를 위해서 Virtual DOM을 활용합니다!

> Virtual DOM = DOM의 사본
>
> > 페이지에서 변경 사항이 생기면 먼저 Virtual dom을 업데이트하는 식으로 변경 사항들을 모았다가 한 번에 실제 DOM을 업데이트시켜버림.
> >
> > > 즉 virtual dom이 업데이트되더라도 실제 DOM은 변화가 없는 상태였다가 필요한 사항이 한꺼번에 업데이트된다는 것임.

링크 : <https://reactjs.winterlood.com/>

<br>
<hr>
<br>

## React의 리렌더링 조건

1. Props 변경: 구성 요소가 부모로부터 새 Props을 받으면 새 데이터를 반영하기 위해 다시 렌더링됩니다.
2. 상태 변경: 구성 요소의 상태가 변경되면 새 상태를 반영하기 위해 다시 렌더링됩니다.
3. 컨텍스트 변경: 구성 요소가 컨텍스트 데이터에 의존하고 해당 데이터가 변경되면 새 컨텍스트를 반영하기 위해 다시 렌더링됩니다.
4. 구성 요소 계층 구조 변경: 상위 구성 요소가 다시 렌더링되면 모든 하위 구성 요소도 다시 렌더링됩니다.
5. useEffect 종속성 변경: 구성 요소가 종속성과 함께 useEffect 후크를 사용하는 경우 종속성이 변경되면 다시 렌더링됩니다.
6. 강제 재렌더링: 새 상태로 setState 메서드를 호출하거나 구성 요소에 새 props를 전달하여 구성 요소를 강제로 다시 렌더링할 수 있습니다.
7. 라우터 탐색: URL 변경에 따라 구성 요소가 렌더링되는 경우(예: React Router를 사용하는 경우) URL이 변경되면 다시 렌더링됩니다.

링크 : ChatGpt <What are the re-render conditions in react?>

> 리렌더링은 성능에 영향을 줄 수 있으므로 React 애플리케이션을 개발할 때 이러한 리렌더링 조건을 인식하는 것이 중요해
>> 왜와이 : 컴포가 너무 자주 리렌더링되면 응용 프로그램 속도도 느려지고 하위 컴포도 불필요하게 리렌더링되기 때문에.

그럼 어떻게 방지할까?
1. 메모리제이션 / shouldComponentUpdate와 같은 기술 사용
2. Profiler API 및 React Devtools와 같은 react 내장 도구 사용해서 앱의 렌더링 기능을 분석하고 최적화 영역 식별


#### useMemo를 쓰는 거 
예를 들어서 알려줄게 <br>
글 목록 부모 컴포가 있고, 그 안에 여러 글 자식 컴포가 있어. 그러면 원래는 부모 컴포가 리렌더되면 자식 모두 다 리렌더되잖아. <br>
근데 부모에 메모를 걸어서 래핑하면 부모만 렌더가 되도록 설정할 수 있어. 굳이 자식까지 모두 리렌더될 필요성을 없애준다.

