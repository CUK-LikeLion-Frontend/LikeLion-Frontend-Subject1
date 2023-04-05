- ## 1. 라벨 태그의 역할과 htmlFor 옵션을 사용한 이유에 대해 설명해보세요.
<hr/>
<br/>
     =>
     라벨 태그는 웹 페이지에서 어떤 요소가 어떤 정보를 담고 있는지 설명하는 역할.
     <br/>

```html
<label for="username">사용자 이름:</label>
<input type="text" id="username" name="username" />
```

=>위와 같이 사용가능함.<br/>
for 속성 = "username"이기에 input 태그 안에 id="username"과 연결이 됨. <br/>
<br/>

htmlFor 옵션: React에서 사용되는 속성. htmlFor 옵션을 대신해서 라벨의 for 속성을 지정 할 수 있음. <br/>
<br/>

Why? => React에서 JSX를 사용 할 때, for 속성이 자바스크립트의 for 반복문과 혼동 될수 있기 때문이다.
<br/>

<hr/>
<br/>

- ## 2 .Javascript의 비구조화 할당 방식과 과제 코드의 어느 부분에서 사용되었는지 설명해보세요.

<hr/>
<br/>

비구조화할당:

- 배열이나 객체 속성을 해체하여 개별 변수에 값을 담을 수 있는 JavaScript 표현식을 말한다. 또는 구조 분해 할당이라고 한다.

- 장점:

  - 배열, 객체 내 값을 추출하는 코드가 매우 간단해짐.

  - 필요한 객체와 나머지 요소 분리가 매우 간단해짐.

  - 기본값 지정이 가능함.

- 사용된 부분:

```jsx
    function KmToMiles({ inverted, amount, onChange }) {
      return (
        <div
          style={{
            marginTop: "50px",
          }}
        >
          <h1>킬로미터/마일 변환기</h1>
          <div
            style={{
              marginTop: "50px",
            }}
          >
            <label htmlfor="kilo">킬로미터: </label>
            <input
              disabled={inverted}
              value={inverted ? amount * 1.609 : amount}
              onChange={onChange}
              placeholder="킬로미터"
              type="number"
            />
          </div>
```

=> props 객체를 인자로 받는 대신, inverted, amount, onChange 속성을 직접 추출한다.

<br/>

- ## 3.인터프리터와 컴파일러의 차이와 이를 중점으로 Javascript의 특징에 대해 설명해보세요. (Javascript는 단순한 인터프리터 언어가 아니에요!)

<hr/>
<br/>
<img src="https://velog.velcdn.com/images%2Fandthensome%2Fpost%2Fe4df7c88-e20f-407d-a602-32b2b7ebdf6f%2Fimage.png">

<br/>

### 컴파일러(compiler):

- 전체 파일은 스캔하여 한꺼번에 번역

- 초기 스캔시간이 오래 걸리지만, 한번 실행 파일이 만들어지고 나면 빠름.
- 기계어 번역과정에서 더 많은 메모리를 사용함.
- 전체 코드를 스캔하는 과정에서 모든 오류를 한꺼번에 출력해주기 때문에 실행 전에 오류를 알 수 있음.
- 대표적인 언엉로 C, C++, JAVA 등이 있음.

<br/>

### 인터프리터(interpreter):

- 프로그램 실행시 한번에 한문장씩 번역함.

- 한번에 한문장씩 번역후 실행시키기 때문에 실행 시간이 느림.

- 컴파일러와 같은 오브젝트 코드 생성과정이 없기 때문에 메모리 효율이 좋음.

- 프로그램을 실행시키고 나서 오류를 발견하면 바로 실행을 중지 시킴. 실행 후에 오류를 알 수 있음.

- 대표적인 언어로 Python, Ruby, Javascript 등이 있음. 즉, JavaScript 코드는 실행 전에 컴파일되지 않고 실행됨. 이것은 JavaScript가 브라우저나 Node.js 같은 플랫폼에서 직접 실행될 수 있도록 가능하게 함.

<br/>

JavaScript는 일반적으로 인터프리티 언어로 분류됨. 이는 JavaScript 코드가 실행되기 전에 미리 컴파일되지 않고, 코드가 실행되는 동안 인터프리터가 한 줄씩 코드를 읽어서 실행하기 때문.
<br/>
또한 JavaScript가 인터프리터 언어인 이유는 JavaScript 코드가 웹 브라우저에서 실행되기 때문입니다. 웹 브라우저는 JavaScript 코드를 실행할 때 인터프리터를 사용하여 코드를 실행합니다. 이 방식으로 웹 브라우저에서 JavaScript 코드를 실행할 수 있으며, 인터넷에 연결되어 있는 모든 기기에서 실행할 수 있습니다.

