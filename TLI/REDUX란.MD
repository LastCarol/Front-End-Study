## 프론트엔드에서의 상태란?

동적으로 표현되는 데이터 

## sideEffect?

함수 입력 외에도 함수의 결과에 영향을 미치는 요인 ex) 네트워크 요청 

## 상태의 두 가지 구분

로컬: 특정 컴포넌트 안에서만 관리되는 상태 ex) 쇼핑몰 사이트 장바구니 선택한 수량 

전역: 프로덕트 전체 혹은 여러 컴포넌트에서 관리되는 상태 ex) 네이버 다크모드 

# REDUX란?

react없이도 사용할 수 있는 상태 관리 라이브러리 

전역상태를 관리할 수 있는 store을 제공

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/19a1b908-f6d9-476e-a5d5-01b7ae7cca8d/Untitled.png)

컴포넌트3과 컴포넌트 6을 사용하고 싶을 때 컴포넌트3 > store > 컴포넌트6 으로 이동가능 

## REDUX의 구조

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/24ef46ad-bf05-439c-a335-70f865f19ece/Untitled.png)

상태 관리 순서 

1. 상태가 변경되어야 하는 이벤트가 발생하면, 변경될 상태에 대한 정보가 담긴 **Action 객체**
가 생성
2. 이 Action 객체는 **Dispatch 함수**의 인자로 전달
3. Dispatch 함수는 Action 객체를 **Reducer 함수**로 전달
4. Reducer 함수는 Action 객체의 값을 확인, 그 값에 따라 **전역 상태 저장소 Store**의 상태를 변경
5. 상태가 변경되면, React는 화면을 다시 렌더링

**Action → Dispatch → Reducer → Store** 순서로 데이터가 단방향으로 흐름