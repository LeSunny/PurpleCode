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
1. Camel case: 변수명에서 구분되는 곳을 대문자로 표기한다.
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


## 형 변환(Type Conversion)
- 함수와 연산자에 전달되는 값은 대부분 적절한 자료형으로 자동 변환된다.
- 타입 확인하기
```
var n = 10;
console.log(typeof n); //number
```
#### 문자형으로 변환
```
let foo3 = 1000; //foo : 미국식 의미없는 변수
console.log(typeof foo3);

foo3 = String(foo3);
console.log(typeof foo3); // string
```
#### 숫자형으로 변환
```
let str = "12345";
let aaa = "aaaaaaaaaaaaa";
let num = Number(str);
console.log(typeof num); // number
num = Number(aaa);
console.log(typeof aaa); // string

console.log("6"+"3"); //63 : +는 숫자 말고도 문자열 더하기도 있어서
console.log("6"/"3"); //2
```
#### 불린형으로 변환
```
console.log(Boolean(1)); //true
console.log(Boolean(0)); //false
```

## 연산자
#### 산술 연산자
- 증감 연산자
```
let number = 10;

number++; //이 다음 줄에서 더하기
++number; //이 줄에서 더하기
number+=10;
number-=10;
console.log(++number);//13
```

#### 대입 연산자
```
let number = 10;

number += 10; // 20
number -= 10; // 10
number *= 2; // 20
number /= 2; // 10
number %= 3; // 1
```

#### 논리 연산자
- !
  - NOT
```
console.log(!true);//false
console.log(!false);//true
console.log(!!true);//true
console.log(!!0); //false
console.log(!!1); //true
```
- &&
  - AND
```
let as = 10;
console.log(as===10 && true);
console.log(as!==10 && true);

//함수 예시
const introduce = name => {
    if(name === undefined) {
        console.log("이름이 정의되지 않았습니다.");
        return;
    }
    console.log(`나의 이름은 ${name}입니다`);
}
introduce(name); // 나의 이름은 이다솜입니다.
const me = {};
introduce(me); // 이름이 정의되지 않았습니다.
```
- 앞의 값을 확인하고 앞의 값이 참이면 뒤의 값을 실행하게 하고, 앞의 값이 falsy한 값이면 앞의 값을 출력시키도록 한다.
```
const name = "이다솜";

console.log(name && "있음"); //앞부터 봐서 true면 뒤의 조건을 본다.
console.log(undefined && "있음"); //이 경우 undefined 출력
```
- ||
  - OR
  - 첫번째 truty 값을 반환
```
console.log(true||false); //앞의 것만 true면 true 반환
console.log(false||true); //앞이 true가 아니면 뒤를 검사
const name3 = "이다솜";
console.log(name3 || "없음"); // 앞의 값이 비어있지 않으면 true >> 이다솜 출력
```

#### 삼항 연산자
```
조건 ? 참일경우 : 거짓일경우
```
코드의 가독성이 떨어지므로 코드의 복잡성이 낮을 때 사용하는 것이 좋다.
```
const name4 = "리닷솜";
if(name4==="리닷솜"){
    console.log("HI");
}else{
    console.log("BYE");
}
```
위의 코드를 아래처럼 사용 가능
```
name4==="리닷솜" ? console.log("HI") : console.log("BYE");
```

#### 비교 연산자
- == : 타입검사를 안해줌
- === : 타입검사도 해줌

#### null 병합 연산자
- a ?? b
  - a가 null도 아니고 undefined도 아니면 a
  - 그 외의 경우는 b
```
const a = null;
const b = 10;
a!==null && a!=undefined ? a : b;
```
```
let width = 0;
width = width || 1000; // 0은 falsy하니까 1000이 저장
width = width ?? 1000; // 비어있는지(undefined)만 체크 --> 0이 저장
```
  
## 조건문
#### if문
```
const number = 10;
if(number === 10){
    console.log("10 입니다.");
}
```

#### switch/case문
```
let car = prompt("차량의 이름을 입력해주세요.");

switch (car) {
  case "제네시스 G80":
    alert("현대");
    break;
  case "스팅어":
    alert("기아자동차");
    break;
  case "카마로":
    alert("쉐보레");
    break;
  case "M3":
  case "X8":
    alert("BMW");
    break;
  case "아벤타토르":
    alert("람보르기니");
    break;
  default:
    alert("모르겠습니다.");
    break;
}
```
