# LifeCycle

**Will**이 붙은 메서드는 어떤 작업을 작동하기 전에 실행되는 메서드이고, **Did**가 붙은 메서드는 어떤 작업을 작동한 후에 실행되는 메서드이다.

라이프사이클은 **마운트, 업데이트, 언마운트** 이 세 가지로 나뉜다.

**마운트**: DOM이 생성되고 웹 브라우저상에서 나타나는 것을 마운트라고 한다.<br />

**업데이트**: 컴포너트를 업데이트를 할 때는 네 가지 경우가 있다.

1. props가 바뀔 때
2. state가 바뀔 때
3. 부모 컴포넌트가 리렌더링될 때
4. this.forceUpdate로 강제로 랜더링을 트리거할 때

**언마운트**: 마운트의 반대 과정, 컴포넌트를 DOM에서 제거하는 것을 언마운트라고 한다.
<br />
<br />

### 라이프사이클 메서드

1. **render()** :<br />
   메서드는 컴포넌트 모양새를 정의한다. 이 메서드 안에서는 절대로 state를 변형해서는 안되며, 웹 브라우저에 접근해서도 안된다. DOM 정보를 가져오거나 변화를 줄 때는 ComponentDidMount에서 처리해야한다.

2. **constructor** :<br />
   컴포넌트의 생성자 메서드로 컴포넌트를 만들때 처음으로 실행된다. 이 메서드에서 초기 state를 정할 수 있다.

3. **getDerivedStateFromProps** :<br />
   props로 받아 온 값을 state에 동기화 시키는 용도로 사용하고, 컴포넌트를 마운트하거나 props를 변경할 때 호출한다.

4. **componentDidMout** :<br />
   컴포넌트를 만들고, 첫 렌더링을 다 마친 후 실행한다. 이 안에서 다른 자바스크립트 라이브러리 또는 프레임워크의 함수를 호출하거나 이벤트 등록, setTimeout, setInterval, 네트워크 요청 같은 비동기 작업을 처리한다.

5. **shouldComponentUpdate** :<br />
   props 또는 state를 변경했을 때, 리렌더링을 시작할지 여부를 지정하는 메서드이다. 이 메서드에서는 true 또는 false 값을 반환해야 한다. <br />
   이 메서드에서 false 값을 반환하면 업데이트 과정은 여기에서 중지된다.

6. **getSnapshotBeforeUpdate** :<br />
   render 메서드를 호출한 후 DOM에 변화를 반영하기 바로 직전에 호출하는 메서드이다. 여기서 반환하는 값은 componentDidUpdate에서 세 번째 파라미터인 snapshot 값을 전달 받을 수 있다.<br/>
   주로 업데이트하기 직전의 값을 참고할 일이 있을 때 활용한다.

7. **componentDidUpdate** : <br />
   리렌더링을 완료한 후 실행한다. 업데이트가 끝난 직후이므로, DOM 관련 처리를 해도 괜찮다. <br />여기서는 prevProps 또는 prevState를 사용해서 컴포넌트가 이전에 가졌던 데이터에 접근할 수 있다.<br />
   (getSnapshotBeforeUpdate에서 반환한 값이 이쓰면 여기에서 snapshot 값을 전달 받을 수 있다.)

8. **componentWillUnmount** : <br />
   컴포넌트를 DOM에서 제거할 때 실행한다. componentDidMount에서 등록한 이벤트, 타이머, 직접 생성한 DOM이 있다면 여기에서 제거 작업을 해야한다.
