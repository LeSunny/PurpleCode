# 개발환경설정
- SourceTree: Git GUI 환경 제공
- chocolatey : Windows에서 소프트웨어를 설치하기 쉽게 도와주는 툴
- Node.js : JavaScript의 실행기
- NVM : 여러 Node 버전을 관리
- Webstorm : 웹 개발용 IDE. Refactoring에 최적화
  - 플러그인 : Code With Me, Rainbow Brackets




# JavaScript
## JavaScript 시작하기
- JavaScript는 브라우저에서 언제든 사용 가능하다. 크롬이 현재 JavaScript 버전을 가장 잘 지원하므로 크롬을 사용한다.
  - Windows의 Chrome: F12 > 개발자도구 > Console탭
- console.log 문법
```
console.log("첫 세미나 입니다");
console.log("첫번째 문");
console.log("두번째 문");
```
- Webstorm > js파일 생성 > 코드 입력 > 하단의 Terminal > node 파일이름 (.js는 생략 가능)


## 주석
#### 1. 한줄 주석
```
//자기소개 함수
//@param name = 이름 : string      <--어떻게 함수를 사용하는지 알 수 있음
const introducet = (name) => {
    console.log("안녕하세요"+ name)
}
```

#### 2. 여러줄 주석
```
/*
* 코드, 파일 등에 대한 작성자 정보
*    만든이 : 이다솜
* */
```


## 변수
#### <변수 선언>
```
var foo = 10,
    bar = 10;

console.log(foo, bar);
```
가독성을 위해 변수는 한 줄씩 적어주는 것이 좋다.
선언하지 않으면 아직 정의되지 않았다는 뜻의 undefined라는 값이 들어가게 된다.

#### <undefined와 null>
```
var foo;
console.log(foo); // undefined
console.log(null === undefined); //false

const a = null;
var b;
console.log(a, b); //null undefined
```
undefined와 null은 다른 값이다.
모두 JavaScript에서 값이 없음을 뜻하지만,
- undefined는 값이 아직 정의되지 않았음, 초기화되지 않음
- null은 값이 없음이라고 명시적으로 제시한 것, 의도한 값
이라는 뜻이다.

#### <var 키워드의 단점>
***var의 단점 1.*** 똑같은 이름으로 두 번 만들어줘도 에러가 안난다.
```
var name = "이다솜";
console.log(name);
var name = "리다솜";
console.log(name);
```
***var의 단점 2.*** if문 스코프 안에서 선언된 변수인데도 그 밖에서 사용이 가능하다.
```
var name = "이다솜";
if(name == "이다솜"){
    var success = true;
}else{
    var success = false;
}
console.log(success);
```
***var의 단점 3.*** 끌어올림. 아래서 선언했는데도 불구하고 var x 선언을 위로 끌어올린다.
```
console.log(x); // error가 아닌 undefined가 뜸
var x = 10;
```

#### <var의 단점을 극복한 let과 const의 등장>
```
//let : 변수
let aa = 10;
aa=20;
console.log(aa);

//const : 상수
const ab = 10;
//ab = 20; --> error 발생
console.log(ab);
```

#### <변수의 표기법>
1. Camel case
변수명에서 구분되는 곳을 대문자로 표기한다.
```
const purpleCode = 10;
```
2. 고유값은 대문자로 표기한다.
```
const BLACK = "#000000";
```
#### 템플릿 리터럴
템플릿 = 일부만 변경해서 반복이나 재사용할 수 있는 틀
```
console.log("안녕하세요 저는"+name+"입니다.");
console.log(`안녕하세요 저는 ${name}입니다.`)//template literal를 사용한 것. 안에 들어간건 place holder?라고 함.
```
