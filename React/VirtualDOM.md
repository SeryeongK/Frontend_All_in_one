# Virtual DOM

- [Virtual DOM에 대해서 아나요?](#virtual-dom)
- [Virtual DOM을 구현하는 방법이 어떻게 되나요?](#howvirtual)
- [💡출처](#출처)

---

## <span id="virtual-dom" style='background-color: #fff5b1; color: black'>Virtual DOM에 대해서 아나요?</span>

virtual dom은 ui를 나타 낼 수 있는 dom 자체를 메모리에 가지고 있는 것이다. 이의 용도는 실제의 DOM과 비교하고 sync, 즉 동기화할 수 있게 해주는 것이다. 특히 React에서는 react elements와 관련된 개념으로 쓰이는 데, react 내에 element를 비교할 때 쓰인다.
React는 fiber라는 internal objects로 컴포넌트를 연결 하게 되는데. 이 또한 virtual dom을 구성하는 일부분이다.

## <span id="virtual-dom" style='background-color: #fff5b1; color: black'>Virtual DOM을 구현하는 방법이 어떻게 되나요?</span>

1. 구성 및 구조

```jsx
const a = (
  <ul className="list">
    <li>item 1</li>
    <li>item 2</li>
  </ul>
);
```

Tree와 같은 구조로 virtual dom을 생성할 수 있다. 보통 이렇게 ul 내부에 2개의 li가 존재하는 데, 다음과 같이 객체로 나타 낼 수 있다

```jsx
const a = {
  tag: "ul",
  children: [
    {
      tag: "li",
      children: "none",
      name: "item 1",
    },
    {
      tag: "li",
      children: "none",
      name: "item 2",
    },
  ],
};
```

실제로는 더 많은 property가 존재하겠지만, 다음과 같이 나타 낼 수 있다.

2. 기존 DOM 과의 비교
   결과적으로 비교하는 함수 `patch`같은 것을 만들어서 비교가 가능하다.
   재귀적으로 children을 타고 들어가서 DOM element에 추가 혹은 삭제 혹은 update를 시켜줄수 있는 함수가 필요하다.
   - 교체: 만약 element가 변경된 것이 있다면, 전체를 갈아낀다.
   - 삭제: 존재하던 것이 없다면, 삭제한다.
   - 생성: 존재하지 않는 element가 있으면 추가해준다.
     다음과 같은 방법을 이용해서 element를 갈아 끼워준다.

## <span id="출처" style='background-color: #fff5b1; color: black'>출처</span>

- https://legacy.reactjs.org/docs/faq-internals.html
- https://junghyunkim.tistory.com/entry/%EB%B2%88%EC%97%AD-Virtual-DOM-%EC%9D%B4-%EB%AD%94%EB%8D%B0-%ED%95%9C%EB%B2%88-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B3%B4%EA%B8%B0
