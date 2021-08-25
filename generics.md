# 제네릭

-> 데이터 타입을 일반화함(generalize), 자료형을 정하지 않고 여러 타입을 사용할 수 있음

-> 선언 시점이 아닌, 생성 시점에 타입을 명시해, 다양한 타입을 사용할 수 있음

-> 타입을 함수의 파라미터처럼 사용

-> 함수 사용 시 타입 추론이 됨

**제네릭 정의**

```TS
function logText<T>(text: T):T {
    console.log(text);
    return text;
}

logText("hi"); //function logText<"hi">(text: "hi"):"hi"
logText<string>("hi"); //function logText<string>(text: string):string
//제네릭을 이용해 타입 추론이 됨

```

# 기존 타입 정의 방식의 문제점
: type이 다르다는 이유 하나만으로 같은 내용의 함수를 중복 선언해야함

예시) 같은 내용의 함수를 string, number 타입으로 

```TS
function logText(text: string) { 
    console.log(text);
    return text;
}  

function logNumber(num: number) { 
    console.log(num);
    return num;
}  
```

# 유니온 타입 이용의 문제점
: 타입들의 공통되는 api만 접근 가능함

: 반환값의 타입 또한 여전히 유니온 타입

```TS
function logText(text: string|number) { 
    console.log(text);
    //text.  -> string과 number의 공통 api만 접근 가능
    return text;
}  

const word = logText('a'); //word의 type은 여전히 string|number
```

# 제네릭 실전 예제 및 타입 추론에서의 이점

```TS
function logText<T>(text: T): T {
    console.log(text);
    return text;
}

const str = logText<string>('abc');
str.split(''); //string api 사용 가능
const login = logText<boolean>(true); //boolean 변경 가능


```

# 인터페이스에서 제네릭을 선언하는 법

```TS
interface Dropdown<T>{
    value: T; // 넘기는 값이 어떤가에 따라 value의 타입이 바뀜
    selected: boolean;
}

const obj: Dropdown<number> = {value: 10, selected: true}; //value: number
const obj_: Dropdown<string> = {value:"hello",selected: false}; //value: string
```

# 제네릭의 타입 제한
: 제네릭 함수에 어느 정도 타입 힌트를 줄 수 있음

```TS
function logText<T>(text: T): T {
  console.log(text.length); // Error: T doesn't have .length
  return text;
}
```
-> 위 코드에서 text에 length가 존재한다는 단서가 없기 때문에 에러가 발생함

```TS
function logText<T>(text: T[]): T[] {
  console.log(text.length); // 제네릭 타입이 배열이기 때문에 `length`를 허용합니다.
  return text;
}
```
-> T[]를 사용해 배열형태의 T를 받는다는 힌트를 남김


### 정의된 타입으로 타입을 제한하기
: extends 키워드 이용

```TS
interface LengthType {
    length: number;
}

function logTextLength_<T extends LengthType>(text: T): T{
    text.length;
    return text;
}

logTextLength_("hello");
```

### keyof로 제네릭의 타입 제한
: 지정한 key 값들만 받을 수 있도록 제약함

```TS
interface ShoppingItem {
    name: string;
    price: number;
    stock: number;
}

//interface ShoppingItem 안의 key값들만 받을 수 있도록 제약 가능

function getShoppingItemOption<T extends keyof ShoppingItem>(itemOption: T):T {
    return itemOption;
}

// getShoppingItemOption(10);
// getShoppingItemOption<string>('a');

getShoppingItemOption("name");

```

