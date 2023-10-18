# class

- [class](#class)
  - [자바스크립트에서 클래스가 생기기 전에는 어떤 방식으로 객체지향 패턴을 구현했나요?](#자바스크립트에서-클래스가-생기기-전에는-어떤-방식으로-객체지향-패턴을-구현했나요)
  - [그럼 생성자 함수와 클래스는 어떤 차이가 있나요?](#그럼-생성자-함수와-클래스는-어떤-차이가-있나요)
  - [클래스 정의](#클래스-정의)

## <span style='background-color: #fff5b1; color: black' id='meta0'>자바스크립트에서 클래스가 생기기 전에는 어떤 방식으로 객체지향 패턴을 구현했나요?</span>

자바스크립트에서 클래스가 도입되기 전에는 객체지향 프로그래밍을 구현하기 위해 프로토타입 기반 패턴을 사용했습니다. 이러한 패턴은 아직도 일부 경우에 유용하게 사용됩니다. 아래는 프로토타입 기반 패턴의 주요 특징과 예시입니다:

- **프로토타입 객체**: 객체 생성자(Constructor) 함수에서 생성된 객체는 프로토타입 객체(Prototype Object)를 가집니다. 이 프로토타입 객체는 해당 생성자 함수로 생성된 모든 객체가 상속할 메서드와 속성을 정의합니다.

```jsx
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Person 생성자 함수의 프로토타입에 메서드 추가
Person.prototype.sayHello = function () {
  console.log(`안녕, 나는 ${this.name}이고, ${this.age}살이야.`);
};

// 객체 생성
const person1 = new Person("Alice", 25);
const person2 = new Person("Bob", 30);

// 메서드 호출
person1.sayHello(); // 출력: 안녕, 나는 Alice이고, 25살이야.
person2.sayHello(); // 출력: 안녕, 나는 Bob이고, 30살이야.
```

- **상속**: 프로토타입 기반 패턴을 사용하여 객체 사이에 상속 관계를 설정할 수 있습니다. 즉, 한 객체의 프로토타입을 다른 객체로 설정하여 메서드와 속성을 공유할 수 있습니다.

```jsx
function Student(name, age, grade) {
  Person.call(this, name, age); // 부모 클래스(Person)의 생성자 호출
  this.grade = grade;
}

// 상속 설정
Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

// 자식 클래스(Student)의 메서드 추가
Student.prototype.study = function () {
  console.log(
    `${this.name}은(는) ${this.grade}학년 학생으로 열심히 공부합니다.`
  );
};

const student1 = new Student("Eve", 18, 12);
student1.sayHello(); // Person 클래스의 메서드 호출
student1.study(); // Student 클래스의 메서드 호출
```

프로토타입 기반 패턴은 ES6에서 클래스 문법이 도입되기 전까지 주요한 객체지향 프로그래밍 방법 중 하나였습니다. ES6에서 클래스 문법이 도입되면서 클래스 기반의 객체지향 프로그래밍도 편리하게 사용할 수 있게 되었습니다.

## <span style='background-color: #fff5b1; color: black' id='meta0'>그럼 생성자 함수와 클래스는 어떤 차이가 있나요?</span>

1.  **구문 및 가독성**:
    클래스는 ES6에서 도입되었으며, 생성자 함수보다 더 간결하고 명확한 문법을 제공합니다. 클래스는 **`class`** 키워드를 사용하여 정의되며 new 연산자 없이 호출이 불가능 하고,
    생성자 함수는 **`function`** 키워드를 사용하고 일반 함수처럼 호출한다.

```
// 생성자 함수
function Person(name) {
this.name = name;
}

    // 클래스
    class Person {
      constructor(name) {
        this.name = name;
      }
    }
```

1.  **메서드 정의**:
    클래스 내에서 메서드를 정의할 때 추가적인 **`function`** 키워드를 사용할 필요 없이 메서드 이름만 작성할 수 있습니다.
    `` jsx
class Person {
sayHello() {
console.log(`안녕, 나는 ${this.name}이야.`);
}
} ``
1.  **상속**:
    클래스는 내장된 상속 메커니즘 ( extends, super ) 을 지원하여 상속 관계를 쉽게 설정할 수 있습니다.
    생성자 함수를 사용할 때는 수동으로 프로토타입 체인을 설정해야 합니다.

1.  Strict Mode
    클래스 내의 모든 코드에는 암묵적으로 strict mode가 저장되어 실행되며 strict mode를 해제할 수 없다.
    생성자 함수는 암묵적으로 strict mode가 지정되지 않는다.
1.  호이스팅
    클래스는 호이스팅이 발생하지 않는 것처럼 동작한다. 하지만 함수 선언문으로 작성된 클래스는 함수 호이스팅이, 함수 표현식으로 정의한 생성자 함수는 변수 호이스팅이 발생한다.

## <span style='background-color: #fff5b1; color: black' id='meta0'>클래스 정의</span>

클래스는 객체지향 프로그래밍(OOP)에서 사용되며, 특정 객체 유형의 모델을 정의하는데 사용됩니다.
class 키워드를 사용하여 정의
클래스 이름은 성성자 함수와 마찬가지로 파스칼 케이스를 사용하는 것이 일반적이다. 파스칼 케이스를 사용하지 않아도 에러가 발생하지는 않는다.

```jsx
class ClassName {
  // 생성자 메서드 (constructor)
  constructor(param1, param2, ...) {
    // 속성 정의
    this.property1 = param1;
    this.property2 = param2;
    // ...
  }

  // 메서드 정의
  methodName1() {
    // 메서드 내용
  }

  methodName2() {
    // 메서드 내용
  }

  // ...
```

- 클래스의 상속
  클래스 상속(Class Inheritance)은 코드 재사용 관점에서 매우 유용하다. 새롭게 정의할 클래스가 기존에 있는 클래스와 매우 유사하다면, 상속을 통해 그대로 사용하되 다른 점만 구현하면 된다. 코드 재사용은 개발 비용을 현저히 줄일 수 있는 잠재력이 있으므로 매우 중요하다.
  **extends** 키워드는 부모 클래스(base class)를 상속받는 자식 클래스(sub class)를 정의할 때 사용
  **오버라이딩(Overriding)**
  상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의하여 사용하는 방식이다.
  **오버로딩(Overloading)**
  매개변수의 타입 또는 갯수가 다른, 같은 이름의 메소드를 구현하고 매개변수에 의해 메소드를 구별하여 호출하는 방식이다. 자바스크립트는 오버로딩을 지원하지 않지만 arguments 객체를 사용하여 구현할 수는 있다.
  ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e0646d00-37dc-4b71-8e17-885fad4ea039/7d2c0546-b1cc-4b57-8342-adeecea7406e/Untitled.png)
  **super 키워드는 부모 클래스를 참조(Reference)할 때 또는 부모 클래스의 constructor를 호출할 때 사용한다.**

  ```jsx
  // 부모 클래스
  class Circle {
  ...
  }

  class Cylinder extends Circle {
    constructor(radius, height) {
      // ① super 메소드는 부모 클래스의 constructor를 호출하면서 인수를 전달한다.
      super(radius);
      this.height = height;
    }

    // 원통의 넓이: 부모 클래스의 getArea 메소드를 오버라이딩하였다.
    getArea() {
      // (원통의 높이 * 원의 둘레) + (2 * 원의 넓이)
      // ② super 키워드는 부모 클래스(Base Class)에 대한 참조
      return (this.height * super.getPerimeter()) + (2 * super.getArea());
    }

    // 원통의 부피
    getVolume() {
      // ② super 키워드는 부모 클래스(Base Class)에 대한 참조
      return super.getArea() * this.height;
    }
  }

  // 반지름이 2, 높이가 10인 원통
  const cylinder = new Cylinder(2, 10);
  ```

  ① super 메소드는 자식 class의 constructor 내부에서 부모 클래스의 constructor(super-constructor)를 호출한다. 즉, 부모 클래스의 인스턴스를 생성한다. **자식 클래스의 constructor에서 super()를 호출하지 않으면 this에 대한 참조 에러(ReferenceError)가 발생한다.**

  ```jsx
  class Parent {}

  class Child extends Parent {
    // ReferenceError: Must call super constructor in derived class before accessing 'this' or returning from derived constructor
    constructor() {}
  }

  const child = new Child();
  ```

  **이것은 super 메소드를 호출하기 이전에는 this를 참조할 수 없음을 의미한다.**
  ② super 키워드는 부모 클래스(Base Class)에 대한 참조이다. 부모 클래스의 필드 또는 메소드를 참조하기 위해 사용한다.
  **static 메소드와 prototype 메소드의 상속**
  프로토타입 관점에서 바라보면 자식 클래스의 [[Prototype]] 내부 슬롯이 가리키는 프로토타입 객체는 부모 클래스이다.
  ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e0646d00-37dc-4b71-8e17-885fad4ea039/2e0f4b18-7d75-42bb-875a-64f27a89694d/Untitled.png)
  상속을 사용하면 부모 클래스의 속성과 메서드를 자식 클래스에서 사용할 수 있으며, 자식 클래스에서 추가적인 속성과 메서드를 정의할 수 있습니다. **`super`** 키워드를 사용하여 부모 클래스의 생성자를 호출하고, **`extends`** 키워드로 상속 관계를 설정합니다.