<br/>

- ## 4. Javascript에서 var보다 let, const 사용을 지향해야하는 이유를 설명해보세요. (변수 호이스팅에 대해 공부해보면 좋겠어요)

    <hr/>

  먼저 스코프의 개념을 알아야함.
  <br/>

  - 스코프

    - 변수에 접근할 수 있는 범위
    - 함수 실행컨텍스트 내부의 변수 환경

  - 함수 스코프

    - 새로운 함수가 생성되면 새로운 스코프가 발생함

    - 자바스크립트는 함수스코프를 따르는 언어

    - 함수에서 선언한 변수들은 해당 함수 내에서만 접근할 수 있음.

  - 블록 스코프

    - 블록이 생성될때 새로운 스코프가 생성

    - 자바스크립트는 원래 함수스코프를 따르지만, let과 const의 등장이후로 블록스코프형성도 가능해짐

  - var => 함수스코프
  - let, const => 블록스코프

  ```javascript
  var name = "kim";
  console.log(name); // kim
  var name = "lee";
  console.log(name); //lee
  ```

=> 위의 예제는 name을 중복해서 선언해도 에러가 발생하지 않음. 의도치 않게 변수명을 똑같이 선언하고 값을 재할당할 수 있기 때문에 문제가 발생할 수 있음.
<br/>
But, const는 변수 중복 선언이 불가함.
<br/>

<br/>

- ## 5. Javascript에서 함수 선언식과 함수 표현식에 대해 설명해보세요. (함수 호이스팅에 대해 공부해보면 좋겠어요)

<hr/>
<br/>

- 함수 호이스팅:

  - 코드 내에서 함수가 선언되기 이전에도 함수를 호출할 수 있게 해줌.

  - JavaScript 엔진이 코드를 실행하기 전에 함수 선언식을 먼저 메모리에 저장하기 때문에 가능.

  - 예시:

  ```javascript
  alert(myFunction());

  function myFunction() {
    return <h1>멋사 파이팅~</h1>;
  }
  //myFunction 함수가 나중에 선언되었지만 위에서 alert()로 호출이 가능한 것을 볼 수 있다.
  // 호이스팅으로 인해 선언부분만 먼저 실행이 되어 undefined로 초기화가 되기 때문에 발생하는 에러다.
  ```

  ```javascript
  alert(myFunction());

  const myFunction(){
  return <h1>멋사 파이팅!</h1>;
  }
  // 실행을 하면 TypeError가 발생함.

  ```

- 함수 선언식:

```javascript
function myFunction() {
  return <h1>멋사 파이팅~</h1>;
}
```

- 특징

  - 코드의 어느곳에서든 호출할 수 있음.

  - 함수가 호출되기 전에 자동으로 전체 스크립트에서 호이스팅됨.

  - 선언식은 호이스팅에 영향을 받지 않음.

  <br/>

- 함수 표현식

```javascript
const myFunction(){
  return <h1>멋사 파이팅!</h1>;
}
```

- 함수 표현식은 변수에 할당되므로 변수가 선언

- 함수 표현식은 호이스팅에 영향을 받음.

<br/>

- ## 6. Javascript에서 콜백함수와 비동기 처리에 대해 설명해보세요.

<hr/>

비동기 처리:

- 자바스크립트의 비동기 처리란 특정 코드의 연산이 끝날때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 자바스크립트의 특성을 의미함. 동시에 여러가지 작업을 처리할 수 있고 기다리는 과정에서 다른 함수를 호출할수도 있음.

동기 처리:

- 자바스크립트의 동기처리란 우선순위 작업이 끝날 때까지 기다리는동안 준비상태가 되기 때문에 다른 작업을 할수가 없음.
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHN2SS%2Fbtruc7Q3Ime%2FLVoXhKrKGQt1fPgqP5jPN1%2Fimg.png">
  <br/>

  콜백 함수:

- 콜백 함수는 함수 안에서 어떤 특정한 시점에 호출되는 함수를 말한다. 보통 콜백 함수는 함수의 매개변수로 전달하여 특정 시점에서 콜백 함수를 호출한다. 콜백함수(Callback Function)란 파라미터로 함수를 전달받아, 함수의 내부에서 실행하는 함수이다.

<br/>

- ## 7.바벨이란?
  <hr/>
  <br/>

