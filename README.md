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
