### React를 시작하기 전 필요한 기반 지식
- [javascript-to-know-for-react](https://kentcdodds.com/blog/javascript-to-know-for-react)

  - 리액트 문법은 순수 자바스크립트 문법을 주로 사용한다.<br> 위 아티클은 리액트에서 자주 사용되는 문법들을 소개한다.
- [DOM은 무엇일까?](https://wit.nts-corp.com/2019/02/14/5522)

  - 리액트의 장점 중 하나는 DOM API 사용 최소화이다.<br/>
    프로그래밍적으로 DOM API를 사용하게 해줄 뿐만 아니라 실제 DOM API 호출 횟수를 최소화 할 수 있는 알고리즘이 적용되어 있다.<br/>
    따라서, 리액트의 내부 동작 원리 및 웹이 어떻게 동작하는지 알기 위해 DOM에 대해 미리 학습하는 것이 좋다.

### React가 만들어진 이유?

먼저 기본 자바스크립트 코드를 작성하여 DOM API를 사용해보자.

```html
<body>
  <div id="root"></div>
  <script type="module">
    const rootElement = document.getElementById('root');
    const element = document.createElement('div');
    element.textContent = 'Hello World';
    element.className = 'container';
    rootElement.append(element);
  </script>
</body>
```

최상위 엘리먼트에 하위 엘리먼트를 추가하는 간단한 구문이지만 여기에 그 이유가 담겨 있다.

- 위와 같이 엘리먼트 하나를 추가하는데 사용되는 코드들이 다섯 줄이나 되는데, 자바스크립트로 작성된 애플리케이션 규모가 점점 커지면 수 많은 코드를 작성 및 관리하기에 어려워질 것이다. <br>

  이를 위해 리액트는 선언적 프로그래밍이라고 해서 위와 같은 코드들을 사용하기 쉽게 만들어주는 JSX 문법을 제공하면서, 순수 자바스크립트 코드를 사용할 수 있는 익숙한 환경을 제공한다. 물론 DOM API를 사용하기 쉽게 만들어주는 헬퍼 함수나 JQuery 같은 라이브러리가 있지만
  리액트가 보다 구조적인 프로그래밍을 할 수 있어 직관적이고 편리하며, 다음와 같은 추가 장점이 있다. 
- 스크립트에 작성된 코드는 모두 DOM API를 사용하고 있다. => 코드 한줄당 DOM API 한번 호출<br>
  추후에 배울 가상 DOM이라는 리액트에서 만들어진 알고리즘은 동일하게 엘리먼트를 추가하는 구문이더라도 DOM API 사용을 최소화 시켜준다. 결과적으로 반복적이고 잦은 DOM API를 사용하는 페이지에서 성능상 큰 이점을 제공한다.

### Root element
최상위(root) 엘리먼트는 리액트 뿐만 아니라 다른 [SPA](https://ko.wikipedia.org/wiki/%EC%8B%B1%EA%B8%80_%ED%8E%98%EC%9D%B4%EC%A7%80_%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98) 프레임워크를 배울 때
가장 처음 접하게되는 DOM Node 이다. 최상위 엘리먼트를 기준으로 페이지의 모든 DOM Node들이 형성되고, 사용자 액션에 따른 인터랙션 및 상태 등의 컨텍스트를 갖게 된다. <br>

또한, 리액트와 같은 SPA에서의 최상위 엘리먼트 사용은 페이지 이동 없이 내부의 DOM Node를 변경하고 History API를 통한 조작으로 사용자에게 하나의 페이지에서 여러 페이지를 이동하는 것처럼 느끼게 해준다.

### Module
리액트나 서버 사이드 프로그래밍을 하면서 모듈을 자주 사용하게 되는데 개념을 한번 짚고 가면 좋을 것 같다.
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules
- https://github.com/mdn/js-examples/tree/master/module-examples 

### 참고
리액트에서 DOM API를 사용하여 실제 `createElement` 함수를 호출하는 코드는 아래에서 확인할 수 있다.
  - https://github.com/facebook/react/blob/48907797294340b6d5d8fecfbcf97edf0691888d/packages/react-dom/src/client/ReactDOMComponent.js#L416
