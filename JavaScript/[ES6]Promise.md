# Promise

> 자바스크립트는 비동기 처리를 위해서 콜백 함수를 사용한다.<br>
하지만 이 콜백함수들이 늘어나면 늘어날수록 가독성과 예외처리들이 어려워지게 된다.<br>
특히 콜백들이 중첩에 중첩을 거듭하게되면 **'콜백지옥(Callback Hell)'** 이 발생하게 된다.
**Promise 패턴**으로 코드를 구성하게 되면 비동기 작업들을 조금은 수월하게 수행할 수 있게 된다.

## 설명할 예제

Promise는 실행될 때마다 진행상태를 체크함

**pending:**
Promise를 수행하고 있는 상태

**fulfilled:**
Promise가 성공적으로 수행된 상태

**rejected:**
Promise가 수행에 실패한 상태

**settled:**
Promise를 수행이 됐든 안됐든 일단 수행이 끝난 상태

이 4가지 상태중 1가지의 상태를 가지게 될 것이다.

```javascript
//Promise 선언
let promise = function(param) {
  return new Promise(function(resolve, reject) {
    window.setTimeout(function() {
      //  param이 true이면,
      if (param) {
        resolve("성공!!")
      }

      // param이 거짓이면,
      else {
        reject(Error("실패!!"))
      }
    }, 3000)
  })
}

//Promise 실행
promise(true)
  .then(text => {
    // 성공시
    console.log(text)
  })
  //실패시
  .catch(error => {
    console.log(error)
  })
```

### 1. Promise 선언부분

```javascript
//Promise 선언
let promise = function(param) {
  return new Promise(function(resolve, reject) {
    window.setTimeout(function() {
      //  param이 true이면,
      if (param) {
        resolve("성공!!")
      }

      // param이 거짓이면,
      else {
        reject(Error("실패!!"))
      }
    }, 3000)
  })
}
```

'new Promise' 로 Promise가 생성되고 resolve 또는 reject가 호출되기 전까지 penging 상태가 된다. 이후 비동기 처리 작업을 하고 나서 이루어지는 수행들에 문제가 없다면 **resolve** 함수를 호출하고, 문제가 있으면 **reject**함수를 호출한다.

### 2. Promise 실행부분

```javascript
//Promise 실행
promise(true)
  .then(text => {
    // 성공시
    console.log(text)
  })
  //실패시
  .catch(error => {
    console.log(error)
  })
```

promise()를 호출하고, 내부에서 resolve가 호출되면 then이 실행되어 ' 성공!! 이
