## Primitive Type
- 오브젝트와 레퍼런스 형태가 아닌 실제 값을 저장하는 자료형
- 프리미티브 형의 내장 함수를 사용 가능한 것은 자바스크립트 처리방식 덕

- ES2015기준 6가지

## Symbol

- 프리미티브 타입의 값을 담아서 사용
- 고유하고 수정불가능한 값으로 만듬
- 주로 접근을 제어하는데 사용


## object

- 프리미티브 타입이 아닌 것을 나타내고 싶을 때 사용하는 타입
- non-primitive type 
- not number, string, boolean, bigint, symbol, null or undefined.

## any

- 정의가 되어있지 않기 때문에 어떤것이든 될 수 있다.
- 최대한 사용하지 않아야 함. -> 컴파일 타임에 타입 체크가 정상적으로 이뤄지지 않기 때문
- 컴파일 옵션 중에 any를 써야하는데 쓰지 않으면 오류를 뱉도록 하는 옵션도 있음 -> nolmplicitAny

## unknown
- typescript 3.0 부터 지원
- any와 짝으로 any보다 Type-safe한 타입
- any와 같이 아무거나 할당 가능
- 컴파일러가 타입을 추론할 수 있게끔 타입의 유형을 좁히거나 타입을 확정해주지 않으면 다른 곳에 할당 할 수 없고, 사용할 수 없다.
- unknown 타입을 사용하면 runtime error를 줄일 수 있을 것 같다.
- 사용 전에 데이터의 일부 유형의 검사를 수행해야 함을 알리는 API에 사용할 수 있을 것 같음


## NEVER
- never 타입은 모든 타입의 subtype 이며, 모든 타입에 할당 할 수 있습니다.
- 하지만, never에는 그 어떤 것도 할당할 수 없다.
- any 조차도 never 에게 할당 할 수 없다.
- 잘못된 타입을 넣는 실수를 막고자 할 때 사용하기도 함.

---------------------------------------
## TypeScript Compiler

### compileOnSave
- true / false(default false)
- who??
    - visual studio 2015 with TypeScript 1.8.4 이상
    - atom-typescript 플러그인

### extends
- 파일 (상대)경로명: string
- TypeScript 2.1 New Spec

### files, include exclude
- 설정이 없으면 전부다 컴파일함

#### files
- 상대 혹은 절대 경로의 리스트 배열
- exclude 보다 강함.

#### include, exclude
- glob 패턴 = .gitignore
- include
    - exclude 보다 약함
    - * 갗은걸 사용하면 .ts / .tsx / .d.ts 만 include함 (allowJS)
- exclude
    - 설정 안하면 4가지 (node_modules, bower_components, jspm_packages, <outDir>)를 default함
    - include에 있어도 <outDir>이건 항상 제외함


## @types
- TypeScript 2.0 부터 사용 가능한 내장 type definition 시스템
- 아무 설정 안하면 -> node_modules/@types 라는 모든 경로 찾아 사용
- typeRoots를 사용하면 -> 배열 안에 들어있는 경로들 아래서만 가져옴
- types를 사용 -> 배열 안의 모듈 혹은 ./node_modules/@tpyes안의 모듈이름에서 찾아옴.
- [] 빈 배열을 넣으면 이 시스템을 사용하지 않겠다는 것.
- typeRoots와 types를 같이 사용하지 않음.

## target & lib

### target
- 빌드의 결과물을 어떤 버전으로 사용할 것인가
- 지정 없으면 es3

### lib
- 기본 type definition 라이브러리를 어떤 것을 사용할 것이냐
- lib를 지정하지 않을 때,
    - target 이 es3면 디폴트로 lib.d.ts를 사용
    - target 이 es5면 디폴트로 dom, es5, scripthost를 사용
    - target 이 es6면 디폴트로 dom, es6, dom.iterable, scripthost를 사용
- lib를 지정하면 그 lib배열로만 라이브러리를 사용함
 