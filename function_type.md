# function

- 함수의 파라미터와 반환값에 타입을 정의할 수 있음

```TS
function addNumber(a: number,b:number): number{
    return a+b;
}
```

- 파라미터를 제한함

```TSTS
function addNumber(a: number,b:number): number{
    return a+b;
}

addNumber(10,20,30,40) //파라미터를 추가로 넣으면 Error 띄워줌 : 2개의 인수가 필요한데 2개를 가져왔습니다

```

- 옵셔널 파라미터

특정 파라미터를 선택적으로 사용하고 싶을 때에 '?' 를 붙임

```TS
function log(a: string, b?: string)

log("hi") //ok
log("hi","hello") //ok
log("hi",20) //error
```
