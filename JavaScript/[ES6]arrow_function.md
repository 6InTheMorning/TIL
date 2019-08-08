# Arrow Function (화살표 함수)

> **'arrow function'** 은 ES6에 새롭게 추가된 함수이다.

arrow function을 써도 되고, 기존의 형태인 function() {} 을 사용해도 된다.

## 기존 함수

```javascript
function exam1(x, y) {
  return x * y
}

function not1(x) {
  return !x
}
```

## arrow function (화살표 함수)

```javascript
const exam3 = (x, y) => {
  return x * y
}
// or
const exam4 = (x, y) => x * y

const not2 = x => {
  return !x
}
// or

const not3 = x => !x
```

위의 함수 예들은 모두 같은 역할을 하고 있다. 화살표 함수에서는 return을 줄일 수 있다.(exam4)
<br> not3처럼 매개변수가 하나일 때는 매개변수를 소괄호로 묶어주지 않아도 된다.

기존의 함수와 화살표 함수의 또 다른점은 this 바인딩 방식이다.
기존의 함수는 this의 탐색 범위가 함수 스코프 안이지만, 화살표함수는 this 바인딩을 갖지 않는다.

```javascript
var es5 = {
  name: "choco",
  friends: ["mint", "banana", "melon"],
  printFriends: function() {
    var that = this
    console.log(that)
    this.friends.forEach(function(friend) {
      console.log(that.name, friend)
    })
  }
}

es5.printFriends()

var es6 = {
  name: "vanilla",
  friends: ["cookie", "mango", "apple"],
  printFriends: function() {
    this.friends.forEach(friend => {
      console.log(that.name, friend)
    })
  }
}

es6.printFriends()
```

es5.printFriends() 안의 forEach문에서는 function을 사용했으므로 각자 다른 함수 스코프의 this를 가진다. 따라서 that이라는 변수를 선언해서 es5에 접근하고 있다.<br>
하지만 es6.printFriends() 안의 forEach문에서는 화살표 함수를 사용하고 있으므로 바깥 스코프의 printFriends()의 this를 그대로 사용할 수 있다. (상위 스코프의 this를 그대로 사용)
