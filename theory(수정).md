## 🎨 라벨 태그 역할 & React에서 htmlFor 사용하는 이유

## HTML에서 label 태그
`-` 사용자 인터페이스 항목의 설명<br>
 `-` label 태그는 input 태그의 의미를 정의하기 위한 태그<br> 
 `-` 보통 input 태그가 있을 때 어떤 입력창인지 앞의 텍스트를 보고 판단<br>
`-` input 태그들에 대해 의미 설명할 때 label 태그 사용할 수 있음<br><br>
<사용법><br>
1. `<input>`에 id 속성을 넣는다<br>
2. `<label>`에 id 와 같은 값의 for 속성을 넣는다

```html
<form>
  <label for = "description">설명: </label>
  <input type="text" id="decription" name="설명">
</form>
```
### `-` react에서 for는? 
React에서는 for는 for문(반복문)을 의미하기 때문에 React에서 <label>의 for 속성을 쓸 수 없음<br> 따라서 htmlfor 라는 속성을 통해 input의 id 속성과 연결



참고: <https://dololak.tistory.com/722> <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<https://velog.io/@agatha/label>

<br>
<hr>
<br>

## 🎨 Javascript의 비구조화 할당(=구조 분해 할당) 방식
`-` Destructuring Assignment<br>
`-` 구조를 분해해 할당하는 문법, **배열이나 객체에서 요소를 해체해 개별 변수에 그 값을 담는 것**<br><br>
`1.` 배열의 구조 분해 할당<br>
`-`구조 분해 할당 전
```javascript
let arr = [1, 2, 3];

let one = arr[0];
let two = arr[1];
let three = arr[2];

console.log(one, two, three);
``` 
`-` 구조 분해 할당 후
```javascript
let arr= [1, 2, 3];
let[one, two, three] =arr;

console.log(one, two, three);
```
```
1 2 3 
```
=> 배열을 구조 분해 할당하면, 저장된 요솟값을 변수 선언과 동시에 순서대로 할당함

`2.` 객체의 구조 분해 할당
```javascript
let person = {
  name: "양혜림",
  age: 23,
  location: "경기도"
};

let {name, age, location} = person;

console.log(name, age, location);
```
```
양혜림 23 경기도
```
=> 객체를 구조 분해 할당할 때는 데이터 저장 순서가 아닌 key를 기준으로 함 <br><br>
참고: '한입 크기로 잘라 먹는 리액트' 책

<br>
<hr>
<br>


## 🎨 인터프리터 & 컴파일러 
인터프리터와 컴파일러는 고레벨 언어를 기계어로 변환하는 번역기 즉, <mark>사람과 컴퓨터 사이의 통역사</mark>

`-` 컴파일러: 특정 프로그래밍 언어로 쓰여 있는 문서를 다른 프로그래밍 언어로 옮기는 언어 번역 프로그램<br>
`-` 인터프리터: 기계어를 다른 언어로 번역할 필요 없이 프로그래밍 언어의 소스 코드를 바로 실행하는 컴퓨터 프로그램<br><br>

<table>
  <tr>
    <th></th>
    <th style="text-align:center">컴파일러</th>
    <th style="text-align:center">인터프리터</th>
  </tr>
  <tr>
    <td>번역 방식</td>
    <td>소스코드 전체 한 번에 번역</td>
    <td>한 줄 씩 읽어들이면서 번역</td>
  </tr>
  <tr>
    <td>번역 속도</td>
    <td style="text-align:center">느림</td>
    <td style="text-align:center">빠름</td>
  </tr>
  <tr>
    <td>실행 시간</td>
    <td style="text-align:center">짧음</td>
    <td style="text-align:center">긺</td>
  </tr>
</table>

<br>

