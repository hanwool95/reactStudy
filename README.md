https://www.udemy.com/course/best-react/
react 완벽 가이드 강의 요약


# Section1

리액트는 무엇인가?

- 사용자 인터페이스 만드는 자바스크립트 라이브러리
- 왜 자바스크립트보다 리액트가 도움이 되는 것?
- Request Response Cycle를 생각해봐야 함.

js로 작업하면 일일히 다 설명되고 작업해야 함. (멸영형 접근 방식)

하지만 리액트

- 유지보수 쉽게 만들어줌.
- 복잡한 인터페이스를 쉽게 구축하게 해 줌.

SPA!

물론 다른 프레임워크도 있다는 것 생각해야 해.

- 앵귤러: 컴포넌트 기반 프레임워크. 타입스크립트 수용. 프레임워크에 많은 기능이 있어 대형 어플에 적합함.
- 뷰: 앵귤러와 리액트 사이임. 컴포넌트 기반. 앵귤러보다는 적고 리액트보다는 많음. 라우팅 같은 핵심 기능 있음.
# React 기초

- 리액트를 사용하는 것은 사용자 인터페이스를 간단히 만들 수 있기 때문!

### 컴포넌트

리액트 = 컴포넌트

모든 사용자 인터페이스는 컴포넌트로 구성됨!

그럼 컴포넌트가 뭐야?

- 재사용 가능 ⇒ 반복 하지 않음
- 관심사 분리 ⇒ 관리 쉬움

리액트에서 물러나 프로그래밍 어떤 언어든, 함수를 사용하고 관심사를 분리하는 것 처럼, 앱 어플리케이션 관점에서 수행하는 것.

그럼 컴포넌트 어떻게 만들어져?

- HTML, CSS, JS를 결합해서 React 컴포넌트를 제작함
- 리액트는 선언적 방식을 사용함
- 목표 상태를 정의!
    - 최종상태에 어떤 상태가 사용되어야 하는지 정의

### Create React App

쉽게 시작하고, 개발과정 단순화 시키고 최적화해줌

`npx create-react-app my-app`

```tsx
// index.js
import ReactDOM from 'react-dom/client';

import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

root object가 리액트에게 어떤 것이 루트인지 알려주고, 어떤 엘리먼트를 가져올지 알려줄 수 있어.

index.htmldml id root의 div태그가 이 App이 되는 것임.

그러면 이 App은  뭐야? 컴포넌트. 첫 번째로 사용하는 컴포넌트~~~!!

```tsx
// App.js

function App() {
  return (
    <div>
      <h2>Let's get started!</h2>
    </div>
  );
}

export default App;
```

JSX라는 리액트의 특수 구문 덕분에 작동.

### JSX

JSX는 뭐야? 자바스크립트의 XML이야.

static/js 안에 코드들을 볼 수 있음.

전체 리액트 라이브러리 소스를 보면. (main.chunk.js 등) 브라우저에서 우리가 작성한 JSX가 변환되어서 사용 됨. 리액트는 JSX가 자동적으로 화면 뒷단에서 브라우저에 사용되도록 변경함.

### Custom Component 실습

```tsx
function App() {
  return (
    <div>
      <h2>Let's get started!</h2>
      <p>This is also visible!</p>
    </div>
  );
}

export default App;
```

컴포넌트는 custom HTML일 뿐.

리액트는 DOM 지시사항을 생성하는 역할을 함.

일반 자바스크립트는 명령형 구조 ⇒ 복잡함.

리액트는 최종상태 지정한 하면, 리액트가 알아서 뒷단에서 생성해줌.

```tsx
// components/ExpenseItem.js

function ExpenseItem() {
  return <h2>Expense item!</h2>;
}

export default ExpenseItem;
```

리액트 컴포넌트 관례.

첫 단어는 대문자, 그다음 단어 첫 단어 대문자.

컴포넌트는 단지 함수 일 뿐!

```tsx
import ExpenseItem from "./components/ExpenseItem";

function App() {
  return (
    <div>
      <h2>Let's get started!</h2>
      <p>This is also visible!</p>
      <ExpenseItem></ExpenseItem>
    </div>
  );
}

export default App;
```

Custom Component export 한 것을 재사용 가능.

```tsx
// components/ExpenseItem.js

function ExpenseItem() {
  return (
    <div>
      <div>March 28th 2021</div>
      <div>
        <h2>Car Insurance</h2>
        <div>$294.67</div>
      </div>
    </div>
  );
}
export default ExpenseItem;
```

리액트 컴포넌트 중요한 규칙.

반드시 하나의 루트 요소를 가져야 한다는 것!

div 태그가 여러개 나열되는 것 같은 두 개 이상의 루트를 허용하지 않음.

가독성을 위해서 괄호로 감싸서 하나의 코드라는 것을 알려주고 오토 포맷으로 가독성을 높일 수 있음.

### Css 추가

```css
/*ExpenseItem.css*/

