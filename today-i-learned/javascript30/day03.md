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

CSS 변수는 문서 전반적으로 재사용할 어떠한 특정 값을 포함하는, CSS 작성자가 정의한 엔터티이다. CSS 변수는 종속되며, 부모로부터 값을 상속받는다.

* 변수 선언
```css
:root {
    --base: #FFC600; // 사용자 정의 속성 표기법
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