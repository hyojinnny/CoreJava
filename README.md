## Ch1
### 1-1

변수 a 선언 

### 1-2
변수의 선언과 데이터 할당

1. 변수 선언 후 선언된 변수에 데이터를 할당하는 방법
2. 변수 선언과 할당을 한 문장으로 하는 방법

### 1-3
불변성

기본형 데이터는 불변값이다
1. 변수 a에 문자열 'abc' 할당하고 그 뒤에 'def'를 추가하면 새로운 문자열 'abcedf'를 만들고 그 주소를 a에 저장
2. 변수 b에 숫자 5 할당한 다음 변수 c에 숫자 5를 할당할 때에는 이미 데이터 영역에 저장된 5의 주소 값을 가져와서 c에 저장
3. b를 7로 바꾸려면 데이터 영역에 7이 있는지 확인해서 있으면 그 주소값을 가져오고, 없으면 새로 만들어서 저장
 
 ### 1-4
참조형 데이터의 할당

참조형 데이터는 객체의 변수영역이 존재한다
1. 변수 영역에서 변수 obj1 저장하기 위한 공간 마련하고 그 주소(@1002) 이름을 obj1로 지정
2. 데이터 그룹 내부의 프로퍼티들을 저장하기 위해 별도의 변수 영역을 마련하고 그 주소(@7103~?)를 데이터 영역 @5001에 저장
3. @7103, @7104의 이름을 a, b로 지정
4. 데이터 영역에 1, 'bbb' 있는지 확인하고 없으므로 데이터 영역 @5003, @5004에 1, 'bbb' 저장

### 1-5
참조형 데이터의 프로퍼티 재할당

obj1의 프로퍼티 a를 2로 재할당할 때 먼저 데이터 영역에서 2가 있는지 확인하고 없으므로 데이터영역 @5005에 2 저장하고 그 주소(@5005)를 @7103에 저장한다 (새로운 객체가 만들어지지 않고 기존 객체 내부 변수영역(@7103)의 값만 변경됨)

### 1-6
배열을 포함한 중첩된 참조형 데이터의 프로퍼티 할당

1. 변수 영역에서 저장 공간 마련하고 그 주소(@1002) 이름을 obj로 지정
2. 데이터 그룹 내부의 프로퍼티들을 저장하기 위한 변수 영역을 마련하고 그 주소(@7103~?)를 데이터 영역 @5001에 저장
3. @7103, @7104의 이름을 x, arr로 지정
4. 데이터 영역에 3 있는지 확인하고 없으므로 데이터 영역 @5002에 3 저장
5. @7104에 저장할 값은 데이터그룹이므로 내부 프로퍼티들을 저장하기 위한 변수 영역을 마련하고 그 주소(@8104~?)를 @5003에 저장
6. 배열의 요소가 총 3개이므로 3개 변수 공간 확보, 각각 인덱스(0,1,2) 부여
7. 데이터 영역에 3 있는지 확인하고 그 주소(@5002)를 @8104에 저장
8. 데이터 영역에 4, 5 있는지 확인하고 없으므로 데이터 영역 @5004, @5005에 4, 5 저장하고 그 주소(@5004, @5005)를 @8104에 저장

### 1-7
var copy

(변수의 선언 및 할당) 변수 a를 선언하고 a가 10을 가리키게 한다

(변수의 복사) b=a를 통해 a가 가리키는 것을 b도 가리키게 한다

변수 obj1을 선언하고 obj1의 프로퍼티 c가 10을, 프로퍼티 d가 'ddd'를 가리키게 한다

obj2=obj1을 통해 obj1이 가리키는 것을 obj2도 가리키게 한다

### 1-8
var copy 후 값 변경 결과 비교(1) - 객체의 프로퍼티 변경 시

6번째 줄에서는 데이터 영역에 아직 15가 없으므로 새로운 공간 @5004에 저장하고, b에 그 주소를 저장

7번째 줄에서는 데이터 영역에 아직 20이 없으므로 새로운 공간 @5005에 저장하고, obj2의 프로퍼티 c에 그 주소를 저장

