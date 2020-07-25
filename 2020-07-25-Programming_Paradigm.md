# Programming Paradigm

- 명령형
    - 상태와 상태를 변경시키는 구문의 관점에서 연산 설명, 알고리즘 명시하며 목표는 명시하지 않음
    - 절차지향
        - 수행될 연속적(Continuous)인 계산 과정을 포함하는 방식
            - e.g. C, C++
    - 객체지향
        - 객체들의 집합으로 이들 간의 상호작용(Inter-communication)을 표현
            - e.g. C++, Java, C#
- 선언형
    - 행동적 관점 (How)보다 선언적 관점(What)을 설명, 알고리즘 명시 없이 목표 명시
    - 함수형
        - 순수 함수를 조합
            - e.g. Closure, Haskell, Lisp



## Comparison

- 선언형 HTML

    ```html
    <article>
    	<header>
      	<h1>
          Declarative
        </h1>
        <p>
          Sprinkle Declarative in your verbiage to sound smart
        </p>
      </header>
    </article>
    ```

- 명령형 / 선언형 Javascript 비교

    ```javascript
    // 명령형
    function double (arr) {
      let results = []
      for (let i = 0; i < arr.length; i++) {
        results.push(arr[i] * 2)
      }
      return results
    }
    
    function add (arr) {
      let result = 0
      for (let i = 0; i < arr.length; i++) {
        result += arr[i]
      }
      return result
    }
    
    $("#btn").click(function () {
      $(this).toggleClass("highlight")
      $(this).text() === 'Add Highlight' ? $(this).text("Remove Highlight") : $(this).text('Add Highlight')
    })
    
    // 선언형
    function double (arr) {
      return arr.map((item) => item * 2)
    }
    
    function add (arr) {
      return arr.reduce((prev, current) => prev + current, 0)
    }
    
    <Btn
    	onToggleHighlight={this.handleToggleHighlight}
    	hightlight={this.state.highlight}>
    	{this.state.buttonText}
    </Btn>
    ```

![Comparison](https://user-images.githubusercontent.com/6733004/46571789-717c4300-c9b6-11e8-82f4-1dee07108e98.jpg)

---

> 함수형 프로그래밍은 계산을 수학적 함수의 조합으로 생각하는 방식을 의미하며, 이것은 일반적인 프로그래밍 언어에서 함수가 특정 동작을 수행하는 역할을 담당하는 것과 반대되는 개념으로 함수를 수행해도 함수 외부의 값이 변경될 수 없다.

---

### Concepts in Functional Programming

#### First Object

- 다음 조건을 만족하는 객체

    - 변수, 데이터 구조 안에 담을 수 있다.
    - 파라미터로 전달할 수 있다.
    - 반환값으로 사용 가능하다.
    - 할당에 사용된 이름과 무관하게 고유한 구별이 가능하다.
    - 동적으로 프로퍼티 할당이 가능하다.

    > Javascript에서 function은 object 이므로 `First Function`으로 불린다.

#### High-order Function

- Lambda 계산법에서 만들어진 용어로 아래 조건을 만족하는 함수

    - 함수에 함수를 파라미터로 전달 가능
    - 함수의 반환값으로 함수 사용 가능

    > `First Function`의 Subset.
    >
    > React의 HOC는 컴포넌트를 사용해 위 조건을 만족하는 컴포넌트

#### Immutability

- 함수형 프로그래밍에서 데이터가 변할 수 없음을 의미 (자바스크립트는 가능하나 불가능한 언어들이 존재)

- 데이터 변경 필요시 원본 데이터 구조 변경없이 데이터 복사본을 만들어 그 일부를 변경하고, 변경한 복사본을 사용해 작업 진행

    ```javascript
    // Mutable Data
    function rateColor(color, rating) {
      color.rating = rating
      return color
    }
    
    console.log(rateColor(color_lawn, 5), rating) // 5
    console.log(color_lawn.rating) // 5
    
    // Immutable Data
    function rateColor(color, rating) {
      return Object.assign({}, color, { rating: rating })
    }
    
    console.log(rateColor(color_lawn, 5), rating) // 5
    console.log(color_lawn.rating) // 0
    ```

    > `const`와 Immutability는 구분해야함. `const`는 `Object`로 사용되는 경우 Mutable 함

#### Pure Function

- 함수형 프로그래밍에 필요한 개념으로 아래 조건을 만족해야함

    - 동일한 입력에는 항상 동일한 값을 반환해야함
    - 함수의 실행은 프로그램 실행에 영향을 미치지 않아야 함 (No side-effect)
        - e.g. 함수 내부에서 인자 값 변경하거나 프로그램 상태를 변경하는 것

    > 순수 함수를 호출하면 프로그램의 어떠한 변화가 없으며, 입력 값에 대한 결과를 예상할 수 있어서 테스트하기 쉬움

    ```javascript
    // Function not pure, side effect occurred (DOM modified)
    function header(text) {
      let h1 = document.createElement('h1')
      h1.innerText = text
      document.body.appendChild(h1)
    }
    
    // Pure function, no side effect occurred
    // Other part takes obligation for modifying DOM
    const header = (props) => <h1>{props.title}</h1>
    ```

#### Data Conversion

- 데이터 변경이 불가능하므로 기존 데이터 복사본을 생성하는 도구 필요
- 자바스크립트의 경우 `Array.map`, `Array.reduce`등의 함수 통해 데이터 복사본 생성

#### Function composition

- 새로운 함수 생성하거나 계산하기 위해 둘 이상의 함수를 조합하는 과정

```javascript
const sum = (a, b) => a + b
const square = x => x * x
const addTen = x => x + 10

const computeNum = addTen(square(sum(3, 5)))

// compose will return value calling functions continuously
const compose = (...fns) =>
	fns.reduce((prevFn, nextFn) =>
  	(...args) => nextFn(prevFn(...args)),
    value => value
  )

const compute = compose(addTen, square, sum)
compute(3, 5)
```



> 함수형 프로그래밍은 **순수 함수를 조합, 공유 상태, 변경 가능한 데이터 및 부작용을 피해 소프트웨어를 만드는 프로세스. 명령형이 아닌 선언형이며 애플리케이션의 상태는 순수 함수를 통해 전달됨**