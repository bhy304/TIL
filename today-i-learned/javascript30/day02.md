# [Day02] JS and CSS Clock

### 코드

[02 - JS and CSS Clock](https://github.com/bhy304/JavaScript30/tree/master/02%20-%20JS%20and%20CSS%20Clock)

------

### 개요

CSS와 JavaScript를 이용한 아날로그 시계 구현

------

### 학습 내용

##### 1. CSS

```css
.hand {
    width: 50%;
    height: 6px;
    background: black;
    position: absolute;
    top: 50%;
    transform-origin: 100%;
    transform: rotate(90deg);
    transition: all 0.05s;
    transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
}
```

1-1) width : width 속성은 요소의 가로 값을 정의한다.

1-2) height : height 속성은 콘텐츠 요소의 세로 값을 설정한다.

1-3) background : background 속성은 배경 속성 값을 정의한다.

1-4) position : position 속성은 요소의 위치를 설정한다. 

1-5) top : top 속성은 위치 요소의 위쪽 속성을 설정한다.

1-6) transform-origin : transform-origin 속성은 요소의 움직임 방향 및 기준점을 설정한다. transform 속성과 같이 설정하며 기준점에 따라 애니메이션의 방향을 설정할 수 있다.

1-7) transform : transform 속성은 요소의 움직임을 표현한다.

transform 속성은 컨텐츠 요소를 이동(translate), 회전(rotate), 확대 or 크기변경(scale), 기울기(skew) 등의 효과를 줄 수 있다. 애니메이션 작업시 가장 많이 쓰는 요소이다. 요소를 이동시키거나 회전 시킬 수 있으며, 원근점(perspective)를 사용하며 3D까지 구현할 수 있다. 

1-8) transition : transition 속성은 요소의 움직임을 정의한다.

1-9) transition-timing-function : transition-timing-function 속성은 요소의 움직임 기능을 정의한다.

속성(property) : 

cubic-bezier(n, n, n, n) - 베지어 곡선값을 만들어서 속도를 설정한다. 

##### 2. JS

##### now() Method

```now.getHours()```

```now.getMinutes()```

```now.getSeconds()```

```javascript
const now = new Date();

const hour = now.getHours();

const minutes = now.getMinutes();

const seconds = now.getSeconds();
```

##### setInterval()