(기본형과 참조형 데이터의 차이) a, b는 서로 다른 주소를 가리키는데, obj1과 obj2는 여전히 같은 객체를 가리킨다 

### 1-9
var copy 후 값 변경 결과 비교(2) - 객체 자체를 변경했을 때

7번째 줄에서 obj2에 새로운 객체를 할당하여 값을 직접 변경

데이터 영역에 새 객체를 저장하고 그 주소를 변수 영역의 obj2에 저장 

### 1-10
객체의 가변성에 따른 문제점

함수 changeName : user 객체를 변수 newUser에 복사하고 newUser 프로퍼티 name을 newName으로 변경한 뒤 newUser 반환

user의 프로퍼티 name이 'Jung'으로 변경되고 변수 user2에 복사 (user == user2)

(불변 객체가 필요한 경우) 정보가 바뀐 시점에 알림을 보내야 하는 경우, 변경 전 후의 정보 차이를 가시적으로 보여줘야 하는 경우 등

### 1-11
객체의 가변성에 따른 문제점 해결 방법

변경 전/후에 서로 다른 객체를 바라보게 한다

함수 changeName이 새로운 객체를 반환하도록 수정 (user != user2)

### 1-12
기존 정보를 복사해서 새로운 객체를 반환하는 함수(shallow copy)

함수 copyObject : for in 문법 (반복) 을 이용하여 result 객체에 target 객체의 프로퍼티들을 복사

### 1-13
함수 copyObject 이용한 객체 복사

user 객체 내부의 변경이 필요할 때 무조건 copyObject 함수를 사용하기로 규칙을 정하면 user 객체가 불변 객체라고 볼 수 있다

### 1-14
중첩된 객체에 대한 shallow copy

user 2의 프로퍼티 name을 변경해도 user의 프로퍼티 name은 바뀌지 않음 (user.name != user2.name)

user의 프로퍼티인 urls의 프로퍼티들 (portfolio, blog) 은 기존 데이터를 그대로 참조하기 때문에 사본을 변경할 때 원본도 변경됨
(user.urls.portfolio == user2.urls.portfolio)

### 1-15
중첩된 객체에 대한 deep copy

user2의 프로퍼티 urls에 함수 copyObject 실행 결과를 할당

urls의 내부 프로퍼티들 (portfolio, blog) 도 원본에 영향을 주지 않고 변경됨

객체를 복사해서 새로운 데이터를 만들 때 객체의 프로퍼티 중에서 기본형 데이터는 그대로 복사, 참조형 데이터는 내부의 프로퍼티들을 복사해야 한다 

참조형 데이터가 있을 때마다 재귀적으로 수행해야 한다 (깊은 복사) 

### 1-16
객체 deep copy 수행하는 범용 함수

함수 coopy ObjectDeep : target이 객체이면 내부 프로퍼티에 copyObjectDeep 함수를 재귀적으로 호출해서 할당하고 target이 객체가 아니면 target을 그대로 할당하여 반환한다

### 1-17
deep copy 결과 확인

깊은 복사로 인해 내부의 프로퍼티들이 변경되어도 원본에 영향을 주지 않음 (obj != obj2)

### 1-18
JSON을 활용한 간단한 deep copy

객체를 JSON 문법으로 표현된 문자열로 전환했다가 다시 JSON 객체로 변환

(함수, __proto__, getter/scatter 등 JSON으로 변경할 수 없는 프로퍼티들은 모두 무시됨)

### 1-19
자동으로 undefined를 부여하는 경우

사용자가 어떤 값을 지정할 것이라고 예상되는 상황에 지정하지 않은 경우 undefined 반환

1. 값을 대입하지 않은 변수 (데이터 영역의 주소를 지정하지 않은 식별자에 접근할 때)
2. 객체 내부에 존재하지 않는 프로퍼티에 접근하려고 할 때
3. return 문이 없거나 호출되지 않는 함수의 실행 결과

### 1-20
undefined와 배열

