# 이넘
특정 값들의 집합(목록)을 의미하는 자료형.

타입스크립트에서는 숫자형, 문자형 이넘을 지원한다.

## 숫자형 이넘

초기값부터 차례대로 1씩 증가해 값을 가진다.
초기값이 주어지지 않으면 기본으로 0이 할당된다.

```
enum Shoes {
    Nike, //(enum member)Shoes.Nike = 0
    Adidas, //1
    Puma, //2
    NewBalance //3
}

let myShoes = Shoes.Nike;
console.log(myShoes); // 0

//다음과 같이 초기값을 설정할 수도 있다
enum Shoes {
    Nike = 1, 
    Adidas, //2
    Puma, //3
    NewBalance //4
}
```

## 문자형 이넘

숫자가 아닌 문자 값을 줄 수 있다.

문자형 이넘은 이넘 값 전부 다 특정 문자 또는 다른 이넘 값으로 초기화 해야함.

```
enum Shoes_ {
    Nike="나이키", //(enum member)Shoes.Nike = 0
    Adidas="아디다스"
}

let myShoes_ = Shoes_.Nike;
console.log(myShoes_); // "나이키"

```

## 이넘 활용 사례

이넘에서 제공하는 값만 받을 수 있도록 지정할 수 있다.

```
enum Answer {
    Yes = 'Y',
    No = 'N'
}

function askQuestion(answer: Answer){
    if(answer===Answer.Yes) console.log("정답입니다");
    if(answer===Answer.No) console.log("오답입니다");
}
askQuestion(Answer.Yes); //correct
askQuestion("yes") //error : enum 에 지정되어 있는 Answer 타입을 넘겨야 함
```

## 이넘의 특징
- 복합 이넘(숫자형+문자형)이 가능하지만, 권고하지 않음
- 이넘은 런타임시에 객체로 존재한다
- 숫자형 이넘에서는 리버스 매핑이 가능하다. (이넘의 키(key)로 값(value)를 얻을 수 있고 값(value)로 키(key)를 얻을 수 있음)