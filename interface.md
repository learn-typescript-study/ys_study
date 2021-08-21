# 인터페이스
인터페이스는 정의한 약속, 규칙을 의미한다. 다음과 같은 범주에 대해 약속을 정의할 수 있다.
- 객체의 스펙(property와 그 타입)
- 함수의 스펙(parameter와 반환 타입 등)
- 배열과 객체를 접근하는 방식
- 클래스

1. 객체의 스펙 정의

```
interface Todo { //인터페이스로 객체 스펙 정의
  id: number; 
  title: string; 
  done: boolean;
}

function fetchTodoItems(): Array<Todo> { //Todo[] 로 사용 가능
  const todos = [
    { id: 1, title: '안녕', done: false },
    { id: 2, title: '타입', done: false },
    { id: 3, title: '스크립트', done: false },
  ];
  return todos;
}
```

2. 함수의 스펙 정의

```
// 함수의 인자 정의
function getUser(user: User){
    console.log(user);
}

// 함수 구조 정의
interface SumFunction{
    (a: number, b: number): number;
}

let sum: SumFunction;

sum = function(num1, num2){ //num1과 num2, 리턴값이 모두 자동으로 number 처리
    return num1+num2;
}
```

3. 인덱싱 방식 정의

```
interface StringArray {
    [index:number]: string; //index는 숫자로 접근하고, 자료는 string이다
}

var arr: StringArray = ['a','b','c'];
arr[0] = "hi"; // 숫자라면 ERROR 발생
```

4. 딕셔너리 패턴

```
interface StringRegexDictionary {
    [key: string]: RegExp //정규표현식
}

let obj: StringRegexDictionary = {
    cssFile: /\.css$/, //확장자가 css로 끝나는 파일들
    jsFile: /\.js$/
}

obj['cssFile'] = 'a' // ERROR: RegExp가 아닌 일반 문자열을 할당할 수 없다

Object.keys(obj).forEach(function(value){ //value가 자동으로 string으로 타입 추론 
      
})
```

5. 인터페이스 확장

```
interface Person {
    name: string;
    age: number;
}

interface Developer extends Person{
    /* Developer가 Person 을 extends 하면서 필요 없어짐
    name: string;
    age: number;
    */
    language: string;
}

let yun: Developer = {
    name: "yunseo",
    age: 22,
    language: "typescript"
}
```