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