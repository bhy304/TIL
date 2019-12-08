# [Day04] Array Cardio Day 1

### 코드

[04 - Array Cardio Day 1](https://github.com/bhy304/JavaScript30/tree/master/04%20-%20Array%20Cardio%20Day%201)

------

### 개요

Array 메소드를 배워봅시다!!

------

### 학습 내용

#### 1. Object 배열

* Array.prototype.filter()
* Array.prototype.map()
* Array.prototype.sort()
* Array.prototype.reduce()

#### 2. Console 메서드
* console.log() : 일반 메시지 출력
* console.table() : 표 형태의 데이터를 표에 그린다.

#### ES6문법
1. Function
```javascript
const fifteen = inventors.filter(inventor => (inventor.year >= 1500 && inventor.year < 1600));
console.table(fifteen);
```

```javascript
// 1. Function
const fifteen = inventors.filter(function(inventor) {
if(inventor.year >= 1500 && inventor.year < 1600) {
    return true; // keep it!
}});
console.log(fifteen);
```

2. Arrow Function Expression
```javascript
// 2. Arrow Function Expression
const fifteen = inventors.filter(inventor => {
if(inventor.year >= 1500 && inventor.year < 1600) {
  return true; // keep it!
} 
});
console.table(fifteen);
```

3. Sort the inventors by birthdate, oldest to youngest
```javascript
const fifteen = inventors.filter(inventor => (inventor.year >= 1500 && inventor.year < 1600));
console.table(fifteen);
```

```javascript
const ordered = inventors.sort(function(a, b) {
    if(a.year > b.year) {
        return 1;
    } else {
        return -1;
    }
});
```

4. How many years did all the inventors live?
```javascript
const totalYears = inventors.reduce((total, inventor) => {
    return total + (inventor.passed - inventor.year);
}, 0);

console.log(totalYears);
```

```javascript
var totalYears = 0;
for(var i = 0; i < inventors.length; i++) {
    totalYears += inventors[i].year
}

console.log(totalYears);
```

5. Sort the inventors by years lived
```javascript
const oldest = inventors.sort(function(a, b) {
   const lastGuy = a.passed - a.year;
   const nextGuy = b.passed - b.year;
   return lastGuy > nextGuy ? -1 : 1;
});
console.table(oldest);
```
```javascript
const oldest = inventors.sort(function(a, b) {
    const lastGuy = a.passed - a.year;
    const nextGuy = b.passed - b.year;
    if(lastGuy > nextGuy) {
        retur -1;
    } else {
        return 1;
    }
});
```

