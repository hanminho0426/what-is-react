## Props 와 State

- Props는 컴포넌트 외부에서 컨포넌트에게 주는 데이터
- State는 컴포넌트 내부에서 변경할 수 있는 데이터
- 둘 다 변경이 발생하면, 랜더가 다시 일어날 수 있다.

## Render 함수

- Props와 State를 바탕으로 컴포넌트를 그린다 그리고, Props와 State가 변경되면  컴포넌트를 다시 그린다. 컴포넌트를 그리는 방법을 기술 하는 함수가 랜더함수이다.

## Event Handling
- HTML DOM 에 클릭하면 이벤트가 발생하고, 발생하면 그에 맞는 변경이 일어나도록 해야한다.
- JSX에 이벤트를 설정할 수 있다.
- camelCase로만 사용할 수 있다.
    - onClick, onMouseEnter
- 이벤트에 연결된 자바스크립트 코드는 함수이다.
    - 이벤트={함수} 와 같이 쓴다.
- 실제 DOM요소들에만 사용 가능하다.
    - 리액트 컴포넌트에 사용하면, 그냥 props로 전달한다.

## Component Lifecycle v16.3 이전
- 리액트 컴포넌트는 탄생부터 죽음까지 여러지점에서 개발자가 작업이 가능하도록 메서드를 오버라이딩 할 수 있게 해준다.

### componentWillReceiveProps
- props를 새로 지정했을 때 바로 호출된다.
- 여기서 state의 변경에 반응하지 않는다.
    - 여기서 props의 값에 따라 state를 변경해야 한다면,
      - setState를 이용해 state를 변경한다.
      - 그러면 다음 이벤트로 각각 가는 것이 아니라 한번에 변경된다.

### shouldComponentUpdate
- props만 변경되어도, state만 변경되어도, props & state 둘 다 변경되어도 new Props와 new State를 인자로 해서 호출   
- return type이 boolean 이다.
    - true면 render
    - false면 render가 호출되지 않는다.
    - 이 함수를 구현하지 않으면, 디폴트는 true

### componentWillUpdate
- 컴포넌트가 재 랜더링 되기 직접에 불린다.
- 여기선 setState 같은 것을 쓰면 안된다.

### componentDidUpdate
- 컴포넌트가 재 랜더링을 마치면 불린다.

### Component 언마운드

## Component Lifecycle v16.3 이후
```js
                constructor
componentWillMount => getDerivedStateFromProps로 변경
                    render
                componentDidMount

componentWillReceiveProps => getDerivedStateFromProps로 변경
                shouldCompnentUpdate 
                    render

componentWillUpdate => getSnapshotBeforeUpdate로 변경
                (dom에 적용)
                componentDidUpdate

                componentWillUnmount
```