'비어있는 것'과 'undefined가 할당되어 있는 것'은 동일하지 않음

1. undefined를 직접 부여했을 때 undefined는 값으로 존재함
2. 빈 요소에 접근하려고 할 때 반환되는 undefined는 인덱스 자체가 존재하지 않고 비어있음을 의미

### 1-21
빈 요소와 배열의 순회

undefined를 할당한 arr1에 대해서는 배열의 모든 요소를 순회해서 결과 출력

빈 요소가 있는 arr2에 대해서는 각 함수들이 빈 요소에 대해서는 건너뜀 (순회 대상에서 제외됨)

배열이 객체이기 때문 (배열에서 값이 지정되지 않은 인덱스인 빈 요소는 아직 존재하지 않는 프로퍼티임)

### 1-22
undefined와 null의 비교

혼란을 방지하기 위해 비어있음을 나타낼 때 'null'로 표현

변수가 undefined 인지 null인지 판단하기 위해서는 동등 연산자(==)가 아닌 일치 연산자(===)를 통해 판별 가능

## Ch2
### 2-1
[변수 호이스팅]
**실행 컨텍스트와 콜 스택**
* Declaration(선언)
* Expression(표현)

- 자바스크립트 엔진은 코드 스캔 2번
1. hoisting : 먼저 코드에서 선언과 표현을 찾음 (1번째 스캔)
2. execution : 코드를 실행 (2번째 스캔)

- 예제 2-1 수행 과정 (console에 대한 스택은 무시)
1. 자바스크립트 코드를 처음 실행했을 때 global execution context가 스택의 가장 첫 부분에 들어감
2. (11번째 줄) outer 함수가 실행되어 outer execution context가 스택에 쌓임
3. (8번째 줄) inner 함수가 실행되어 inner execution context가 스택에 쌓임
4. inner 함수 수행이 끝나면 inner execution context가 스택에서 제거됨 (pop)
5. outer 함수 수행이 끝나면 outer execution context가 스택에서 제거됨
6. 전체 프로그램이 끝나면 global execution context가 스택에서 제거됨

* 각 execution context
    - environmentRecord (내부환경)
    - outerEnvironmentReference (외부환경)
    - This

### 2-2 : 변수 재선언, 호이스팅
매개변수와 변수에 대한 호이스팅(1) - 원본 코드

세번째 줄에서 var x; 변수 선언 부분에 대해 값이 정의되지 않은 것으로 착각하면 안됨  
a(1)에서 이미 매개변수 x를 받아서 x는 1을 가리키고 있음

* function에 대한 declaratiion : function a (...) {...}
* function execution : a(...);

### 2-3
매개변수와 변수에 대한 호이스팅(2) - 매개변수를 변수 선언/할당과 같다고 간주해서 변환한 상태

예제 2-2에서 a(1);을 통해 매개변수 x=1 선언/할당 
예제 2-3에서 function a 내부에서 변수 var a = 1 선언/할당

### 2-4
매개변수와 변수에 대한 호이스팅(3) - 호이스팅을 마친 상태

예제 2-2에서 호이스팅으로 수집 대상(declaration)을 끌어올리고 호이스팅을 마치면 예제 2-4와 같은 형태

### 2-5
함수 선언의 호이스팅(1) - 원본 코드

1. 3번째 줄에서 var b 변수 선언
2. 5번째 줄에서 function b () {} 함수 선언
3. 호이스팅 마친 후 b는 함수 b () {} 에 대한 주소를 가리키고 있음
4. 8번째 줄에서 a(); 수행
5. 2번째 줄 결과 : 함수 b () {}
6. 3번째 줄에서 var b = 'bbb'; 할당하여 b는 'bbb'를 가리키고 있음
7. 4번째 줄 결과 : 'bbb'
8. 5번째 줄은 선언이므로 지나감
9. 6번째 줄 결과 : 'bbb'

### 2-6
함수 선언의 호이스팅(2) - 호이스팅을 마친 상태

### 2-7
함수 선언의 호이스팅(3) - 함수 선언문을 함수 표현식으로 바꾼 코드

