# SCSS MASTER

### CSS 환경 설정

- nodeJs, npm 다운로드 및 설치
- npm create vite@latest
- npm install
- code .
- npm run dev

### flexbox 모바일 친화적이고 반응이 빠른 유연한 웹 사이트 구축을 도움

- 부모요소, 직속부모에게 flex 하면 자식들에게 적용
- gap : 공백적용
  1. row-gap, column-gap
- flex-direction :
  1. 기본값 row, 요소들이 어떤 방향으로 갈 지를 지시
  2. row 일 경우 주축은 수평이고, 교차축은 수직
  3. column 일 경우 주축은 수직이고, 교차축은 수평
- justify-content :
  1. 자식 요소들을 수평,수직 정렬
  2. space-between, row(column)-reverse, space-around
  3. row 일경우 왼쪽에서 오른쪽을 정렬
- align-items :
  1. 높이가 있어야만 적용
  2. 교차축을 따라 flex item을 정렬 함
  3. row 일 경우 위 아래 높이를 정렬
  4. 전체를 위, 아래, 혹은 중앙으로 움직임
- flex-wrap : 박스를 한 줄에 적용 하거나, 여러줄로 적용
  1. 기본 nowrap : 한줄에 모든 박스가 적용, wrap : 박스의 너비를 적용
  2. flex-flow: row wrap > direction 과 wrap를 한번에 적용 시켜줌
- align-content :
  1. 다중라인 flex 컨테이너에서 라인들의 정렬을 설정하는데 유용 함
  2. 항목들 사이의 공간을 적용
  3. 여러개의 라인이 or 다중 라인을 사용하게 되면 필요
     ㄴ
- flex의 자식 항목들에 적용되는 속성

  1. order : 0 위치를 변경할 수 있음
     상대적인 속성이고, 아무데나 갈 수 있는게아니고 다른 자식들에 상대적으로 동작
     음수 값도 적용 가능
  2. align-self : 항목이 교차축(이 경우 수직)에서 개별적으로 정렬을 선택할 수 있게 해줌
     flex-start, flex-end

  ```
  .father {
    height: 100vh;
    display: flex;
    row-gap: 10px;
    column-gap: 20px;
    flex-direction: row;
    justify-content: space-between;
    align-items: self-start;
    flex-wrap: wrap;
    align-content: center;
  }

  .box {
    width: 150px;
    height: 150px;
    background-color: tomato;
    font-size: 36px;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .box:nth-child(3) {
    background-color: blueviolet;
    order: 1;
  }
  .box:nth-child(6) {
    background-color: aqua;
    order: 2;
  }
  ```

- flex-grow

  ```
  1. 직접 값을 설정하지 않고 플렉스 컨테이너로 크기를 정하는 방법
  2. flex 컨테이너 자식들에게 얼마만큼의 공간을 차지할 수 있는지 알려줌
  3. 필셀이나 백분율을 사용하지 않고 비율만 사용 함
  4. grow 0은 딱 필요한 만큼만 공간을 만듬

  .box:first-child {
    background-color: tomato;
    flex-grow: 0.8;
  }
  .box:last-child {
    background-color: teal;
    flex-grow: 0.2;
  }
  ```

- flex-shrink

  ```
  1. 아이템이 얼마나 줄어들지 정할 수 있음
      화면이 줄어들 경우 어떤 비율로, 어느 순서로 먼저 줄어들지 정할 수 있음

  .box:first-child {
    background-color: tomato;
    flex-grow: 1;
    flex-shrink: 3;
  }
  .box:nth-child(2) {
    background-color: orange;
    flex-grow: 2;
    flex-shrink: 0;
  }
  .box:last-child {
    background-color: teal;
    flex-grow: 1;
    flex-shrink: 1;
  }
  ```

- flex-basis

  1. flex 항목의 이상적인 크기인 초기 크기를 설정 할 수 있음
  2. min-width와 같은 효과를 낼 수 있음
  3. flex: 1 0 500px; (grow shrink basis)

  ```
  .box:first-child {
    background-color: tomato;
    flex: 0 0 500px;
  }
  .box:last-child {
    background-color: teal;
    flex-grow: 1;
  }
  ```

### grid

- grid-template-columns, grid-template-rows : 레이아웃 설정
- grid-column-start, grid-column-end (grid-column,grid-row: 1 / -1) :
  1. 공간 위치 변경 및 공간 크기 설정
  2. 라인 이름을 지정할 수 있음
  ```
  .father {
    display: grid;
    grid-template-columns: [ㄱ] 100px [ㄴ] 200px [ㄷ] 50px [ㄹ];
    grid-template-rows: [ㅁ] 200px [ㅂ] 100px [ㅅ];
    row-gap: 10px;
    column-gap: 20px;
  }
  .child:last-child {
    background-color: turquoise;
    grid-column: ㄴ / ㄹ;
  }
  .child:first-child {
    grid-row: ㄱ / ㅁ;
  }
  ```
