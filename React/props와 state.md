# props와 state

props
- 받은 데이터 이거나 생성된 데이터, 즉 데이터의 기원이 자기 자신이 아닌 것
- 컴포넌트는 상속하는 부모 컴포넌트로 부터 props 를 받음
- props 는 상속받는 컴포넌트 내에서 수정이 불가능


state
- 현재 컴포넌트에서 생성, 변할 수 있는 데이터 
- 오직 state가 생성된 컴포넌트 내에서만 변경이 가능
- state 는 외부에 공개하지 않고 컴포넌트가 스스로 관리
- 컴포넌트의 상태값을 나타내기 위한 것들 ( 리스트에서 선택된값 , 체크박스에서 체크된 값, 텍스트 박스의 텍스트 등등)
- state 가 변경되면 컴포넌트를 다시 렌더링 해야 함


\* 자식 컴포넌트에서 부모 컴포넌트로 전달하는 방법?
직접 props를 보낼 수는 없다. 자식 컴포넌트에 콜백 함수를 props로 전달하고, 자식 컴포넌트는 해당 콜백 함수를 실행하여 부모 컴포넌트에 정보를 전달하거나 부모 컴포넌트의 상태를 변경할 수 있다.

### 💡 출처
- https://ljh86029926.gitbook.io/coding-apple-react/1/props-and-state
- [https://velog.io/@s2s2hyun/React.state-props-하는일과-차이점](https://velog.io/@s2s2hyun/React.state-props-%ED%95%98%EB%8A%94%EC%9D%BC%EA%B3%BC-%EC%B0%A8%EC%9D%B4%EC%A0%90)