### 2-8
함수를 정의하는 세 가지 방식

1. function a () {...}  
함수 선언문. 호이스팅 시 함수 a 선언
2. var b = function () {...}  
(익명) 함수 표현식. 호이스팅 시 변수 b 선언. 실행 시 b가 function () {} 에 대한 주소를 가리킴
3. var c = function d () {...}  
기명 함수 표현식. 호이스팅 시 변수 c 선언. 실행 시 c가 function d () {} 에 대한 주소를 가리킴  
기명 함수 표현식을 사용할 경우, 외부에서는 함수명으로 함수를 호출할 수 없음 (외부에서 함수명 보이지 않음)

### 2-9
함수 선언문과 함수 표현식(1) - 원본 코드

1. function sum (...) {...} 함수 선언
2. var multiply 선언
3. 1번째 줄 실행 시 함수 sum 수행하여 결과 3 반환
4. 2번째 줄 실행 시 multiply는 아직 가리키고 있는 것이 없음 (함수 아님) - 에러

### 2-10
함수 선언문과 함수 표현식(2) - 호이스팅을 마친 상태

함수 선언문은 전체를 호이스팅, 함수 표현식은 변수 선언부만 호이스팅

### 2-11
함수 선언문의 위험성

한 코드 내에서 여러 함수 선언문이 사용될 경우 위험성 높음  
호이스팅 과정에서 원래 목적과 다르게 변수가 가리키는 것이 바뀔 수 있음  
위 함수대로 출력, 아래 함수대로 출력이 순서대로 이루어지는 것이 원래 목적이었으나 결과로는 모두 아래 함수대로 출력됨  
(sum 함수가 2번 선언되어 아래 함수를 가리키는 상태가 되고 위 함수는 없는 것과 같음)

### 2-12
상대적으로 함수 표현식이 안전

함수 표현식을 사용한 경우, 호이스팅 과정에서 변수 선언될 때 함수로 값이 할당되지 않으므로,  
할당 전에 함수를 수행하려고 하면 에러 발생  
실행 과정에서 함수가 할당된 후에는 함수 수행 시 목적에 맞게 결과값 출력  
(함수 명 중복 사용 등으로 인한 혼란 방지됨)

### 2-13
스코프 체인

* identifier
    - scope : identifier가 읽거나 쓸 수 있는 유효범위
    - lifetime : identifier가 생성되고 소멸될 때 까지 시간 (call stack에 있는 context가 발생하고 소멸할 때까지)

* inner context를 수행 중에 어떤 변수를 읽거나 써야할 때 스코프 체인(scope chain)
1. 먼저 내부 환경에서 찾아봄
2. 1에서 없을 때 외부 환경 chain을 따라가서 그 실행 컨텍스트(outer context)의 내부 환경에서 찾아봄
3. 2에서 없을 때 2 과정을 반복

### 2-14
스코프 체인 확인(1) - 크롬 전용

outer 스코프에서 inner 변수만 노출됨

### 2-15
스코프 체인 확인(2) - 크롬 전용

outer 스코프에서 변수 b, inner 노출됨

* 함수 내부에서 실제로 호출할 외부 변수들의 정보만 보여준다 (브라우저 속도 향상)

### 2-16
스코프 체인 확인(3)

debugger; 를 통해 스코프 체인, this 정보를 자세하게 확인 가능

## Ch3
### 3-1
전역 공간에서의 this(브라우저 환경)

* this는 실행 컨텍스트가 생성될 때 (함수를 호출할 때) 결정됨
* 전역 공간에서 this는 전역 객체
* 브라우저 환경에서 전역 객체는 window (this == window)

### 3-2
전역 공간에서의 this(Node.js 환경)

* Node.js 환경에서 전역 객체는 global (this == global)  
* Node.js에서 전역 객체가 global인데 console.log(this) 실행 결과 {}, console.log(this === global) 실행 결과 false인 이유
    - Node에서 실행되는 js 파일은 하나의 모듈
    - js 파일에서 작성하는 코드 전체는 하나의 함수 내부에 들어가게 되므로 지역 scope를 가짐
    - 참고 : https://www.zerocho.com/category/NodeJS/post/5b67e8607bbbd3001b43fd7b, https://haeunyah.tistory.com/86

