리액트에서 제공하는 기능을 사용하여 간단한 애플리케이션 뼈대를 만들어보겠습니다.

테스트를 위해 아래의 자바스크립트 라이브러리 파일들을 사용합니다.

```html
<script src="https://unpkg.com/react@18.1.0/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18.1.0/umd/react-dom.development.js"></script>
```

- **React** : 리액트 엘리먼트를 생성하고 다루기 위한 기본 라이브러리
- **React DOM** : 생성한 리액트 앨리먼트를 DOM에 렌더링하기 위한 라이브러리

<br>

다음은 리액트의 엘리먼트 생성 방식이 DOM API를 사용한 방식과 어떻게 다른지 비교해보겠습니다.

```js
// DOM API
const root = document.createElement('div');
const element = document.createElement('div');
element.className = 'container';
element.textContent = 'Hello World';
root.append(element);

// React
const element = React.createElement('div', { className: 'container' }, 'Hello World');
const root = React.createElement('div', {}, element);
```

최상위 엘리먼트 생성 후 자식 엘리먼트를 추가하는 코드로, 위와 같이 작성했을 때 다음과 같은 차이점이 있습니다.

- DOM API로는 하나의 동작에 한줄의 코드가 필요하지만, 리액트는 이를 객체 형태로 표현하여 코드를 간소화할 수 있습니다.<br>
  스크립트 객체 형태로 표현할 경우 간소화 뿐만 아니라 아래와 같은 이점이 있습니다.
  - 모듈화가 가능하게 되어 코드 분리에 용이해집니다.
  - 자바스크립트를 사용하는 플랫폼에서 호환이 가능합니다. DOM API로 작성할 경우 브라우저에서만 호환되지만 리액트의 경우 Native 환경에서도 호환될 수 있습니다.
- DOM API에서는 코드 한줄을 실행할 때 마다 DOM API 호출이 일어납니다. 반면 리액트에서는, 가상 DOM의 개념을 가져오면, 엘리먼트들을 스크립트 객체 형태로 모두 표현한 후 이를 최종적으로 취합해 최소한의 DOM API를 사용하여 DOM에 렌더링 합니다.

<br>

위에서 살펴본 내용은 간단한 차이점을 다룬 것이고, 리액트는 선언적 프로그래밍 기법을 토대로 이보다 더 많은 기능들을 제공하여 코드를 보다 직관적이고 편리하게 작성할 수 있도록 도움을 줍니다.

<br>

다음으로는 생성한 엘리먼트를 DOM에 렌더링 하는 코드를 작성해보겠습니다. 

```html
<script type="module">
  const rootElement = document.getElementById('root');
  const element = React.createElement('div', { className: 'container' }, 'Hello World');

  const root = ReactDOM.createRoot(rootElement); // DOM 렌더링에 기준이 되는 최상위 엘리먼트를 지정합니다.
  root.render(element); // 작성한 엘리먼트를 렌더링 합니다.
</script>
```

- React v18 버전 부터는 `ReactDOM.render` 이 아닌 `ReactDOM.createRoot().render` 형태로 변경되었습니다.
- 단 코드 몇줄로 `root.append(element)` 처럼 DOM API를 사용한 렌더링과 차이가 없어 보이지만, 실제로는 위에서 설명했던 가상 DOM을 비롯하여 리액트로 작성된 코드들을 변환해주는 기능들을 포함하고 있습니다.   
