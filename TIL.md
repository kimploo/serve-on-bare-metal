# TIL

## TIL 2025-02-01

### esbuild

- esbuild는 JavaScript, TypeScript 기반 개발을 할 때 유용한 번들러다
- JavaScript, CSS, TypeScript, JSX를 기본적으로 지원한다.
- Go 기반이다
- ESM, CommonJS 둘 다 가능
- CSS, CSS Modules 가능
- Tree shaking, minification, source map 기능
- local server, watch mode, plugins

### build

build는 entry, output이 있다. entry는 코드가 시작하는 곳으로 보면 된다. 여기서부터 파일/메서드를 불러와서 실행한다. output은 빌드의 결과물이 담기는 곳이다.

esbuild에는 build mode가 3가지 있다. watch, serve, rebuild. watch는 dev hot reloading server, server는 prod sever, rebuild는 build

### TypeScript

TypeScript도 기본으로 지원한다. entry에 그대로 파일을 넣기만 하면 됨

### entry, output

entry와 output에는 다양한 옵션이 있는데, 당장 개발을 위해서 너무 자세히 알 필요는 없을 듯 하다.

### Server Component

웹 서버로 콘텐츠를 서빙하기 위해서는, React Server Component에 대해서 추가로 학습해야 한다. 아직 어떤 형태로 보내야 브라우저에서 그대로 이걸 잘 읽는지 자세히는 모르겠다. 이전에 봤었던 Jack Harrington 영상에서 얼추 익혔던 것 같긴 한데 확인이 필요한다.

### 서버..

웹 서버를 만들.. 것이면 따로 뭔가를 더 설치를 해야 하는지 아닌지 모르겠다. esbuild의 기본적인 serve 기능을 활용하면 되는 것 같긴 한데? 음 내가 routing까지 할지 말지가 고민이 되는 듯 하다.

### Tailwind

Tailwind를 넣는 방법이 생각보다 어려울 것 같다. 아무래도 서버 컴포넌트든 아니든 쉽게 작동을 했었던 부분이 그냥 자연스럽게 작동을 했었기 때문에 별 생각 없이 개발을 했어서 구체적으로 어떻게 하는지 생각이 나지 않긴 하다.

## TIL 2025-02-04

### Tailwind

이번 기회에 tailwind 4를 넣어보기로 했다. 넣기 위해서는 postcss와 같이 들어가야 하는 듯 하고 .. 여러 라이브러리를 찾아봤는데 결국 꽤 low 한 접근을 해야 문제를 해결할 수 있어보인다.

당장은 tailwind 4 + esbuild를 적용하기는 어려워보였다. tailwind의 작동원리를 정확하게 알지 못하기 때문에, 이를 번들러에서 적용하는 것은 허들이 상당히 높았다. 일단 속도를 올리기 위해서 cli를 설치해서 쓰기로 했고 이게 더 편해보인다.

단점이라면 
- esubild의 config에서 깔끔하게 해결하지 못하고 별도의 cli를 작동시켜야 한다는 점
- HTML에 따로 빌드된 CSS, JS를 연결을 수동으로 해줘야 하는 점

postcss와 tailwind가 어떻게 작동하는지 우선 명확하게 알아야 esbuild에 tailwind4를 적용하는 노하우도 생길 것 같다. 쉽지 않네

### Routing & Serving

현재 라우팅과 서빙을 어떻게 해야 하는지 분명하게 정해지지 않았다. React Router v7로 프레임워크를 온전히 사용하는 느낌으로 가던지, 아니면 내가 직접 라우팅, 서빙까지 하나 서버를 파서 하던지 결정을 해야 한다. CSR을 기본으로 하고 SSR을 덧붙여야 하는지, SSR을 기본으로 하고 CSR을 가끔씩 넣어줘야 하는지 여전히 조금 헷갈린다. 이게 각 라우팅마다 다 설정을 해줘야 하는게 그것도 귀찮을 것 같다. 편하게 가면 되는데 어려운 길을 괜히 선택하고 있다 ...

그래도 하나씩 차근차근 해낸다고 생각하면 너무 어렵진 않을 것 .. 힘냅시다