### 3-3
전역변수와 전역객체(1)

* 전역 변수를 선언하면 자바스크립트 엔진은 이를 전역객체의 프로퍼티로도 할당
* 자바스크립트의 모든 변수는 특정 객체의 프로퍼티로서 동작

### 3-4
전역변수와 전역객체(2)

전역변수 a == window.a == this.a

### 3-5
전역변수와 전역객체(3)

* 전역변수를 선언하면 자동으로 전역객체의 프로퍼티로 할당하고, 그 프로퍼티의 configurable attribute에서 (update:false), (delete:false) 로 정의
* 전역변수는 변경 및 삭제가 불가능

### 3-6
함수로서 호출, 메서드로서 호출

1. 객체의 메서드로서 호출할 경우에만 메서드(method)로 동작
2. 그렇지 않으면 함수(function)로 동작

4번째 줄에서 func는 함수, 9번째 줄에서는 obj의 메서드로 동작

* 함수로서 호출되었을 때 this는 전역객체 (window)
* 메서드로서 호출되었을 때 this는 실질적으로 호출한 객체 (obj)
* ‘함수로서의 호출’과 ‘메서드로서의 호출’을 구분하는 방법 : 함수 앞에 점(.)이 있는지 여부

### 3-7
메서드로서 호출 – 점 표기법, 대괄호 표기법

1. 점 표기법 (ex) obj.prop
2. 대괄호 표기법 (ex) obj[‘prop’]

함수 이름 앞에 객체가 명시되어 있는 경우는 메서드로서 호출, 그렇지 않으면 함수로서 호출

### 3-8
메서드 내부에서의 this

10~13번째 줄에서 methodB를 실행 - this 출력 - methodB를 호출한 객체는 obj.inner

### 3-9
내부함수에서의 this

* outer 함수 안에 함수 innerFunc 선언 – 내부함수
* This 바인딩에 관해서는 함수를 실행하는 당시의 주변 환경(매서드 내부인지, 함수 내부인지) 중요하지 않음. 
* 오직 해당 함수를 호출하는 구문 앞에 점 또는 대괄호 표기가 있는지가 중요

* 15번째 줄에서 outer 호출한 객체는 obj1 (obj1.outer 이므로)
* 7번째 줄에서 innerFunc 호출한 객체는 window 또는 global (innerFunc 이므로 전역객체)
* 12번째 줄에서 innerMethod 호출한 객체는 obj2 (obj2.innerMethod 이므로)

### 3-10
내부함수에서의 this를 우회하는 방법

내부함수에서의 this와 외부함수의 this를 일치시키고 싶은 경우, 외부함수에서 변수를 선언하여 this를 넘겨줄 수 있음 (ex) var self = this

* 16번째 줄에서 outer 호출한 객체는 obj (obj.outer)
* 7번째 줄에서 innerFunc1 호출한 객체는 window 또는 global (innerFunc1 * 이므로 전역)
* 12번째 줄에서 innerFunc2 실행 시 obj (self == this == obj)

### 3-11
this를 바인딩하지 않는 함수(화살표 함수)

1. function (args) {…}
2. (args) => {…}  (ex) var innerFunc = ( ) => { console.log(this); }

2번 경우, this가 없음 (scope chain에서 this를 찾음)

### 3-12
콜백 함수 내부에서의 this

**콜백 함수 : 함수를 다른 함수의 argument로 전달하는 경우. 함수의 제어권을 다른 함수(or 메서드)에게 넘겨주는 함수**

콜백 함수 내부의 this는 콜백을 사용하는 함수에 의해 결정됨