- grid-template-areas, grid-areas

  1. 텍스트로 grid의 템플릿을 디자인 함
  2. grid-template 을 사용하면 더 간편하고쉽게 설정 가능

  ```
  body {
    padding: 0;
    margin: 0;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;

    display: grid;
    height: 100vh;
    /* grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 2fr 1fr;
    grid-template-areas:
      "header header header header"
      "content content content menu"
      "footer footer footer footer"; */
    grid-template:
      "header header header header" 1fr
      "content content content menu" 2fr
      "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr;
  }
  header {
    background-color: aqua;
    grid-area: header;
  }
  section {
    background-color: coral;
    grid-area: content;
  }
  aside {
    background-color: forestgreen;
    grid-area: menu;
  }
  footer {
    background-color: deeppink;
    grid-area: footer;
  }
  ```

- span

  1. 그냥 이 박스는 2개의 행을 차지하도록 설정하고 싶을 경우
  2. (y)grid-row: span 2
  3. (x)grid-column: span 2
  4. grid-row: content / span 2

- gird auto columns, rows, flow

  1. 준비하지 않은 콘텐츠가 있을 때 그리드에 어떤 일이 발생할 지 결정
  2. grid-auto-rows(1fr), column, : 지정한 행의 크기보다 많아 질경우, 준비하지 않은 행의 크기를 미리 지정, 새로 추가된 행의 크기를 지정
  3. grid-auto-flow(row, column) : 추가로 늘어난 행의 방향을 설정

  ```
  .father {
    display: grid;
    min-height: 50vh;
    gap: 10px;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 1fr);
    grid-auto-rows: 1fr;
    grid-auto-flow: row;
  }
  ```

- 그리드의 각 셀 내부 콘텐츠가 정렬되는 방식을 변경할 수 있는 속성

  1. justify-items(stretch(기본값), start, end, center) : 기본값으로 그리드 셀 안의 내용물을 가로방향으로 늘림, stretch는 with(넓이)를 가지지 않을 때만 적용
  2. align-items(stretch(기본값), start, end, center) : 셀 안의 내용물을 세로방향으로 늘림, heigth(높이)를 가지지 않을 때만 적용
  3. place-items: end center - 1,2번의 단축 속성

  ```
  .father {
    display: grid;
    min-height: 50vh;
    gap: 10px;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 1fr);
    grid-auto-columns: 1fr;
    grid-auto-flow: column;
    /* justify-items: stretch;
    align-items: stretch; */
    place-items: end center;
  }
  ```

- 셀 자체를 정렬 하는 방법

  1. align-content(space-between, start, end, center) : y방향
  2. justify-content(space-between, start, end, center) : x방향
  3. place-content: center - 1,2번의 단축 속성

  ```
  .father {
    display: grid;
    gap: 10px;
    height: 100vh;
    grid-template-columns: repeat(5, 100px);
    grid-template-rows: repeat(2, 100px);
    background-color: lightblue;
    /* align-content: center;
    justify-content: center; */
    place-content: center;
  }
  ```

- 내용물의 사이즈에 따라 열 크기를 조절할 수 있는 속성

  1. max-content : 기본적으로 두 번째 열을 콘텐츠가 필요한 만큼 크게 만듬
  2. min-content : 열의 내용물이 가질 수 있는 최소 사이즈를 열의 크기로 만듬
  3. minmax(250px, 1fr) : 최소 크기와 최대 크기가 있는 열을 생성, 최대값은 1fr로 지정해서, 공간이 있을때는 꽉 채우고, 작아지면 250px까지만 줄어들도록 만듬

  ```
  .father {
    display: grid;
    gap: 10px;
    height: 100vh;
    grid-template-columns: repeat(3, minmax(250px, 1fr));
    /* grid-template-columns: 1fr minmax(250px, 1fr) 1fr; */
    /* grid-template-columns: 1fr max-content 1fr; */
  }
  ```

- 반응형 그리드 만드는 방법, 크기에 따라 3열, 2열, 1열 로 변환
  1. auto-fill : 화면이 작아지면 3열,2열,1열 로 변환, 지정한 크기의 열을 최대한 많이 만듬, 열이 비어있다고 해도 만듬
  2. auto-fit : 화면이 작아지면 3열,2열,1열 로 변환, 공간을 전부 씀
  ```
  .father {
    display: grid;
    gap: 10px;
    height: 100vh;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  }
  ```

### SCSS ,SASS

```sass 설치, 빌드
npm add -D sass
npm run build
```

- SASS로 SCSS 코드를 처리
- nesting, mix-in, extend
  1. mix-in - css와 scss를 마치 프로그래밍 언어처럼 사용
