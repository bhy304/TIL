# [Day02] JS and CSS Clock

### 코드

[02 - JS and CSS Clock](https://github.com/bhy304/JavaScript30/tree/master/02%20-%20JS%20and%20CSS%20Clock)

------

### 개요

CSS와 JavaScript를 이용한 아날로그 시계 구현

------

### 학습 내용

#### 1. CSS

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

|              속성              | 설명                                                         |
| :----------------------------: | :----------------------------------------------------------- |
|             width              | 요소의 가로 값을 정의한다.                                   |
|             height             | 콘텐츠 요소의 세로 값을 설정한다.                            |
|           background           | 배경 속성 값을 정의한다.                                     |
|            position            | 요소의 위치를 설정한다.                                      |
|              top               | 위치 요소의 위쪽 속성을 설정한다.                            |
|      **transform-origin**      | transform-origin 속성은 요소의 움직임 방향 및 기준점을 설정한다. <br />transform 속성과 같이 설정하며 기준점에 따라 애니메이션의 방향을 설정할 수 있다. |
|         **transform**          | transform 속성은 요소의 움직임을 표현한다.<br />transform 속성은 컨텐츠 요소를 이동(translate), 회전(rotate), 확대 or 크기변경(scale), 기울기(skew) 등의 효과를 줄 수 있다. 애니메이션 작업시 가장 많이 쓰는 요소이다. 요소를 이동시키거나 회전 시킬 수 있으며, 원근점(perspective)를 사용하며 3D까지 구현할 수 있다. |
|         **transition**         | transition 속성은 요소의 움직임을 정의한다.                  |
| **transition-timing-function** | transition-timing-function 속성은 요소의 움직임 기능을 정의한다.<br />cubic-bezier(n, n, n, n) : 베지어 곡선값을 만들어서 속도를 설정한다. |

#### 2. JS

##### 2-1) now() Method

```javascript
function setDate() {
    const now = new Date(); // Date() : 현재 날짜 및 시간의 값을 가져온다.

    const hour = now.getHours(); // 현재 시 정보
    const hourDegrees = ((hour / 12) * 360) + 90;
    hourHand.style.transform = `rotate(${hourDegrees}deg)`;

    const minutes = now.getMinutes(); // 현재 분 정보
    const minutesDegrees = ((minutes / 60) * 360) + 90;
    minHand.style.transform = `rotate(${minutesDegrees}deg)`;

    const seconds = now.getSeconds(); // 현재 초 정보 
    const secondsDegrees = ((seconds / 60) * 360) + 90; // CSS에서 transform의 rotate를 90deg로 설정했기 때문에 90을 더해준다. 
    secondHand.style.transform = `rotate(${secondsDegrees}deg)`;
}
```

##### 2-2) setInterval()

```javascript
setInterval(setDate, 1000);
```
setInterval() 함수는 일정한 시간 간격으로 코드를 반복 실행하는 함수이다.

##### ※ setInterval()과 setTimeout() 함수의 차이?

* ```setInterval```은 일정 시간 간격으로 함수가 주기적으로 실행된다.

* ```setTimeout```은 일정 시간 간격 이후에 함수가 한번 실행된다. 