## Javascript는 인터프리터?
기본적으로 자바스크립트는 인터프리터 언어에 해당 <br>
(다른 대표적 컴파일러 언어인 C/C++의 경우 컴파일 과정을 통해 실행 파일을 생성해주어야 비로소 프로그램 실행 가능)<br>
자바스크립트 같은 경우에는 한 줄 씩만 입력해도 바로바로 실행하며 결과를 확인하는 것 가능해 인터프리터 언어에 해당 <br>
**but** 자바스크립트가 따로 별도의 과정없이 컴퓨터가 실행되는 것 x (자바스크립트가 인터프리터에 전해지기 일련의 과정 거쳐야 함)
### < 자바스크립트 구동원리 >
자바스크립트 코드 == <span style = "color: lightgreen">바스크립트 엔진</span> ==> 바이트 코트 == <span style = "color: lightgreen">가상머신</span> ==> 기계어 ====> 컴퓨터

> `1)` 바이트 코드로의 변환<br>
&nbsp;: <span style = "color: yellow">자바스크립트 엔진</span>에 의해 바이트코드로 변환<br>

 &nbsp; 어떻게 자바스크립트 엔진에 의해 어떻게 바이트 코드로 변환되냐? <br>
 &nbsp; ~ 엔진 내 인터프리터가 진행 , 인터프리터에 전달되기 전에도 일련의 과정 필요<br>
- (V8엔진 등장 이전)<br>
&nbsp;&nbsp;자바스크립트 코드 == <span style = "color: lightgreen">토크나이저</span> ==> 토큰 == <span style = "color: lightgreen">파서</span> ==> AST == <span style = "color: lightgreen"> 인터프리터</span> ==> 바이트 코드
 <br>

 - (V8엔진 등장 이후)<br>
&nbsp;&nbsp; **프로파일러**라는게 등장 <br>
&nbsp;`-` 인터프리터를 관찰하며 실행되는 코드를 계속 모니터링, 모니터링하는 과정에 코드내에 반복 실행되는 것이 있다면 이를 컴파일러에게 넘겨 실시간으로 컴파일 함, 이를 통해 최적화된 바이트 코드를 생성<br>
`-` 필요할 때마다 컴파일 하는 컴파일러를 JIT(Just-In-Time) 컴파일러라고 부름
 <br>

> `2)` 기계어로 변환<br>
&nbsp;: CPU마다 기계어를 다르게 해석하기에 가상머신은 최적화된 기계어 제작함<br>

>`3)` CPU 코드 실행<br>
&nbsp;: 기계어를 실행해 데이터 저장 및 연산 작업 진행<br>

 

<br>

### <span style = "color: yellow">&nbsp;결론!!!!</span>

```
기본적으로 인터프리터 언어로서의 성질을 가지지만, 성능상의 최적화를 위해 컴파일러 언어의 특성도 같이 가진다.
```

<br>

링크: <https://foreverhappiness.tistory.com/87> ,<br>
<https://velog.io/@seungchan__y/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-Compiler-Interpreter-%EC%96%B8%EC%96%B4%EB%8B%A4>



<br>
<hr>
<br>


## 🎨 Javascript에서 var보다 let, const 사용
`-` var 키워드 사용
```javascript
var age = 25;
console.log(age);

var age = 23;
console.log(age);
```
```
25
23
```
var 사용하면 변수의 이름이 중복해 사용해도 아무런 문제 발생 x <br>
=> 코드 많아지고 복잡해질 때 프로그래머들 혼란 빠뜨릴 여지 많음<br>
따라서 let, const 키워드 사용

`-` let 키워드 사용
```javascript
let age = 25;
console.log(age);

let age = 23;
console.log(age); // error: age는 이미 선언되었습니다.
```

### `-` 변수 호이스팅
:&nbsp; JavaScript에서 변수가 선언되기 전에도 참조할 수 있다는 독특한 동작 방식<br>
JavaScript에서 변수를 선언하면, 해당 변수는 스코프 내에서 유효하지만 변수의 선언문보다 변수를 사용하는 코드가 먼저 나오는 경우에도 JavaScript 엔진은 변수를 먼저 선언한 것으로 간주하는데 이를 **변수 호이스팅**이라고 합

