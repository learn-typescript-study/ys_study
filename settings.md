# 타입스크립트 설치 및 컴파일

```
npm install typescript -g
tsc [파일명] // ts 파일이 js로 컴파일 됨
```

# 웹팩 사용하기

# json 파일 설정하기

```
{
    "compilerOptions": { // 컴파일 옵션
        "allowJs": true,
        "checkJs": true,
        "noImplicitAny": true //최소한 any type이라도 넣어야 함
    }
}
```

# Babel

js 최신문법 컴파일러