.expense-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
    padding: 0.5rem;
    margin: 1rem 0;
    border-radius: 12px;
    background-color: #4b4b4b;
}

.expense-item__description {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    align-items: flex-end;
    flex-flow: column-reverse;
    justify-content: flex-start;
    flex: 1;
}

.expense-item h2 {
    color: #3a3a3a;
    font-size: 1rem;
    flex: 1;
    margin: 0 1rem;
    color: white;
}

.expense-item__price {
    font-size: 1rem;
    font-weight: bold;
    color: white;
    background-color: #40005d;
    border: 1px solid white;
    padding: 0.5rem;
    border-radius: 12px;
}

@media (min-width: 580px) {
    .expense-item__description {
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
        flex: 1;
    }

    .expense-item__description h2 {
        font-size: 1.25rem;
    }

    .expense-item__price {
        font-size: 1.25rem;
        padding: 0.5rem 1.5rem;
    }
}
```

```tsx
// components/ExpenseItem.js

import "./ExpenseItem.css";

function ExpenseItem() {
  return (
    <div className={"expense-item"}>
      <div>March 28th 2021</div>
      <div className={"expense-item__description"}>
        <h2>Car Insurance</h2>
        <div className={"expense-item__price"}>$294.67</div>
      </div>
    </div>
  );
}
export default ExpenseItem;
```

css가 응용 프로그램에 삽입되도록 알려야 함.

그리고 css에서 지정한 class 추가해야 함.

jsx에서는 class가 아니라 className으로 class를 정의.(이건 html 코드가 아니라 자바스크립트 코드라는 것을 생각해야 함!)

### JSX 동적 데이터

```tsx
// components/ExpenseItem.js

import "./ExpenseItem.css";

function ExpenseItem() {
  const expenseDate = new Date(2021, 2, 28);
  const expenseTitle = "Car Insurance";
  const expenseAmount = 294.67;

  return (
    <div className={"expense-item"}>
      <div>{expenseDate.toISOString()}</div>
      <div className={"expense-item__description"}>
        <h2>{expenseTitle}</h2>
        <div className={"expense-item__price"}>${expenseAmount}</div>
      </div>
    </div>
  );
}
export default ExpenseItem;
```

JSX 코드 안에 특별한 리액트 코드를 사용하여 동적 데이터 사용

- 중괄호! {}
- 중괄호 안은 결과 값이 출력되는 것.

### Props

```tsx
import ExpenseItem from "./components/ExpenseItem";