`-` var는 함수 스코프를 가져 함수 내에서 선언된 변수는 함수 내에서만 유효하며, 함수 밖에서 선언된 변수는 전역변수로 선언<br>
 => 이때 변수 호이스팅이 발생해 변수가 선언되기 전에도 사용 가능<br>

`-` let, const는 블록 스코프를 가져 변수 호이스팅이 발생하지 않음<br>

<br>

참고: '한입 크기로 잘라 먹는 리액트' 책

<br>
<hr>
<br>


## 🎨 Javascript에서의 함수 선언식 & 함수 표현식

## `-` 함수 호이스팅 <br>
: 프로그램에서 변수나 함수를 호출하거나 접근하는 코드가 함수 선언 코드보다 위에 있어도, 선언 코드가 위에 있는 것처럼 동작하는 기능
```javascript
func();

function func(){
	console.log("hello");
}
```
```
hello
```
=> 자바스크립트에서 함수는 선언하기 전에도 호출할 수 있는데 이런 기능을 '호이스팅'이라 함<br>

### `-` 함수 선언식<br>
```javascript

function greetint(){
  console.log("안녕?");
}
```



### `-` 함수 표현식<br>
```javascript
let greetint = function(){
  console.log("안녕?");
}
```

### `-` 함수 호이스팅 적용<br>

```javascript
funcA(); // funcA 출력
funcB(); // Error: funcB 정의되지 않았으며 함수x

function funcA(){
  console.log("funcA");
}

let funcB = function(){
  console.log("funcB");
} 

```
함수 표현식: 함수 표현식을 사용하여 저장한 함수는 선언이 아닌 '값'으로 취급하기 때문에 호이스팅 하지 못함

함수 선언식: 함수 funcA을 선언하기 전에 호출하지만 오류 발생 x

<br><br>
참고: '한입 크기로 잘라 먹는 리액트' 책

<br>
<hr>
<br>


## 🎨 Javascript에서의 콜백 함수 & 비동기 처리
## `-` 콜백 함수<br>
: 함수는 다른 함수의 인수(=값)로도 전달할 수 있는데, 이를 **콜백 함수**
```javascript
// 매개변수 callBack에는 함수 childFunc저장
function parentFunc(callBack) { 
	console.log("parent");
	callBack();
}

function childFunc(){
	console.log("child");
}

parentFunc(childFunc);
```
```
parent
child
```
### `-` 콜백함수 왜 필요해?
```javascript
function repeat(count){
	for(let idx = 0; idx < count; idx++){
		console.log(idx + 1);
	}
}

function repeatDouble(count){
	for(let idx = 0; idx < count; idx++){
		console.log((idx + 1) * 2);
	}
}

repeatDouble(5);
```
```
2 4 6 8 10
```
=> 함수가 동일해도 특정 부분이 달라 새 함수를 만들게 되면 중복 코드가 발생함 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이때, 콜백 함수를 사용하면 효과적으로 해결 가능!
```javascript
function repeat(count, callBack){
	for(let idx = 0; idx < count; idx++){
		callBack(idx + 1);
	}
}

function origin(count){
	console.log(count);
}

function double(count){
	console.log(count * 2);
}

repeat(5, origin); // repeat 매개변수 callBack에 함수 origin 저장
repeat(5, double); // repeat 매개변수 callBack에 함수 double 저장
```
```
1 2 3 4
2 6 6 8
```
=> 콜백 함수를 이용하면 상황에 맞게 하나의 함수가 여러 동작 수행하도록 만들 수 있음<br>

