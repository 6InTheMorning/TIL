# [ES6] const와 let

> 자바스크립트를 처음 배울 때 'var'로 변수를 선언한다고 배웠다. 하지만 **ES6** 문법을 배우면서 var 대신 **const, let**으로 대체하게 되었다.

var과 const,let의 가장 큰 차이점은 '**스코프**' 이다.

이전에 썼던 var는 함수 스코프를 가지는 반면, const와 let은 **블록 스코프**를 가진다.

코드를 예로 들어보면

```javascript
if (ture) {
  var x = 7
}
console.log(x) // 7 출력

if (true) {
  let y = 7
}
console.log(y) // Uncaught ReferenceError: y is not defined 에러 출력
```

var로 선안한 x를 콘솔로 찍어보면 7이 정상적으로 출력되지만 let으로 출력한 y는 에러가 발생한다.
var는 함수스코프를 가지기 때문에 if의 블록과 상관없이 접근이 가능하지만, let 또는 const는 블록 스코프를 가지므로 if 블록 밖에서는 변수에 접근을 할 수가 없다.
( '{}'로 묶은 부분 블록의 범위 )

추가로 const는 한 번 값을 대입하면 다른 값을 대입할 수 없다. (다른 값 대입시 에러 발생)
let은 값을 대입하고 나서 다른 값 대입이 가능하다.
