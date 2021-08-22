# 프로토타입
js는 프로토타입 기반 언어이다

기존에 써왔던 Array, Object, Function 생성도 함수로 생성되어지며, 각각의 prototype을 지니고 있음

-> Built-in Javascript API 또는 Javascript Native API

```
let user = {name: 'capt', age: 100};
>undefined

let admin={}
>undefined

admin.__proto__=user; //admin의 prototype을 user 라고 하자.
{name: "capt", age: 100}


admin
> {}  //admin은 빈 객체이지만
  >[[Prototype]]: Object  //prototype으로 상속받은 값이 있음
    age: 100
    name: "capt"
    >[[Prototype]]
```

# 클래스
JS에서 클래스는 기존의 생성자 함수와 프로토타입으로 구현한 상속 기능을 문법적으로만 바꾼 것

-> 프로토타입 기반이 그대로 유지됨

```
function Person(name,age){
    this.name=name;
    this.age=age;
}


class Person {
    constructor(name,age){
        this.name = name;
        this.age = age;
    }
}

let capt = new Person('captain',100); //function 구현, class 구현 동일

```

## typescript 에서의 클래스 적용

```
class Person_ {
    public name: string; //class 상단에 타입 정의
    private age: number;
    readonly log: string;
    //기본적으로는 public, 접근 범위 지정 가능

    constructor(name: string,age: number){ //parameter 에도 타입 정의
        this.name = name;
        this.age = age;
    }
}
```