## `-` 비동기 처리<br>
> 동기처리: 순차적으로 코드를 실행하는 것 (자바스크립트 기본적으로 동기적으로 동작)<br>
> 비동기처리: 특정 작업을 다른 작업과 관계없이 독립적으로 동작하게 만드는 것
 
 setTimeout 함수 이용하면 비동기적으로 처리 가능
 ```javascript
 setTimeout(function(){
  console.log("1번");
 },3000); // 두 번쨰 인수로 전달 받은 시간(3초)만큼 기다리고, 첫 번째 인수로 전달한 콜백함수를 실행함

 console.log("2번");
 ```
 ```
 2번
 1번
 ```
=>  비동기 처리를 통해 오래 걸리는 작업은 독립적으로 실행<br><br>
`-` 콜백 함수로 비동기 처리하기
```javascript
function double(num, cb){
  setTImeout(()=>{
    const doubleNum = num*2;
    cb(doubleNum);
  }, time);
}
double(10, (res) => {
  console.log(res);
})

console.log("마지막");
```
```
마지막
20
```
=> 콜백 함수 이용하면 비동기 작업의 결괏값을 사용할 수 o

<br><br>

참고: '한입 크기로 잘라 먹는 리액트' 책

<br>
<hr>
<br>


## 🎨 바벨이란?

babel은 javascript로 결과물을 만들어주는 컴파일러<br>
최신 버전의 자바스크립트가 실행되지 않는 구 버전의 브라우저에서 정상적으로 실행되도록 변환해주는 것
 

참고: <https://rypro.tistory.com/179>

<br>
<hr>
<br>


## 🎨 React 엘리먼트 & JSX

## `-` React 엘리먼트
: React에서 UI를 구성하는 가장 작은 단위<br>
: 일반적으로 JSX를 사용하여 정의, React.createElement() 사용해 정의할 수 있음<br>
: React Element는 Javascript의 객체로써, 화면에 실제로 그려지는 단위

## `-` JSX(JavaScript XML)
: React에서 UI를 구성하는 엘리먼트를 선언하기 위한 문법<br>
: JSX는 HTML 형태의 JavaScript Object를 사용하는 확장된 JavaScript문법 (공식 문법은 x) <br>
: JSX는 결과물로 React Element 를 생성

<br><br>
참고: <https://geonlee.tistory.com/180>

<br>
<hr>
<br>


## 🎨 브라우저 DOM &  React의 virtual DOM

## `-` 브라우저 DOM (Document Object Model, 문서 객체 모델)
: HTML 코드를 트리 형태로 변환하는 구성물<br>
: 웹 브라우저가 직접 생성, HTML 코드를 렌더링하기 위해 만듦<br>


> 돔의 업데이트가 많아지면 브라우저 성능 떨어짐 <br> 
> 그럼 어떻게 하면 될까? => virtual DOM 사용

## `-` virtual DOM
: 가상의 돔, 실제 돔의 사본<br>
: 리액트에서는 페이지에서 변경사항이 발생하면 먼저 버추얼 돔을 업데이트하는 방식으로 
변경사항을 모았다가 한 번에 실제 돔을 업데이트<br>
=> 업데이트가 잦아도 브라우저의 성능 떨어뜨리지 x
<br><br>

참고: '한입 크기로 잘라 먹는 리액트' 책

<br>
<hr>
<br>


## 🎨 React의 리렌더링 조건

1. state(상태)가 변경이 있을 때<br>
`-`  react는 state 변경이 감지되면 리렌더링 함
2. 새로운 props가 들어올 때<br>
`-` 부모 컴포넌트로부터 새 props가 들어오면 자식 컴포넌트는 리렌더링 됨
3. 기존 props가 업데이트 됐을 때<br>
`-` 부모 컴포넌트로부터 받은 props가 변경되면 props 값을 받은 자식 컴포넌트도 리렌더링 됨
4. 부모 컴포넌트가 리렌더링 될 때<Br>
`-` 부모 컴포넌트가 업데이트 되어 리렌더링 되면 자식 컴포넌트도 리렌더링 됨


참고: <https://fromnowwon.tistory.com/103>