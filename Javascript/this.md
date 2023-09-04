# this

- [this](#this)
  - [this가 뭔가요?](#this가-뭔가요)
  - [this 바인딩이란?](#this-바인딩이란)
  - [this는 동적으로 바인딩이 된다고 하는데 바인딩되는 객체가 어떻게 다르나요?](#this는-동적으로-바인딩이-된다고-하는데-바인딩되는-객체가-어떻게-다르나요)

## <span style='background-color: #fff5b1; color: black'>this가 뭔가요?</span>

this는 실행 컨텍스트에 따라 동적으로 결정되는 특별한 키워드입니다.</br>
this는 현재 실행되는 함수나 메서드 내에서 참조하는 객체를 가리키는 역할을 합니다. 함수가 호출될 때마다 this의 값이 달라질 수 있습니다.

## <span style='background-color: #fff5b1; color: black'>this 바인딩이란?</span>

함수나 메서드 내에서 `this`의 값은 호출되는 방법에 따라 동적으로 결정됩니다. 이를 <span style='font-weight: bold; color: tomato'>this 바인딩</span> 이라고 합니다. `this`의 값은 함수를 호출하는 방식과 위치에 따라 달라집니다. 일반적으로 다음과 같은 규칙에 따라 `this`가 바인딩됩니다:

1. **전역 컨텍스트에서의 `this`:** 전역 스코프에서 실행되는 코드 내에서 `this`는 전역 객체를 가리킵니다. 브라우저 환경에서는 **`window`** 객체가 전역 객체입니다.
2. **함수 호출에서의 `this`:** 일반 함수 내에서 `this`는 해당 함수를 호출한 주체에 따라 결정됩니다. 함수 호출 시 사용된 방법에 따라 다르게 바인딩됩니다.

   - 함수를 일반적인 방식으로 호출하면 (**`functionName()`**), `this`는 전역 객체를 가리킵니다.
   - 메서드로서 객체 내에서 호출하면 (**`object.method()`**), `this`는 해당 객체를 가리킵니다.
     </br></br>

3. **화살표 함수에서의 `this`:** 화살표 함수 내에서 `this`는 함수가 생성될 때의 상위 스코프에서 상속됩니다. 즉, 화살표 함수 내에서 **`this`**는 함수가 정의된 곳의 `this`를 가리킵니다.

## <span style='background-color: #fff5b1; color: black'>this는 동적으로 바인딩이 된다고 하는데 바인딩되는 객체가 어떻게 다르나요?</span>

`this`가 어떤 객체를 가리키는지는 함수를 어떻게 호출했느냐에 따라 다릅니다. 예를 들어:

```jsx
var person = {
  name: "John",
  greet: function () {
    console.log(`Hello, my name is ${this.name}`);
  },
};

person.greet(); // this는 person 객체를 가리킴 Hello, my name is John

var greetFunction = person.greet;
greetFunction(); // this는 전역 객체를 가리킴 (브라우저에서는 window) Hello, my name is
```

위 예시에서 **`person.greet()`**를 호출하면 **`this`**는 **`person`** 객체를 가리키며, **`greetFunction()`**을 호출하면 **`this`**는 전역 객체를 가리킵니다.

이처럼 **`this`**의 바인딩은 함수 호출의 맥락에 따라 달라지며, 함수가 어떻게 호출되었는지에 따라 결정됩니다.

| 함수 호출 방식                                             | this 바인딩                                                            |
| ---------------------------------------------------------- | ---------------------------------------------------------------------- |
| 일반 함수 호출                                             | 전역 객체(window/ global)                                              |
| 콜백 함수 호출                                             | 전역 객체(window/ global)                                              |
| 내부 함수 호출                                             | 전역 객체(window/ global)                                              |
| 메서드 호출                                                | 메서드를 호출한 객체                                                   |
| 생성자 함수 호출                                           | 생성자 함수가 (미래에) 생성할 인스턴스                                 |
| Function.prototype.apply/call/bind 메서드에 의한 간접 호출 | Function.prototype.apply/call/bind 메서드에 첫 번째 인수로 전달한 객체 |