querySelector(‘#a’) : dom element selector에 의해 결정 (ex) id==”a” 인 것을 찾아라

### 3-13
생성자 함수

생성자 : 구체적인 인스턴스를 만들기 위한 일종의 틀

1. ‘new’ 명령어와 함께 생성자 함수를 호출하면 빈 객체를 생성하고 그 주소가 this에 할당됨
2. 함수를 실행하여 this에 새로운 프로퍼티를 추가하고 끝나면 this를 반환

```js
var Dog = function (name, color) { 
this.name = name;
this.color = color;
};
var happy = new Dog(‘해피’, ‘white’);
```

### 3-14
call 메서드(1)

Function.prototype (object의 일종으로 아래 메서드들이 정의되어 있음)
1. call : function ( … ) { … }
2. apply : function ( … ) { … }
3. bind : function ( … ) { … }

function의 instance 들이 위 function들을 사용할 수 있음

(ex) var func = function ( … ) { … } 에서 func 가 instance이고, func.call 을 실행할 수 있음

* call 메서드 : 첫 번째 argument를 this로 바인딩하고 두 번째 이후 인자들을 함수의 매개변수로 지정

### 3-15
call 메서드(2)

obj.method.call({a:4}, 5, 6); 에서 this={a:4} (this.a==4), 매개변수 x=5, y=6

### 3-16
apply 메서드

* apply 메서드 : 첫 번째 인자를 this로 바인딩하고 두 번째 인자를 배열로 받아서 배열의 요소들을 함수의 매개변수로 지정

obj.method.apply({a:4}, [5, 6]); 에서 this={a:4} (this.a==4), 매개변수 x=5, y=6

### 3-17
call/apply 메서드의 활용 (1-1) 유사배열객체에 배열 메서드 적용

array-like object : object 내부에 index와 length를 키(key)로 갖는 경우
배열 메서드(push, slice 등) - array 인스턴스만 사용 가능, object에서 사용 불가, array-like object는 사용 가능

* push 메서드 : this(배열 형식)를 받아서 새 index로 매개변수를 추가하고 length를 증가시켜 반환
    - 참고 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push

* slice 메서드 : this를 받아서 array로 변환하여 반환
    - 참고 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice

### 3-18
call/apply 메서드의 활용 (1-2) arguments, NodeList에 배열 메서드 적용

* forEach (배열 메서드) : this(array)에서 element 하나씩 함수에 실행시킴

### 3-19
call/apply 메서드의 활용 (1-3) 문자열에 배열 메서드 적용 예시

문자열(string) : array-like, read-only (string에 변형을 가하는 메서드는 사용 불가), immutable

문자열에 push 메서드를 사용하려고 할 경우 에러 메시지 출력

* map 메서드 : this(array)에서 element 하나씩 꺼내서 함수를 실행하고 새로운 어레이를 만들어서 반환 (array 복제)
    - 참고 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map

* reduce 메서드 : 초기값에서 변환(transform)하여 누적한 값을 반환
    - reduce 메서드의 콜백함수에는 4개의 인수가 존재
        1. 초기값 또는 누적값(콜백함수의 이전 반환값)
        2. 현재값 (reduce 메서드를 호출한 배열의 요소값)
        3. index (reduce 메서드를 호출한 배열의 요소값의 index)
        4. this (reduce 메서드를 호출할 배열자체)
    - reduce 메서드를 사용할 때는 반드시 값을 리턴해야 함
    - 인용 : https://velog.io/@favorcho/%EB%B0%B0%EC%97%B4%EC%9D%98-reduce-%EB%A9%94%EC%84%9C%EB%93%9C

### 3-20
call/apply 메서드의 활용 (1-4) ES6의 Array.from 메서드

예제 3-17에서 사용된 slice 메서드는 원래 ‘복사’의 목적은 아님. ES6에서는 Array.from 메서드를 이용할 수 있음

* Array.from 메서드 : 유사배열객체/순회 가능한 모든 종류의 데이터 타입을 배열로 전환 

### 3-21
call/apply 메서드의 활용 (2) 생성자 내부에서 다른 생성자를 호출

* 예제 3-13 (생성자 함수) 참고
* 생성자 함수 내부에 다른 생성자와 공통 사항이 있는 경우, 생성자 함수 내부에서 다른 생성자를 호출 가능

### 3-22
call/apply 메서드의 활용 (3-1) 최대/최솟값을 구하는 코드를 직접 구현

배열에서 하나씩 number를 받아서 그 시점에서 최댓값보다 큰 경우 최댓값이 number가 되고, 최솟값보다 작은 경우, 최솟값이 number가 된다.   
(그렇지 않으면 최댓값, 최솟값 그대로 유지)  
배열 요소를 모두 순회하면 배열의 최댓값이 max, 최솟값이 min으로 구할 수 있다.

### 3-23
call/apply 메서드의 활용 (3-2) 아래 인수를 받는 메서드(Math.max/Math.min)에 apply 적용

예제 3-22 보다 훨씬 간단하게 최대 최소 구하기 문제 해결 가능

### 3-24
call/apply 메서드의 활용 (3-3) ES6의 펼치기 연산자 활용

* 펼치기 연산자(spread operator) : 배열이나 문자열과 같이 반복가능한 객체를 하나씩 펼쳐서 리턴
    - 인용 : https://velog.io/@seul06/Spread-Operator-%EC%A0%84%EA%B0%9C-%EC%97%B0%EC%82%B0%EC%9E%90

### 3-25
bind 메서드의 활용 - this 지정과 부분 적용 함수 구현

* bind 메서드 : call과 비슷하지만 즉시 호출하지 않고 넘겨받은 this 및 인자들을 바탕으로 새로운 함수를 반환하기만 하는 메서드. 다시 새로운 함수를 호출할 때 인수를 넘기면 그 인수들은 기존 bind 메서드를 호출할 때 전달했던 인수들의 뒤에 이어서 등록됨.

* bind 메서드 목적 2가지
1. 함수에 this 미리 적용하는 것
2. 부분 적용 함수 구현하는 것

* 6번째 줄에서 bindFunc1 : func에 this를 {x:1} 로 지정
    - bind로 this만 지정
* 9번째 줄에서 bindFunc1 : func에 this를 {x:1} 로 지정하고, 앞에서부터 2개의 인수를 각각 4, 5로 지정
    - bind로 this 지정 및 부분 적용 함수 구현

### 3-26
bind 메서드 - name 프로퍼티

* bind 메서드를 적용해서 새로 만든 함수가 갖는 성질
    - name 프로퍼티에 'bound' 접두어가 붙는다

### 3-27
내부함수에 this 전달 - call vs. bind

(예제 3-10 보다 간단하게 표현하는 방법)  
(위) call 메서드 사용한 방식  
(아래-주석처리 해체필요) bind 메서드 사용한 방식

### 3-28
bind 메서드 - 내부함수에 this 전달

콜백 함수를 인자로 받는 함수/메서드 중에서 콜백함수 내의 this에 관여하는 함수/메서드에 대해서도 bind 메서드를 사용하면 this 값을 사용자 설정 값으로 변경 가능

### 3-29
화살표 함수 내부에서의 this

* ES6 화살표 함수 
    - 실행 컨텍스트 생성 시 this를 바인딩하는 과정 제외됨
    - 함수 내부에 this가 아예 없고, 접근할 때 스코프 체인 상 가장 가까운 this에 접근

### 3-30
thisArg를 받는 경우 예시 - forEach 메서드

* report 객체 
    - sum, count 프로퍼티
    - add, average 메서드

* 5번째 줄에서 arguments를 배열로 변환해서 args 변수에 담는다
* 6번째 줄에서 배열을 순회하면서 콜백 함수 실행, 콜백 함수 내부에서의 this는 forEach 함수의 두번째 인자로 전달
* 15번째 줄에서 add 메서드를 수행할 때 콜백 함수 내부에서의 this는 add 메서드에서의 this가 전달된 상태이므로 add 메서드의 this (this == report)

### 3-31
콜백 함수와 함께 thisArg를 인자로 받는 메서드

forEach, map, filter, some, every, find, findIndex, flatMap, from, forEach