function App() {
  const expenses = [
    {
      id: 21,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
    {
      id: 22,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
    {
      id: 23,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
    {
      id: 24,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
  ];

  return (
    <div>
      <h2>Let's get started!</h2>
      <p>This is also visible!</p>
      <ExpenseItem
        title={expenses[0].title}
        amount={expenses[0].amount}
        date={expenses[0].date}
      />
      <ExpenseItem
        title={expenses[1].title}
        amount={expenses[1].amount}
        date={expenses[1].date}
      />
      <ExpenseItem
        title={expenses[2].title}
        amount={expenses[2].amount}
        date={expenses[2].date}
      />
      <ExpenseItem
        title={expenses[3].title}
        amount={expenses[3].amount}
        date={expenses[3].date}
      />
    </div>
  );
}

export default App;
```

js에서 매개변수를 받아서 재사용할 수 있는 것처럼 리액트도 동일한 개념이 탑재되어 있음!

props 개념을 이용하여 컴포넌트 재사용.

단순히 컴포넌트 정의할 때 key를 넣고 중괄호 안에 값을 넣을 수 있으며, 컴포넌트 파라미터로 꺼내올 수 있음.

```tsx
// components/ExpenseItem.js

import "./ExpenseItem.css";

function ExpenseItem(props) {
  return (
    <div className={"expense-item"}>
      <div>{props.date.toISOString()}</div>
      <div className={"expense-item__description"}>
        <h2>{props.title}</h2>
        <div className={"expense-item__price"}>${props.amount}</div>
      </div>
    </div>
  );
}
export default ExpenseItem;
```

props object 안에 key가 할당이 됨.

```tsx
// components/ExpenseItem.js

import "./ExpenseItem.css";

function ExpenseItem(props) {
  const month = props.date.toLocaleString("en-US", { month: "long" });
  const day = props.date.toLocaleString("en-US", { day: "2-digit" });
  const year = props.date.getFullYear();

  return (
    <div className={"expense-item"}>
      <div>{month}</div>
      <div>{year}</div>
      <div>{day}</div>
      <div className={"expense-item__description"}>
        <h2>{props.title}</h2>
        <div className={"expense-item__price"}>${props.amount}</div>
      </div>
    </div>
  );
}
export default ExpenseItem;
```

props를 컴포넌트 안에서 변형과 가공도 가능.

위의 예시는 date 객체를 이용한 가공.

```tsx
// components/ExpenseItem.js

import "./ExpenseItem.css";
import ExpenseDate from "./EspenseDate";

function ExpenseItem(props) {
  return (
    <div className={"expense-item"}>
      <div className={"expense-item__description"}>
        <ExpenseDate date={props.date} />
        <h2>{props.title}</h2>
        <div className={"expense-item__price"}>${props.amount}</div>
      </div>
    </div>
  );
}
export default ExpenseItem;
```

```tsx
// components/ExpenseDate.js

function ExpenseDate(props) {
  const month = props.date.toLocaleString("en-US", { month: "long" });
  const day = props.date.toLocaleString("en-US", { day: "2-digit" });
  const year = props.date.getFullYear();

  return (
    <div>
      <div>{month}</div>
      <div>{year}</div>
      <div>{day}</div>
    </div>
  );
}

export default ExpenseDate;
```

컴포넌트를 분리해서 재사용 가능. 똑같이 props를 원하는 것을 내려 보낼 수 있음.


### 컴포넌트 실습 정답

```tsx
// components/Expenses.js

import ExpenseItem from "./ExpenseItem";
import "./ExpenseItem.css";

function Expenses(props) {
  return (
    <div className={"expenses"}>
      <ExpenseItem
        title={props.items[0].title}
        amount={props.items[0].amount}
        date={props.items[0].date}
      />
      <ExpenseItem
        title={props.items[1].title}
        amount={props.items[1].amount}
        date={props.items[1].date}
      />
      <ExpenseItem
        title={props.items[2].title}
        amount={props.items[2].amount}
        date={props.items[2].date}
      />
      <ExpenseItem
        title={props.items[3].title}
        amount={props.items[3].amount}
        date={props.items[3].date}
      />
    </div>
  );
}

export default Expenses;
```

```tsx
// App.js

import Expenses from "./components/Expenses";

function App() {
  const expenses = [
    {
      id: 21,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
    {
      id: 22,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
    {
      id: 23,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
    {
      id: 24,
      title: "Car Insurance",
      amount: 294.67,
      date: new Date(2021, 2, 28),
    },
  ];

  return (
    <div>
      <h2>Let's get started!</h2>
      <Expenses items={expenses} />
    </div>
  );
}

export default App;
```

### 컴포지션 & children

컴포지션: 작은 빌딩 블록으로 인터페이스 구축하는 것

- 컴포넌트들은 props로 재설정 됨
- 컴포넌트 열고 닫는 사이의 콘텐츠에 전달하고 싶을 경우! `children`

```tsx
// components/ExpenseItem.js

import "./ExpenseItem.css";
import ExpenseDate from "./EspenseDate";
import Card from "./Card";

function ExpenseItem(props) {
  return (
    <Card className={"expense-item"}>
      <div className={"expense-item__description"}>
        <ExpenseDate date={props.date} />
        <h2>{props.title}</h2>
        <div className={"expense-item__price"}>${props.amount}</div>
      </div>
    </Card>
  );
}
export default ExpenseItem;
```

shell 역할을 하는 Card 컴포넌트 제작

하지만 그냥 감싸서는 안의 컴포넌트들을 소실함.

```tsx
import "./Card.css";

function Card(props) {
  return <div className={"card"}>{props.children}</div>;
}

export default Card;
```

모든 리액트 컴포넌트가 갖는 특수한 props `children`

Card 사이의 컴포넌트들은 children props 안에 들어가게 됨

이렇게 래퍼 컴포넌트를 만들어서, 일부 중복된 코드들을 추출할 수 있음

### JSX

JSX 자체는 브라우저에서 지원하지 않고, 리액트가 변환해서 브라우저에 전달하는 것.

브라우저에서 청크 파일 확인하면 복잡한 JSX 확인 가능. 하지만 이것은 가독성이 당연히 안 좋음.

화면 뒷단에서는 변환이 이루어지고 있음. package.json에서 react import 하지 않아. 오래된 버전에서는 react import 해야 했지만, 지금은 하지 않음. JSX 코드는 react 라이브러리에서 변환시킴.

`React.createElement`가 return하는 과정에서 call되는 것임.

```tsx
return React.create('div', {},
				React.createElement('h2', {}, "Let's get started!"),
				React.createElement(Expenses, {items: expenses})
	);

return (
    <div>
      <h2>Let's get started!</h2>
      <Expenses items={expenses} />
    </div>
  );
```

첫 인자는 어떤 태그의 요소인지 전달해주고, 두 번째는 요소를 설정하는 attribute. 세 번째 인자 부터는 div 안에 있는 element 들.

- 그래서 return 안에 root element 두 개 이상을 가질 수 없었던 것!!

### 파일 정리

프로젝트 진행되어서 파일 많아지면, 정리가 필요.

UI나 User 컴포넌트, 특정 기능만 갖는 컴포넌트 등이 있어.

components의 하위 폴더로 Expenses, UI 등 만들고 각각 을 배치할 수도 있어.

### 대체 함수

화살표 함수도 사용 가능.

```tsx
function App() {}

const App2 = () => {}

```