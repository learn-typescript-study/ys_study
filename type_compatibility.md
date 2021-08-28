# 타입 호환
: 타입스크립트 코드에서 특정 타입이 다른 타입에 잘 맞는가, 타입이 호환되는가

```TS
interface Ironman {
  name: string;
}

class Avengers {
  name: string;
}

let i: Ironman;
i = new Avengers(); // OK, because of structural typing
```
-> 인터페이스 간의 대입이 아니더라도 호환이 가능하다.

-> 타입스크립트에서는 타입에 명시되어있는 속성의 타입 위주로 판단하기 때문이다 : 구조적 타이핑(코드 구조 관점에서 타입이 서로 호환되는지 여부 판단)

### 구조적 타이핑 예시

```TS
interface Avengers {
  name: string;
}

let hero: Avengers;
// 타입스크립트가 추론한 y의 타입은 { name: string; location: string; } 입니다.
let capt = { name: "Captain", location: "Pangyo" };
hero = capt;
//더 큰 구조를 가지는 것을 더 작은 구조를 가지는 것에 대입할 수 있음 (공통이 있다면)
```

# 타입호환 예제 - 함수, 제네릭

```TS
//함수
let add = function(a: number){
    //...
}
let _sum = function(a: number, b: number){
    //...
}

_sum = add; // 파라미터의 수가 적은것을 더 큰 것에 대입할 수 있음
```

```TS
//제네릭
interface Empty<T>{

}
let empty1: Empty<string>;
let empty2: Empty<number>;
empty1 = empty2;
empty2 = empty1;

interface NotEmpty<T> {
    data: T;
}
let notempty1: NotEmpty<string>;
let notempty2: NotEmpty<number>;
//notempty1 = notempty2 //호환 x
//notempty2 = notempty1 //호환 x
```