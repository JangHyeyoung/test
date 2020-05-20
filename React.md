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

사용목적:<br>
1. 웹 서버 동작
2. 언어의 자동컴파일 구현 (ex : Sass => CSS)
3. 자동 새로 고침 기능
4. 배포를 위한 리소스를 최적화

**gulp서버를 실행하기위해서 typescript를 한번 더 설치해야 된다.(로컬 설치)**

# 2. TypeScript

## 2.1. let
1. let
: 중복선언 불가, 블럭 범위내에서만 사용 가능
2. const
: 상수화된 변수에 초기값을 설정, 중간에 값 변경불가(상수), 중복선언가능, 블럭 범위내에서만 사용 가능
