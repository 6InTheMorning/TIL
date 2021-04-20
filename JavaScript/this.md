# this란?
> 자바스크립트 내에서 'this'는 호출자가 누구인지를 나타낸다.  
> **함수가 호출되는 방식**에 따라 'this'는 달라진다고 볼 수 있다.  
> 호출 방식 - 일반함수, 메소드, 생성자(new), 명시적 지정(call, apply, bind)

<br/>
<br/>

## 1. 일반함수 호출 시 this는 전역객체(window)에 바인딩
```javascript
//기본적으로 this는 브라우저에서 window이다.
var a=30
console.log(window.a === a) //true

function Func(){
    return this
}

Func() === window //true
```
<br/>

## 2. 메소드 호출 시 this는 호출한 객체에 바인딩
```javascript
var firstName= 'Mat'

var who = {
    firstName:'Noah',
    lastName: 'Ohlsen',
    crossfitter(){
        console.log(this.firstName + this.lastName)
    },
}

who.crossfitter() //NoahOhlsen

/* MatOhlsen이 아니라 NoahOhlsen으로 찍히는데 
    이는 this가 호출한 객체 Who에 바인딩 되었기 때문이다. */
```
<br/>

## 3. 생성자(new)함수 호출 시 this는 생성자함수가 만든 객체에 바인딩
```javascript
function Crossfitter(firstName, lastName){
    this.firstName = firstName,
    this.lastName = lastName,
    this.newChamp = function () {
        console.log(this.firstName + this.lastName) //'MathewFraser'
        return this
    },
}

const champion = new Crossfitter('Mathew', 'Fraser')

champion.newChamp() //this는 생성한 객체에 바인딩한다.

champion.newChamp() === window //false
```
<br/>

## 4. call, apply, bind를 이용하여 this를 바인딩하여 함수를 호출할 수 있다
    call과 apply는 함수를 즉시 호출하고 bind는 this를 바인딩한 새로운 함수를 리턴한다.

* ## call
```javascript
function champion(a, b, c){
  console.log(`Champion is ${this.name}`);
  console.log(a + b + c);
}

var corssfitter = {
    name: 'Mathew Fraser'
}

champion.call(corssfitter, 1, 2, 3); //첫번째 인자가 this로 바인딩할 값
// Champion is Mathew Fraser
// 6
```

* ## apply
```javascript
function champion(a, b, c){
  console.log(`Champion is ${this.name}`);
  console.log(a + b + c);
}

var corssfitter = {
    name: 'Mathew Fraser'
}

champion.apply(corssfitter, [1, 2, 3]);
// Champion is Mathew Fraser
// 6

 /* 첫번째 인자를 this로 바인딩하는 것은 call과 같지만,
    apply는 나머지 인자를 배열 형태로 전달한다. */
```

* ## bind
```javascript
function champion(a, b, c){
  console.log(`Champion is ${this.name}`);
  console.log(a + b + c);
}

var corssfitter = {
    name: 'Mathew Fraser'
}

champion.bind(corssfitter, 1, 2, 3); //함수 반환

champion.bind(corssfitter, 1, 2, 3)();
// Champion is Mathew Fraser
// 6 

/* 바인드는 첫번째 인자에 this를 바인딩하는 점은 같지만 
    함수를 실행하지 않으며 새로운 함수를 반환한다 */
```