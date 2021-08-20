# String, Number, Bollean

```
let str: string = "hi";
let num: number = 10;
let isLoggedIn: boolean = false;
```

# Array

```
let arr: number[] = [1,2,3];
let arr: Array<number> = [1,2,3]; // 제네릭 사용
```

# Object

```
let obj: object={};

let person: {name:string, age:number} = { //객체의 property에 자료형 지정 가능
    name:"yun",
    age: 20
}
```

# Tuple

튜플은 배열의 길이가 고정되고 각 요소의 타입이 지정되어 있는 배열 형식

정의하지 않은 타입이나 인덱스로 접근할 수 없음

```
let arr: [string,number] = ["hi", 10];
```

# Enum

특정값(상수)들의 집합

인덱스 번호로 접근 가능, 이넘의 인덱스를 변경 가능

```
enum Avengers { Capt, IronMan, Thor }
let hero: Avengers = Avengers.Capt;
let hero: Avengers = Avengers[0]; // 인덱스로 점근 가능

enum Avengers { Capt = 2, IronMan, Thor } //인덱스 변경 가능
let hero: Avengers = Avengers[2]; // Capt
let hero: Avengers = Avengers[4]; // Thor

```

# Any, Void, Never

- any : 모든 타입에 대해서 혀용함
- void를 사용하면 변수에는 undefined와 null을 할당하고, 함수에는 반환값을 설정할 수 없음
- never: 함수 끝에 절대 도달하지 않음

```
let arr: any = ['a', 2, true];

let unuseful: void = undefined;
function notuse(): void {
  console.log('sth');
}

// 이 함수는 절대 함수의 끝까지 실행되지 않는다는 의미
function neverEnd(): never {
  while (true) {

  }
}

```
