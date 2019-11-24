# [Day01] JavaScript Drum Kit

### 코드

[01 - JavaScript Drum Kit](https://github.com/bhy304/JavaScript30/tree/master/01%20-%20JavaScript%20Drum%20Kit)

------

### 개요

키보드를 누르면 화면 효과와 함께 소리가 나는 드럼킷

------

### 학습 내용

##### 1. HTML ```<kbd>``` tag

```<kbd>``` 태그는 키보드(keyboard) 입력을 나타낼 때 사용한다. <br>
```<kbd>``` 요소 내의 텍스트는 브라우저의 기본 고정폭 글꼴을 사용하여 표현된다. 

```html
<kbd>A</kbd>
```

##### 2. HTML data-* Global Attributes

> ```data-*``` 속성은 표준이 아닌 속성이나 추가적인 DOM 속성, Node.setUserData()과 같은 다른 조작을 하지 않고도, 의미론적 표준 HTML 요소에 추가 정보를 저장할 수 있도록 해준다. 

```html
<div class="keys">
	<div data-key="65" class="key">
		<kbd>A</kbd>
	<span class="sound">clap</span>
</div>

<audio data-key="65" src="sounds/clap.wav"></audio>
```

HTML5의 도입으로 HTML에서도 데이터를 저장할 수 있게 되었고 CSS, JavaScript에서도 접근할 수 있게 되었다. 

모든 Element에서 ```data-```로 시작하는 속성은 무엇이든 사용할 수 있다. 화면에 안 보이게 글이나 추가 정보를 Element에 담아놓을 수 있다.

##### 3. KeyboardEvent

| 이벤트명 | 이벤트 발생 시점                                             |
| :------: | ------------------------------------------------------------ |
| keydown  | 키가 눌렸을 때                                               |
| keypress | shift, Fn, CapsLock 을 제외한 키가 눌린 상태일 때(연속적으로 실행됨) |
|  keyup   | 키 누름이 해제될 때                                          |

```EventTarget.addEventLister()``` 메서드는 지정한 이벤트가 대상에 전달될 때마다 호출할 함수를 설정한다.

```javascript
window.addEventListener('keydown', function(e) {
	console.log(e.keyCode); // 키보드를 누를때마다 이벤트가 발생하고 콘솔창에 keyCode 출력한다.
});
```

##### 4. audio element 찾기

 ```querySelectorAll()``` 메서드는 CSS 선택자(아이디, 클래스, 속성, 속성값 등)를 이용하여 HTML 요소를 선택한다.

```javascript
const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
```

만약 audio element가 없다면(audio 태그의 data-key 속성과 매칭되는 값이 없다면) null 값을 출력하게 된다. 
그러므로 audio element가 없다면 return

```javascript
if(!audio) return; 
```

##### 5. HTMLMediaElement.currentTime Property

같은 키를 연달아 누르면 연속해서 소리가 나지 않는다. ```currentTime```을 0으로 설정해 오디오의 재생 시점을 처음으로 다시 돌려준다. 

* ```currentTime``` : 음악의 재생 지점이다. 초 단위이며, 0 값인 경우에 처음부터 음악을 재생

```javascript
audio.currentTime = 0;
```

##### 6. HTMLMediaElement.play() Method

```javascript
audio.play(); 
```

data-key가 매칭되면 audio Element 소리 재생

##### 7. playing 클래스 추가

```javascript
const key = document.querySelector(`.key[data-key="${e.keyCode}"]`);
```
class가 "key"인 Element 중에서 data-key의 값이 e.keyCode와 일치하는 것을 찾는다.

```javascript
key.classList.add('playing'); // key에 playing 클래스 추가
```

##### 8. Transitionend Event

```transitionend Event```는 CSS transition이 완료된 이후에 발생한다.

```javascript
const keys = document.querySelectorAll('.key');
keys.forEach(key => key.addEventListener('transitionend', removeTransition));  // removeTransition 콜백 함수 호출
```

```javascript
function removeTransition(e) {
    //console.log(e); // 키보드 A 클릭시 총 6개의 transitionEvent가 한번에 발생한다.
    if (e.propertyName !== 'transform') return; // 이벤트 발생시 프로퍼티의 이름이 transform이 아니면 skip!
    //console.log(e.propertyName);
    this.classList.remove('playing');
}
```