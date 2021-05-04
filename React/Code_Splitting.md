# Code Splitting, React lazy, Suspense

번들이 거대해지는 것을 방지하기 위한 좋은 해결방법은 번들을 '나누는' 것이다. **코드 분할** 은 런타임에 여러 번들을 동적으로 만들고 불러오는 것으로 [Webpack](https://webpack.js.org/guides/code-splitting/), [Rollup](https://rollupjs.org/guide/en/#code-splitting)과 Browserify ([factor-bundle](https://github.com/browserify/factor-bundle)) 같은 번들러가 지원하는 기능이다.

**코드 분할**

- 앱이 지연 로딩하도록 돕고, 성능을 향상한다.
- 코드를 줄이지 않고도 불필요한 코드를 불러오지 않게 하며, 앱 초기 로딩 비용을 줄인다.

### React.lazy

- React.lazy, Suspense는 아직 서버 사이드 렌더링 x
- React.lazy 함수를 사용시, 동적 import로 컴포넌트 렌더링 가능

  Before

  ```js
  import OtherComponent from "./OtherComponent";
  ```

  After

  ```js
  const OtherComponent = React.lazy(() => import("./OtherComponent"));
  ```

  - MyComponent가 처음 렌더링 될 때 OtherComponent를 포함한 번들을 자동으로 불러옴

lazy 컴포넌트

- Suspense 컴포넌트 하위에서 렌더링
- Suspense는 lazy 컴포넌트 로드을 기다리는 동안, 임시 페이지를 보여줄 수 있음

```js
import React, { Suspense } from "react";

const OtherComponent = React.lazy(() => import("./OtherComponent"));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

- fallback prop = 컴포넌트가 로드될 때까지 기다리는 동안 렌더링하려는 React 엘리먼트를 받음
- Suspense 컴포넌트는 lazy 컴포넌트를 감쌈
- Suspense 컴포넌트 하나로 여러 lazy 컴포넌트를 감쌀 수도 있음

```js
import React, { Suspense } from "react";

const OtherComponent = React.lazy(() => import("./OtherComponent"));
const AnotherComponent = React.lazy(() => import("./AnotherComponent"));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </div>
  );
}
```

### Error boundaries

Error Boundary를 만들고 + lazy 컴포넌트를 감싸면 = 네트워크 장애가 발생시 에러표시 가능

```js
import React, { Suspense } from "react";
import MyErrorBoundary from "./MyErrorBoundary";

const OtherComponent = React.lazy(() => import("./OtherComponent"));
const AnotherComponent = React.lazy(() => import("./AnotherComponent"));

const MyComponent = () => (
  <div>
    <MyErrorBoundary>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </MyErrorBoundary>
  </div>
);
```

### Route-based code splitting

React.lazy를 React Router 라이브러리를 사용해, 라우트 기반 코드 분할을 설정하는 예시

```js
import React, { Suspense, lazy } from "react";
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";

const Home = lazy(() => import("./routes/Home"));
const About = lazy(() => import("./routes/About"));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Suspense>
  </Router>
);
```

### Reference

- [공식문서](https://ko.reactjs.org/docs/code-splitting.html)<br>
- [블로그](https://velog.io/@ansrjsdn/React.lazy-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0)
