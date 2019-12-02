# [Day03] Update CSS Variables with JS

### 코드

[03 - CSS Variables](https://github.com/bhy304/JavaScript30/tree/master/03%20-%20CSS%20Variables)

------

### 개요

Javascript로 CSS 변수 업데이트

------

### 학습 내용

#### 1. HTML

```<input>``` Tag type
```html
<!-- // range -->
<input id="spacing" type="range" name="spacing" min="10" max="200" value="10" data-sizing="px">
<input id="blur" type="range" name="blur" min="0" max="25" value="10" data-sizing="px">

<!-- // color -->
<input id="base" type="color" name="base" value="#ffc600">
```

#### 2. CSS Variables

CSS 변수는 문서 전반적으로 재사용할 어떠한 특정 값을 포함하는, CSS 작성자가 정의한 엔터티이다.<br>CSS 변수는 종속되며, 부모로부터 값을 상속받는다.

* 변수 선언
```css
:root {
    --base: #FFC600; /* 사용자 정의 속성 표기법 */
    --spacing: 20px;
    --blur: 10px;
}
```

* 변수의 사용
```css
img {
    padding: var(--spacing);
    background: var(--base);
    filter: blur(var(--blur));
}
```

#### 3. JS

- ```document.querySelector()``` : 주어진 CSS 선택자에 대응하는 요소 중 첫 번째 요소를 반환
- ```document.querySelectorAll()``` : 주어진 CSS 선택자에 대응하는 요소 모두를 반환

- 개발자도구의 콘솔창을 통해 ```document.querySelectorAll('.controls input')``` 확인하면 ```__proto__ : NodeList```임을 알 수 있다. <br>NodeList가 Array는 아니지만 **```forEach()```**를 사용하여 반복할 수 있다. 
  
```javascript
function handleUpdate() {
    console.log(this.value);
}

inputs.forEach(input => input.addEventListener('change', handleUpdate));
inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));
```

##### 3-1. 이벤트 타입
| 이벤트명  | 발생하는 시점                                                |
| --------- | ------------------------------------------------------------ |
| change    | 변동이 있을 때 발생                                          |
| mousemove | 포인팅 장치가 엘리먼트 위에서 이동했을 때(마우스가 이동하는 동안 계속 실행됨.) |

##### 3-2. dataset
HTMLElement.dataset 속성은 HTML이나 DOM 요소의 커스텀 데이터 속성(data-*)에 대한 읽기와 쓰기 접근을 허용한다.
```html
<!-- HTML -->
<input id="spacing" type="range" name="spacing" min="10" max="200" value="10" data-sizing="px">
```
```javascript
// JavaScript
const suffix = this.dataset.sizing
```

##### 3-3. element.style을 통한 인라인 스타일
Javascript를 사용해서 CSS를 조작하는 가장 기본적인 방법은 style을 이용하는 것이다.
```javascript
document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
```