바벨은 원래 '6to5'라는 이름을 가졌음. 이는 ES6(ECMAScript 6) => ES5(ECMAScript 5)로 바꿔주는 걸 뜻함.
<br/>
바벨의 기능은 최신 문법을 이전 세대의 코드로 호환해주는 기능 이외에도 다양한 기능을 제공하는데, 그 중 하나가 JSX 문법임.
<br/>
바벨을 사용하면 JSX를 브라우저가 읽기 쉬운 ES5 코드로 변환해주고, 이를 바탕으로 개발자는 최신 문법을 사용하면서도 여러 브라우저에서 작동될 수 있는 코드를 작성할 수 있음.
<br/>
JSX의 예시

```javascript
const element = <h1>Hello, world!</h1>;
```

- ## 8.React 엘리먼트와 JSX에 대해서 설명해보세요.

<hr/>

엘리먼트는 컴포넌트의 구성요소이며 React앱의 가장 작은 단위다. 엘리먼트는 화면에 표시할 내용을 기술한다.
<br/>

```html
<div id="root"></div>
```

root 안에 들어가는 모든 엘리먼트를 React DOM에서 관리하며 이것을 root DOM 노드라고 부른다. 일반적으로는 “컴포넌트”라는 개념이 더 많이 알려져 있는데, 엘리먼트는 바로 이 컴포넌트의 “구성 요소”라고 할 수 있다.
<br/>
리액트 엘리먼트는 일반적으로 JSX 문법을 사용한다.
<br/>

- JSX:

  - Javascript에서 XML을 추가한 확장 문법

  - 브라우저에 실행하기 전에 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환됨.

  - ```jsx
    const element = <h1>Hello, World!</h1>;
    ```

    => JSX코드 예시

  - ```js
    const element = React.createElement("h1", null, "Hello, World!");
    ```
    => JSX 예시 코드는 바벨에 의해 다음과 같은 자바스크립트 코드로 변환됨.

  <br/>

- ## 9.브라우저의 DOM과 React의 virtual DOM에 대해서 설명해보세요.
<hr/>

<br/>

DOM (Document Object Model):

- HTML 또는 XML document와 상호작용하고 표현하는 API이다.

- DOM은 브라우저에서 로드되며, 노드트리로 표현하는 document 모델이다.
- 문서 객체한 HTML, head body와 같은 태그들을 Javascript가 이용할 수 있는 객체를 의미함.
- div, input, a 등이 DOM에 해당함.

<img src="https://velog.velcdn.com/images/ctdlog/post/f2e1e3a9-d66e-42e8-a073-72540a01ace5/image.png">
<br/>
DOM이 존재하기 때문에 Javacript는 HTML 태그들을 수정할 수 있다.

<br/>

Virtual DOM:

- Virtual DOM을 사용하면 실제 DOM에 접근하여 조작하는 대신, 이를 추상화한 자바스크립트 객체를 구성하여 사용함.

  - React가 Virtual DOM을 반영하는 절차:

    - 데이터가 업데이트 되면, 전체 UI를 Virtual DOM에 리렌더링함

    - 이전 Virtual DOM에 있던 내용과 현재의 내용을 비교함
    - 바뀐 부분만 실제 DOM에 적용이 됨

    <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FSjw1C%2FbtrhBMKFIaQ%2FzSJrx0mIcjjvQQaVcEH8mk%2Fimg.png">

<br/>

- ## 10.React의 리렌더링 조건에 대해서 설명해보세요.

<hr/>

- state(상태) 변경이 있을 때

  - 리액트는 state 변경이 감지되면 재렌더링 한다.

- 새로운 props가 들어올 때

  - 부모 컴포넌트로부터 새 props가 들어오면 자식 컴포넌트는 재렌더링 된다.

- 기존 props가 업데이트 됐을 때

  - 부모 컴포넌트로부터 받은 props가 변경되면 props 값을 받은 자식 컴포넌트도 재렌더링 된다.

- 부모 컴포넌트가 재렌더링 될 때
  - 부모 컴포넌트가 업데이트 되어 재렌더링 되면 자식 컴포넌트도 재렌더링 된다.

### References

- https://fromnowwon.tistory.com/103

- https://chat.openai.com/chat
- https://m.blog.naver.com/haakuz/221341716499
- https://velog.io/@kimhyesu-_-/JavaScript-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94-%ED%95%A0%EB%8B%B9%EA%B5%AC%EC%A1%B0%EB%B6%84%ED%95%B4%ED%95%A0%EB%8B%B9

- https://velog.io/@dnjsdud2257/var%EB%A5%BC-%EC%A7%80%EC%96%91%ED%95%98%EA%B3%A0-const-let%EC%9D%84-%EC%8D%A8%EC%95%BC%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0

- https://kkhcode.tistory.com/6

- https://velog.io/@jangwonyoon/React%EC%97%90%EC%84%9C%EC%9D%98-%EB%B0%94%EB%B2%A8%EA%B3%BC-%EC%9B%B9%ED%8C%A9
