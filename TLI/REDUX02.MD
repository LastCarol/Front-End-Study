# ACTION

어떤 액션을 취할 것인지 정의해 놓은 객체 

```jsx
//Payload가 필요 없는 경우
{ type: 'INCREASE'}
//Payload가 필요한 경우 
{ type: 'SET_NUMBER', Payload: 5}
```

type은 필수로 지정해야 함 Snake Case로 작성 권장 

필요에 따라 payload를 작성해 구체적인 값 전달 (option)

보통 Action 객체를 생성하는 함수를 만들어 사용함 (이러한 함수를 액션생성자라 부름)

```jsx
const increase = () => {
	return {
		type : 'INCREASE'
	}
}
// payload가 필요할떈? 
const setNumber = (num) => {
	return {
		type: 'SET_NUMBER',
		payload: num
	}
}
```

# Dispatch

Dispatch는 Reducer한테 Action을 전달하는 함수

Dispatch의 전달인자로 Action 객체가 전달

```jsx
// Action 객체를 직접 사용하는 경우 
dispatch( { type: 'INCREASE' } );
dispatch( { type: 'SET_NUMBER', payload: 5 } );

// 액션 생성자를 사용하는 경우 
dispatch( increase() );
dispatch( setNumber(5) );
```

# Reducer

Reducer는 Dispatch에게서 전달받은 Action 객체의 type 값에 따라 상태를 변경시키는 함수 

```jsx
const count = 1;

//Reducer를 생성할 때 초기 상태를 인자로 요구 
const counterReducer = (state = count, action) {
	
	//Action 객체의 type 값에 따라 분기하는 switch 조건문 
	switch (action.type)
		case "INCREASE':
			return state +1
		case 'DECREASE':
			return state -1 
		case 'SET_NUMBER':
			return action.payload

		default:
			return state;
}
```

Reducer는 순수함수여야 함 (외부 요인으로 값이 변경되면 안됨)

combineReducers 메서드로 Reducer 합칠 수 있음 

```jsx
import { combineReducers } from 'redux';

const rootReducer = combineReducers({
	counterReducer,
	anyReducer,
	...
});
```

# Store

상태 관리되는 저장소의 역할 

```jsx
import { createStore } from 'redux';

const store = createStore(rootReducer);
```

# Redux Hooks

## useSelector()

컴포넌트와 state를 연결하여 Redux의 state에 접근할 수 있는 메서드 

```jsx
import {useSelector } from 'react-redux'
const counter = useSelector(state => state.counterReducer)
console.log(counter) //1
```

## useDispatch()

Action 객체를 Reducer로 전달해 주는 메서드 

```jsx
import { useSelector } from 'react-redux'

const dispatch = useDispatch()
dispatch( increase() )
console.log(counter) //2

dispatch( setNumber(5) )
console.log(counter) // 5
```

# Redux의 세 가지 원칙

## 1. Single source of truth

동일한 데이터는 항상 같은 곳에서 가져와야 한다는 의미 즉 store라는 공간과 연결이 되야하는 원칙 

## 2. state is read-only

상태는 읽기 전용이라는 뜻 Redux의 상태는 직접 변경할 수 없고 Action 객체를 통해서만 상태를 변경 시켜야 한다는 원칙 

## 3. Changes are made with pure functions

변경은 퓨어함수로만 가능하다는 뜻으로 Reducer는 순수함수로 작성되어야한다는 원칙