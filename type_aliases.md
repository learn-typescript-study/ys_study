# 타입 별칭
특정 타입이나 인터페이스를 참조할 수 있는 타입 변수를 의미함.

## 타입 별칭 사용법

```
// 1. 하나의 type에 사용 가능 (예시: string 타입을 Myname이라 지정 가능) 
type MyName = string;
const name: MyName = 'yun';

// 2. 복잡한 타입에도 별칭 부여 가능
type Developer = {
  name: string;
  skill: string;
}


```


# 타입 별칭과 인터페이스의 차이점

```
interface Person {
    name: string;
    age: number;
}

type Person = {
    name: string;
    age: number;
}
```

<타입 별칭>
- 프리뷰로 확인할 때 선언한 타입의 형태가 다음처럼 확인 가능
type Person = {
    name: string;
    age: number;
}
- 확장 불가능


<인터페이스>
- 프리뷰로 확인할 때 interface Person 라고만 확인 가능
- 확장 가능

결론: **확장이 가능한 인터페이스를 사용하자**