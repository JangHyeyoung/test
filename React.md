[TypeScript]
======================

# 1. TypeScript 환경설정 및 작성법

## 1.1. Node.js 설치
1. [**Node.js**](https://nodejs.org/ko/)에서 설치
2. npm,yarn명령어 사용
3. Node.js 확인명령어 : node -v
4. npm 업그레이드 명령어 : npm i npm to update

## 1.2. TypeScript 설치(es6)
1. 설치
```
npm install -g typescript
```
2. 설치제거
```
npm uninstall -g typescript
```
3. 특정버전 설치
```
npm install -g @특정버전명(3.8.3)
```
4. tsc 옵션 설정 파일을 생성(json)
```
tsc --init
```

## 1.3. Gulp서버(편집기) 설치
1. [**Gulp**](https://www.typescriptlang.org/index.html#download-links/)에서 설치
2. 컴파일 형식
```
tsc 예제파일명.ts
```
3. 실행 형식
```
node 예제파일명.js
```
## 1.4. Gulp서버의 개요 및 작성법
Gulp는 프로젝트를 다른 빌드들로 빌드해 줄 수 있으며 많은 플러그인들을 통해 확장성있게 작업할 수 있도록 도와주는 빌드시스템.

사용목적:<br 
1. 웹 서버 동작
2. 언어의 자동컴파일 구현 (ex : Sass =  CSS)
3. 자동 새로 고침 기능
4. 배포를 위한 리소스를 최적화

**gulp서버를 실행하기위해서 typescript를 한번 더 설치해야 된다.(로컬 설치)**

# 2. TypeScript

## 2.1. 변수선언
1. let   
: 중복선언 불가, 블럭 범위내에서만 사용 가능
2. const   
: 상수화된 변수에 초기값을 설정, 중간에 값 변경불가(상수), 중복선언가능, 블럭 범위내에서만 사용 가능,   
객체에도 사용 가능(key,value로 객체 저장 가능) =  주소값은 그대로 유지, 키에 해당되는 내용만 변경   
```
const obj = {id:123};
const user = {
    name : 'Lee',
    address : {city : 'Seoul'}
}

user.name='Kim'
console.log(user); //Kim
```
3. template literal(백틱 문자열)
:줄바꿈,다음줄 개행 자동으로 인식   
'작은 따옴표'와 "따옴표"를 혼용해서 사용
```
const template2=`
 <ul class="nav-item" 
   <li <a href="#home" Home</a </li 
   <li <a href="#news" News</a </li 
   <li <a href="#contact" Contact</a </li 
   <li <a href="#about" About</a </li 
 </ul `;

 console.log(template2);
 
 //console.log 결과값
 <ul class="nav-item" 
   <li <a href="#home" Home</a </li 
   <li <a href="#news" News</a </li 
   <li <a href="#contact" Contact</a </li 
   <li <a href="#about" About</a </li 
 </ul 
```
  ' '은 문자열뿐만 아니라 수식계산, 객체의 함수호출할때도 사용한다.

```
const name = '테스트'
const add = '서울시 강남구'
const name2 = 'test'
console.log(`1+1=${1+1}`) // 1+1=2
console.log(`안녕. ${name2.toUpperCase()}`) // 안녕. TEST
```
4. arrow function(화살표 함수)
:function 키워드 대신 화살표(= )를 사용하여 보다 간략한 방법으로 함수를 선언할 수 있다.(자료형 추가)   
JSON표기법 형태의 객체내부에서는 함수를 작성할때 화살표함수를 사용X
```
var pow=function(x:number){ //function pow(x:number)
    console.log('x= '+x);
    return x*x;
}
const test=x= x*x;
console.log(test(20));//400
```
 **자바스크립트에서 자주 사용되는 함수 5가지(배열)**
-indexOf 함수(특정한 값을 찾을때)
```
var index = [12, 5, 8, 130, 44].indexOf(8); 
console.log("index is : " + index );
//결과값
index is : 2
```
-filter 함수(JSON객체중에서 특정한 값만 추출,반환)
```
function isBigEnough(element, index, array) { 
   return (element  = 10); 
} 
          
var passed = [12, 5, 8, 130, 44].filter(isBigEnough); 
console.log("Test Value : " + passed );
//결과값
Test Value :12,130,44
```
-**Map 함수**(기존의 배열의 요소들을 하나씩 읽어들여서 계산후 길이가 같은 새로운 배열을 만들어주는 함수)
```
var numbers = [1, 4, 9]; 
var roots = numbers.map(Math.sqrt); 
console.log("roots is : " + roots );
//결과값
roots is : 1,2,3
```
-reduce 함수(배열의 각 요소에 대해 주어진 reduce 함수를 실행하고, 하나의 결과값을 반환)
```
var total = [0, 1, 2, 3].reduce(function(a, b){ return a + b; }); 
console.log("total is : " + total );
//결과값
total is : 6
```
-forEach 함수(for문 대신에 사용(성능향상))
```
let num = [7, 8, 9];
num.forEach(function (value) {
  console.log(value);
}); 
//결과값
7,8,9
```
5. rest,spread
:매개변수를 전달 못한경우에는 내부적으로 디폴트 매개변수값을 지정
-rest 매개변수(정상적으로 매개변수값이 전달되면은 적용X)
```
//x:number,y:number- default(기본값)
function plus(x=8,y=9){
    return x+y;
}
console.log('plus()= ',plus());
//결과값
17
```
-spread 연산자(react에서 많이 사용하는 연산자)
```
//동적으로 배열의 값을 받아서 처리해주는 연산자 (...배열명)
function ktest(...abc){
    console.log(Array.isArray(abc)) //배열이면 true, 배열X false
    console.log('abc= ',abc)
}

ktest(1);

//결과값
true
abc=  [ 1 ] 
```
