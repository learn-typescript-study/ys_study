# Typescript

_JS에 type을 부여한 언어_
브라우저에서 실행하려면 컴파일이 필요하다

# Typescript를 사용했을때의 장점

## 에러의 사전 방지

의도하지 않은 코드 동작을 예방할 수 있다

```
// math.ts
function sum(a: number, b: number) :number { //return 값의 타입도 지정해놓을 수 있음
  return a + b;
}
sum('10', '20'); // Error: '10'은 number에 할당될 수 없습니다.
```

## 코드 가이드 및 자동 완성(개발 생산성 향상)

변수에 타입이 지정되어 있다면, 코드 편집기에서 해당 타입에 대한 api를 자동으로 띄워주기 때문에 정확하게 작성할 수 있다

```
function sum(a: number, b: number): number {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString(); //total 변수에 number 타입이 지정되어 있어, toLocaleString api에 바로 접근할 수 있다
```

+)js를 ts처럼 쓰려면, JSDoc을 사용해서 타입 정보를 달아 놓을 수 있다.
하지만 api들을 일일이 다 작성하는 것이 번거로우므로 typescript를 사용하는 것이 좋다!
