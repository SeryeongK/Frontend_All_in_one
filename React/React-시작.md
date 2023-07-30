# React 시작

- [React 시작](#react-시작)
  - [React란?](#react란)
  - [렌더링의 과정](#렌더링의-과정)
    - [Trigger a render(렌더링 촉발)](#trigger-a-render렌더링-촉발)
    - [Rendering the component(컴포넌트 렌더링)](#rendering-the-component컴포넌트-렌더링)
    - [Committing to the DOM(DOM에 커밋)](#committing-to-the-domdom에-커밋)
  - [리액트의 불변성이 필요한 이유](#리액트의-불변성이-필요한-이유)
    - [💡 출처](#-출처)

---
## <span style='background-color: #fff5b1; color: black'>React란?</span>
React는 사용자 인터페이스를 구축하기 위한 선언적이고 효율적이며 유연한 JavaScript 라이브러리이다. “컴포넌트”라고 불리는 작고 고립된 코드의 파편을 이용하여 복잡한 UI를 구성하도록 돕는다.

## <span style='background-color: #fff5b1; color: black'>렌더링의 과정</span>
### Trigger a render(렌더링 촉발)
컴포넌트 렌더링이 일어나는 데에는 두 가지 이유가 있다:
1. 컴포넌트의 첫 렌더링인 경우: 
   앱을 시작하기 위해서는 첫 렌더링을 촉발해야 한다. 프레임워크와 샌드박스가 때때로 코드를 숨기지만, 대상 DOM 노드로 `createRoot`를 호출한 다음 컴포넌트로 render 메서드를 호출하면 됩니다.
2. 컴포넌트의 state(또는 상위 요소 중 하나)가 업데이트된 경우: 컴포넌트가 처음 렌더링되면 `set(설정자)` 함수로 state를 업데이트하여 추가 렌더링을 촉발시킬 수 있다. 컴포넌트의 state를 업데이트하면 자동으로 렌더링이 대기열에 추가된다.
### Rendering the component(컴포넌트 렌더링)
렌더링을 촉발시키면, React는 컴포넌트를 호출하여 화면에 표시할 내용을 파악한다. **렌더링**은 React에서 컴포넌트를 호출하는 것이다.
- 첫 렌더링에서 React는 루트 컴포넌트를 호출한다.
- 이후 렌더링에서 React는 state 업데이트에 의해 렌더링이 발동된 함수 컴포넌트를 호출한다.

### Committing to the DOM(DOM에 커밋)
컴포넌트를 렌더링(호출)한 후 React는 DOM을 수정한다. 
- 초기 렌더링의 경우 React는 `appendChild()` DOM API를 사용하여 생성한 모든 DOM 노드를 화면에 표시한다.
- 리렌더링의 경우 React는 필요한 최소한의 작업(렌더링하는 동안 계산된 것!)을 적용하여 DOM이 최신 렌더링 출력과 일치하도록 한다.

## <span style='background-color: #fff5b1; color: black'>리액트의 불변성이 필요한 이유</span>
일반적으로 데이터 변경에는 두 가지 방법이 있다. 첫 번째는 데이터의 값을 직접 변경하는 것이다. 두 번째는 원하는 변경 값을 가진 새로운 사본으로 데이터를 교체하는 것이다.
- 복잡한 특징들을 **단순**하게 만든다. 이전 버전을 유지하고 나중에 재사용할 수 있게 한다.
- **변화를 감지**한다. 객체가 직접적으로 수정되기 때문에 복제가 가능한 객체에서 변화를 감지하는 것은 어렵다. 감지는 복제가 가능한 객체를 이전 사본과 비교하고 전체 객체 트리를 돌아야 한다.
하지만 불변 객체에서 변화를 감지하는 것은 상당히 쉽다. 참조하고 있는 불변 객체가 이전 객체와 다르다면 객체는 변한 것이다.
- React에서 **다시 렌더링하는 시기**를 결정한다. 불변성의 가장 큰 장점은 React에서 순수 컴포넌트를 만드는 데 도움을 준다는 것이다. 변하지 않는 데이터는 변경이 이루어졌는지 쉽게 판단할 수 있으며 이를 바탕으로 컴포넌트가 다시 렌더링할지를 결정할 수 있다.

---
### 💡 출처
- https://ko.legacy.reactjs.org/
- https://react-ko.dev/learn/render-and-commit