# 유니온 타입

둘 이상의 타입을 '|' 연산자를 통해 지정할 수 있음

```
function logMessage(value: string | number){ //value에 string 아니면 number 가 들어감
    console.log(value);
}

logMessage("hello");
logMessage(10); 
```

any를 쓰지 않고 유니온 타입을 쓰게 될때의 좋은 점?

-> 유니온 타입을 쓰게 되면 헤당 타입에 대한 api와 속성을 사용할 수 있다.

-> 즉, 타입 가드가 가능하다. (타입가드: 특정 타입으로 타입의 범위를 좁혀나가는, 필터링 하는 과정)

```
function logMessage(value: string | number){
    if (typeof value === 'number'){
        value.toLocaleString();    //이 시점에서 value는 number로 읽힘. number 관련 api 사용 가능
    }
    if(typeof value === 'string'){
        value.toString(); //이 시점에서 value는 string으로 읽힘. string 관련 api 사용 가능
    }
    throw new TypeError("value must be string or number");
}

```

# 인터섹션 타입

둘 이상의 타입을 '&' 연산자를 통해 지정할 수 있음

-> 여러 타입을 하나로 결합함 : 기존 타입을 합쳐 필요한 기능을 모두 가진 단일 타입을 얻을 수 있음


# 유니온 타입과 인터섹션 타입의 차이점

-> 상대적으로 유니온 타입이 더 많이 쓰인다

function에서 넘기는 인자를 비교하자면, 유니온 타입은 넘기는 타입에 대해 선택지가 생기지만, 인터섹션 타입은 타입의 합집합으로 넘겨야 한다

```
interface Developer_ {
    name: string;
    skill: string;
}

interface Person {
    name: string;
    age: number;
}

function askSomeone(someone:Developer_|Person) {
    someone.name; //공통된 property 에 대해서만 제공함
    /*
    접근 x
    someone.skill
    someone.age
    */
}

function ask_Someone(someone:Developer_&Person) {
    // & 인터섹션 타입을 사용하면 공통이지 않은 property에도 접근 가능하다
    someone.name; 
    someone.skill;
    someone.age; 
}

///////////function 활용시////////////

// union 활용
askSomeone({name:"yun", skill:"ts"}); //Developer_ 타입 선택
askSomeone({name: "yun", age: 22}) //Persion 타입 선택

//intersection 활용
ask_Someone({name:"yun", skill:"ts", age: 22}) // 두 타입을 합친, 양쪽의 property를 다 넘겨야 함

```
