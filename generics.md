# 제네릭

-> 데이터 타입을 일반화함(generalize), 자료형을 정하지 않고 여러 타입을 사용할 수 있음

-> 선언 시점이 아닌, 생성 시점에 타입을 명시해, 다양한 타입을 사용할 수 있음

-> 타입을 함수의 파라미터처럼 사용

**제네릭 정의**

```

function logText<T>(text: T):T {
    console.log(text);
    return text;
}

logText("hi"); //function logText<"hi">(text: "hi"):"hi"
logText<string>("hi"); //function logText<string>(text: string):string

```

# 기존 타입 정의 방식의 문제점
: type이 다르다는 이유 하나만으로 같은 내용의 함수를 중복 선언해야함

예시) 같은 내용의 함수를 string, number 타입으로 
```
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
```
function logText(text: string|number) { 
    console.log(text);
    //text.  -> string과 number의 공통 api만 접근 가능
    return text;
}  

const word = logText('a'); //word의 type은 여전히 string|number
```