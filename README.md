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

## Ch4
### 4-1
콜백 함수 예제 (1-1) setInterval

* 콜백 함수 : 다른 코드(함수/메서드)에게 인자로 넘겨줌으로써 제어권도 함께 위임한 함수
* var intervalID = scope.setInterval(func, delay, param1, param2, ...);
    - 매개변수 func, delay
    - 세 번째 매개변수부터는 func 함수를 실행할 때 매개변수로 전달할 인자
    - func에 넘겨준 함수는 매 delay마다 실행, 결과로 어떠한 값도 리턴하지 않음
    - 반복적으로 실행되는 내용 자체를 특정할 수 있는 고유한 ID 값이 반환 (-> 변수 할당, 반복 실행되는 중간에 종료할 수 있게 하기 위함)

### 4-2
콜백 함수 예제 (1-2) setInterval

* setInterval에 전달한 첫 번째 인자인 cbFunc 함수는 0.3초마다 자동 실행됨
* 콜백 함수 내부에서는 count 값을 출력하고 count를 1 증가시킨 뒤, 값이 4보다 크면 반복 실행을 종료
* 코드 실행 방식과 제어권
    - cbFunc(); - 호출 주체 : 사용자, 제어권 : 사용자
    - setInterval(cbFunc,300); - 호출 주체 : setInterval, 제어권 : setInterval

### 4-3
콜백 함수 예제 (2-1) Array.prototype.map

* Array.prototype - array instance가 활용할 수 있는 methods
* Array.prototype.map(callback[, thisArg])
    callback: function(currentValue, index, array)

* 배열 [10,20,30]의 각 요소를 처음부터 하나씩 꺼내서 콜백 함수 실행
    - (1) currentValue : 10, index : 0, return값 : 10+5 
    - (2) currentValue : 20, index : 1, return값 : 20+5
    - (3) currentValue : 30, index : 2, return값 : 30+5 

### 4-4
콜백 함수 예제 (2-2) Array.prototype.map - 인자의 순서를 임의로 바꾸어 사용한 경우

* (예제 4-3) 과 차이 - currentValue 인자의 위치가 두번째이므로 여기에 인덱스값 부여됨 (순서가 중요)

### 4-5
콜백 함수 예제 (2-3) Array.prototype.map - 구현

* A||B - A가 없으면 B를 수행, A가 있으면 A를 수행
* call/apply 메서드 : this에는 thisArg 값이 있을 경우에는 그 값을, 없을 경우에는 전역객체를 지정하고, 1번째 인자에는 메서드의 this가 배열을 가리킬 것이므로 배열의 i번째 요소 값, 2번째 인자에는 i값, 3번째 인자에는 배열 자체를 지정해 호출
* this에 다른 값이 담기는 이유 : 제어권을 넘겨받을 코드에서 call/apply 메서드의 1번째 인자에 콜백 함수 내부에서의 this가 될 대상을 명시적으로 바인딩하기 때문

### 4-6
콜백 함수 내부에서의 this

* setTimeout, addEventListener : Web API
* 사물인터넷을 구현하기 위해 사물에 대한 API를 만들어야 한다. 사물을 customize하기 위해 Web API의 콜백함수를 우리가 작성하고, Web API가 콜백함수의 argument를 자동으로 채운다.
* setTimeout의 this는 window, forEach의 this는 window

### 4-7
메서드를 콜백 함수로 전달한 경우

* 7번째 줄 : 메서드로서 호출 - this는 obj를 가리키므로 인자로 넘어온 1, 2 출력
* 8번째 줄 : forEach 함수의 콜백 함수로서 전달 - obj.logValues가 가리키는 함수만 전달
* 어떤 함수의 인자에 객체의 메서드를 전달하더라도 이는 메서드가 아닌 함수

### 4-8
콜백 함수 내부의 this에 다른 값을 바인딩하는 방법(1) - 전통적인 방식

* obj1.func 메서드 내부 : self 변수에 this 값을 넣음,  익명함수를 선언하고 반환
* 10번째 줄 : obj1.func 호출하면 앞서 선언한 내부함수가 반환되어 callback 변수에 담김
* 11번째 줄 : callbak을 setTimeout 함수에 인자로 전달하면 1000ms(1초) 후 callback 실행, obj1 출력

### 4-9
콜백 함수 내부에서 this를 사용하지 않은 경우

* this를 사용하지 않는 경우 코드가 간결해지지만, 작성한 함수를 this를 사용해서 다양한 상황에 재활용하는 것이 불가능

### 4-10
(예제 4-8) func 함수 재활용

* obj2에 obj1 func 복사
* callback2에 obj2의 func 실행 결과를 넣고 콜백으로 사용
* callback3에 obj1의 func에서 this를 obj3으로 지정하고 실행 결과를 담아 콜백으로 사용

### 4-11
콜백 함수 내부의 this에 다른 값을 바인딩하는 방법(2) - bind 메서드 활용 

* (예제 3-25) 참고 - (ES5) bind 메서드로 this를 객체에 바인딩

* 사물인터넷 개발 과정
    1. 사물 디자인                       Timer
    2. WebAPI design                    setTimeout(CB)
    3. CB의 args를 정해서 Docs에 기술     CB(args[0], args[1], args[2])
    4. user coding CB작성                args[0], args[1], args[2]


### 4-12
콜백 지옥 예시

* 콜백 지옥 (callback hell) : 콜백 함수를 익명 함수로 전달하는 과정이 반복되어 코드의 들여쓰기가 계속 깊어지는 현상
* 동기적 코드 : 현재 실행 중인 코드가 완료된 후에 다음 코드 실행
* 비동기적 코드 : 현재 실행 중인 코드의 완료 여부와 무관하게 즉시 다음 코드 실행 (setTimeout, addEventListener, XMLHttpRequest)

* 0.5초 주기마다 각 콜백은 커피 이름을 전달하고 coffeList에 이름을 추가하여 coffeList 출력

### 4-13
콜백 지옥 해결 - 기명함수로 변환

* (예제 4-12)에서 익명 함수를 기명 함수로 변환하여 들여쓰기를 하지 않고 각각 따로 함수 선언, 호출 
* 문제점 : 일회성 함수로 헷갈릴 소지 있음
* 비동기적인 작업을 동기적인 것처럼 보이게 처리해주는 장치 마련 : (ES6) Promise, Generator (ES2017) async/await

### 4-14
비동기 작업의 동기적 표현(1) - Promise(1)

* new 연산자와 함께 호출한 Promise의 인자로 넘겨주는 콜백 함수는 호출할 때 바로 실행되지만, 그 내부에 resolve 또는 reject 함수를 호출하는 구문이 있을 경우, 둘 중 하나가 실행되기 전까지는 다음(then) 또는 오류구문(catch)으로 넘어가지 않는다
* 비동기 작업의 동기적 표현 : 비동기 작업이 완료될 때 resolve 또는 reject를 호출하는 방법

### 4-15
비동기 작업의 동기적 표현(2) - Promise(2)

* (예제 4-14)에서 반복되는 부분을 함수화하여 간결해짐
* 클로저(closure) : 외부 변수를 기억하고 이 외부 변수에 접근할 수 있는 함수
    - 참고 : https://ko.javascript.info/closure

### 4-16
비동기 작업의 동기적 표현(3) - Generator

* 6번째 줄 : function*() - Generator 함수
* Generator 함수 실행 시 Iterator 반환
* Iterator의 next 메서드 호출 시 Generator 함수 내부에서 가장 먼저 등장하는 yield 에서 함수 실행 멈춤
    - 이후 다시 next 메서드 호출 시 멈췄던 부분부터 시작해서 그 다음의 yield 에서 함수 실행 멈춤
* 비동기 작업이 완료되는 시점마다 next 메서드 호출하여 generator 함수 내부의 소스가 순차적으로 진행

### 4-17
비동기 작업의 동기적 표현(4) - Promise + Async/await

* 비동기 작업을 수행하고자 하는 함수 앞에 async, 함수 내부에서 비동기 작업이 필요한 위치에 await 작성
    - 뒤의 내용을 Promise로 자동 전환하고 해당 내용이 resolve 된 후에 다음 진행 (Promise then과 비슷)

## Ch5
### 5-1
외부 함수의 변수를 참조하는 내부 함수(1)

* 클로저(closure) : 클로저는 함수와 그 함수가 선언될 당시의 lexical environment의 상호관계(combination)에 따른 현상
    - 선언될 당시의 lexical environment : 실행 컨텍스트 중 outerEnvironmentReference

* outer 함수에서 변수 a 선언, 내부함수 inner 에서 a 값을 1 증가하고 출력
* inner 함수 내부에서 a 선언하지 않았으므로 environmentRecord에서 값을 찾지 못함
    - outerEnvrionmentReference에 지정된 상위 컨텍스트인 outer의 LexicalEnvironment에 접근해서 a 찾음
    - outer 함수의 실행 컨텍스트가 종료되면 LexicalEnvironment에 저장된 identifier(a, inner)에 대한 참조가 지워짐
    - 각 주소에 저장된 값들은 참조하는 변수가 없어져서 garbage collection(GC)의 대상이 됨

### 5-2
외부 함수의 변수를 참조하는 내부 함수(2)

* 6번째 줄 : inner 함수 실행 결과 리턴 - outer 함수의 실행 컨텍스트가 종료될 때 a를 참조하는 대상이 없어져서 GC 대상이 됨
* (예제 5-1)과 (예제 5-2) 공통점
    - outer 함수의 실행 컨텍스트 종료 이전 inner 함수의 실행 컨텍스트가 종료
    - outer 실행 컨텍스트 종료 후 별도로 inner 함수를 호출할 수 없음

### 5-3
외부 함수의 변수를 참조하는 내부 함수(3)

* 6번째 줄 : inner 함수 실행 결과가 아니라 inner 함수 자체를 반환
    - outer 함수의 실행 컨텍스트가 종료될 때 outer2 변수는 outer 실행 결과인 inner 함수 참조
* 9번째 줄 : outer2 호출하면 inner 실행
* inner 함수의 실행 컨텍스트의 environmentRecord에는 정보가 없음
* outerEnvironmentReference에는 *inner 함수가 선언된 위치의 LexicalEnvironment*가 참조복사됨
    - inner 함수는 outer 함수 내부에서 선언되었으므로 outer 함수의 Lexical Environment
* scope chain에 따라 outer에서 선언한 변수 a에 접근해서 1 증가하여 반환 (= 2)
* 10번째 줄 : outer2 다시 호출 - a 값 1 증가하여 반환 (= 3)

* inner 함수의 실행 시점에는 outer 함수는 실행이 종료된 상태이지만 outer 함수의 LexicalEnvironment에 접근할 수 있음
 - 가비지 콜렉터는 어떤 값을 참조하는 변수가 하나라도 있으면 수집 대상에 포함시키지 않음

* 클로저란 어떤 함수 A에서 선언한 변수 a를 참조하는 내부함수 B를 외부로 전달할 경우 A의 실행 컨텍스트가 종료된 이후에도 변수 a가 사라지지 않는 현상

### 5-4
return 없이도 클로저가 발생하는 다양한 경우

1. 별도의 외부객체인 window의 메서드(setTimeout/setInterval)에 전달할 콜백 함수 내부에서 지역변수를 참조 
2. 별도의 외부객체인 DOM의 메서드(addEventListener)에 등록할 handler 함수 내부에서 지역변수를 참조

### 5-5
클로저의 메모리 관리

* (예제 5-3), (예제 5-4) 코드에 메모리 해제 코드를 추가
* 클로저의 메모리 소모
    - 필요성이 사라진 시점에 더 메모리를 소모하지 않게 해서 해결
    - 참조하는 대상을 없애서 GC의 대상이 되도록 함(메모리 회수)
    - 식별자에 참조형이 아닌 기본형 데이터(null/undefined) 할당

### 5-6
콜백 함수와 클로저(1)

* 콜백 함수를 내부함수로 선언해서 외부변수를 직접 참조하는 방법
* (A) : forEach 메서드에 넘겨준 콜백 함수 - 내부에서 외부 변수를 사용하지 않고 있으므로 클로저 없음
* (B) : addEventListener에 넘겨준 콜백 함수 - fruit라는 외부 변수를 참조하고 있으므로 클로저 있음

* (A) 는 fruits 개수만큼 실행되며, 그때마다 실행 컨텍스트가 활성화
* (A) 실행 종료 여부와 무관하게 클릭 이벤트에 의해 각 컨텍스트의 (B) 실행
    - (B)의 outerEnvironmentReference가 (A)의 LexicalEnvironment를 참조
    - fruit는 (A)가 종료된 후에도 GC 대상이 되지 않음

### 5-7
콜백 함수와 클로저(2)

* (예제 5-6)에서 (B)함수의 사용이 콜백 함수에 국한되지 않으므로 외부로 분리
    - 콜백 함수를 외부로 꺼내서 alertFruit 변수에 담음
* 14번째 줄 :  fruits[1]에 해당하는 'banana'알림이 출력
* li 클릭 시 (예제 5-6)에서 클릭한 이름이 출력된 것과 달리 [object PointerEvent] 로 출력됨
    - 콜백 함수의 인자에 대한 제어권을 addEventListener가 가진 상태이며, addEventListner는 콜백 함수를 호출할 때 첫 번째 인자에 이벤트 객체를 주입하기 때문

### 5-8
콜백 함수와 클로저(3)

* bind 메서드 활용한 방법
    - (예제 5-7) 문제 해결되었으나, 이벤트 객체가 인자로 넘어오는 순서가 바뀜, 함수 내부에서의 this가 원래와 달라짐

### 5-9
콜백 함수와 클로저(4)

* 고차함수 활용한 방법
* 4번째 줄 : alertFruitBuilder 함수 - 내부에서 다시 익명함수 (이전 alertFruit) 반환
* 12번째 줄 : alertFruitBuilder 함수 실행, fruit 값 인자로 전달
    - 함수의 실행 결과가 다시 함수로 반환되고 콜백 함수로써 전달됨 
* alertFruitBuilder 실행 결과로 반환된 함수에는 클로저가 존재
    - 클릭 이벤트가 발생하면 함수의 실행 컨텍스트가 열리면서 인자로 전달된 fruit 값을 outerEnvironmentReference에 의해 참조할 수 있음

### 5-10
자동차 객체 예시

* 접근 권한 제어(정보 은닉, information hiding)
    - public(외부접근 가능), private(내부에서만 사용 가능), protected
    - 외부에 제공하고자 하는 정보는 return - public member
    - 내부에서만 사용할 정보는 return 하지 않음 - private member

* 자동차 경주 게임을 위한 자동차 객체 예시
    - fuel(연료량), power(연비), moved(총 이동거리)
    - run 메서드 실행할 때마다 car 객체의 fuel, moved 값이 변하게 됨
    - car 객체를 게임 참가자 수 만큼 생성하고 각자의 턴에 run 실행
    - 참가자가 랜덤으로 정해지는 값을 지정해서 바꿔버릴 수 있는 문제

### 5-11
클로저로 변수를 보호한 자동차 객체(1)

* creatorCar 함수 실행하여 객체 생성
    - feul, power 변수는 private로 지정
    - moved 변수는 getter 부여해서 읽기 전용 속성
    - 외부에서는 run 메서드 실행, 현재의 moved 값 확인만 가능

### 5-12
클로저로 변수를 보호한 자동차 객체(2)

* (예제 5-11)에서 run 메서드를 다른 내용으로 덮어씌우는 어뷰징은 가능한 상태
    - 객체를 return하기 전에 미리 변경할 수 없도록 보완 

* 클로저를 활용해 접근권한을 제어하는 방법
    1. 함수에서 지역변수 및 내부함수 등을 생성
    2. 외부에서 접근권한을 주고자 하는 대상들로 구성된 참조형 데이터를 return

### 5-13
bind 메서드를 활용한 부분 적용 함수

* 부분 적용 함수 (partially applied function) : n개의 인자만 넘겨 기억시켰다가, 나중에 (n-m) 개의 인자를 넘기면 비로소 원래 함수의 실행 결과를 얻을 수 있게 하는 함수

* addPartial 함수 : 인자 5개를 미리 적용하고, 추가적으로 인자들을 전달하면 모든 인자를 모아 원래의 함수가 실행되는 부분 적용 함수
    - add 함수는 this를 사용하지 않으므로 bind 메서드만으로도 구현됨

### 5-14
부분 적용 함수 구현(1)

* 1번째 인자에는 원본 함수, 2번째 인자 이후부터는 미리 적용할 인자들을 전달, 반환할 함수(부분 적용 함수)에서는 나머지 인자들을 받아서 원본 함수를 호출
* 실행 시점의 this를 그대로 반영하여 this에는 아무런 영향을 주지 않음

### 5-15
부분 적용 함수 구현(2)

* 비워놓은 공간임을 표시하기 위해 전역객체로 '_' 프로퍼티 - 삭제/변경 등 접근에 대한 방어
* 17~21번째 줄 : 처음에 넘겨준 인자들 중에 _로 비워놓은 공간마다 나중에 넘어온 인자들이 순서대로 들어감
* 부분 적용 함수를 만들 때 미리 실행할 함수의 모든 인자 개수를 맞춰 빈 공간을 확보하지 않아도 됨

### 5-16
부분 적용 함수 - 디바운스

* 디바운스(debounce)
    - 짧은 시간 동안 동일한 이벤트가 많이 발생한 경우, 이를 전부 처리하지 않고 처음 또는 마지막에 발생한 이벤트에 대해 한 번만 처리하는 것
    - 프런트엔드 성능 최적화에 도움
    - scroll, wheel, mousemove, resize 등 적용하기 좋음

* 1번째 줄 : debounce 함수는 출력 용도로 지정한 eventName과 실행할 함수, 마지막으로 발생한 이벤트인지 여부를 판단하기 위한 대기시간을 받음
    - 내부에서 timeoutId 변수 생성, 클로저로 EventListener에 의해 호출될 함수 반환
* 4번째 줄 : setTimeout을 사용하기 위해 this를 별도의 변수 self에 담음
* 6번째 줄 : 무조건 대기 queue를 초기화 (clearTimeout)
* 7번째 줄 : setTimeout으로 wait 만큼 지난 후 원래 func를 호출

* 최초 event가 발생하면 7번째 줄에 의해 timeout의 대기열에 wait 시간 뒤에 func를 실행할 것이라는 내용이 담김
    - wait 시간 지나기 전에 동일한 event 발생하면 6번째 줄에 의해 앞서 저장했던 대기열을 초기화하고 7번째 줄에서 새로운 대기열 등록
    - 각 event가 바로 이전 event로부터 wait 시간 이내에 발생하면 마지막에 발생한 이벤트만 초기화되지 않고 실행됨
* debounce 함수에서 클로저로 처리되는 변수 : eventName, func, wait, timeoutId

* 실행 결과 : 마우스 포인터 움직임 횟수에 따라 move event 발생 횟수가 카운트 됨

### 5-17
커링 함수(1)

* 커링 함수(currying function) : 여러 개의 인자를 받는 함수를 하나의 인자만 받는 함수로 나눠서 순차적으로 호출될 수 있게 체인 형태로 구성한 것
    - 한 번에 하나의 인자만 전달하는 것이 원칙
    - 중간 과정상의 함수를 실행한 결과는 다음 인자를 받기 위해 대기하고, 마지막 인자가 전달되기 전까지는 원본 함수 실행되지 않음
    - 필요한 인자 개수만큼 함수를 만들어 계속 리턴하면 되므로 간편하지만 인자가 많아지면 들여쓰기가 깊어지는 문제

* 부분 적용 함수는 여러 개의 인자를 전달할 수 있고, 실행 결과를 재실행할 때 원본 함수가 무조건 실행됨

### 5-18
커링 함수(2)

* (ES6) 화살표 함수로 구현하면 커링 함수를 간단히 표기 가능
    - 각 단계에서 받은 인자들을 모두 마지막 단계에서 참조할 것이므로 GC 대상이 되지 않고 메모리에 쌓였다가 마지막 호출로 실행 컨텍스트가 종료되면 한꺼번에 GC 대상이 됨

* 자연실행 (lazy execution) - 함수형 프로그래밍 표현
    - 당장 필요한 정보만 받아서 전달하는 방식 - 마지막 인자가 넘어갈 때 까지 함수 실행을 미루는 것
    - 커링 함수 활용하기 적합
* 프로젝트 내에서 자주 쓰이는 함수의 매개변수가 항상 비슷하고 일부만 바뀌는 경우 활용 예시
* HTML5의 fetch 함수 - url 받아서 해당 url에 HTTP 요청
    - 서버에 정보를 요청할 필요가 있을 때마다 매번 baseUrl 부터 입력할 필요 없음 (baseUrl은 보통 몇 개로 고정됨), 특정한 값(id)으로 서버 요청

```js
var getInformation = function (baseUrl) {
    return function (path) {
        return function (id) {
            return fetch(baseUrl + path + '/' + id);
        };
    };
};
// var getInformation = baseUrl => path => id => fetch(baseUrl + path + '/' + id);

var imageUrl = 'http://image.com/';
var productUrl = 'http://product.com/';

//이미지 타입별 요청 함수 준비
var getImage = getInformation(imageUrl);
var getEmoticon = getImage('emoticon');
var getIcon = getImage('icon');

//제품 타입별 요청 함수 준비
var getProduct = getInformation(productUrl);
var getFruit = getProduct('fruit');
var getVegetable = getProduct('vegetable');

//실제 요청
var emoticon1 = getEmoticon(100);
var emoticon2 = getEmoticon(102);
var icon1 = getIcon(205);
var icon2 = getIcon(227);
var fruit1 = getFruit(300);
var fruit2 = getFruit(400);
var vegetable1 = getVegetable(901);
var vegetable1 = getVegetable(942);
```
* 최근 여러 프레임워크나 라이브러리 등에서 커링을 광범위하게 사용하고 있음

```js
const logger = store => next => action => {
  console.log('dispatching',action);
  console.log('next state',store.getState());
  return next(action);
};
const thunk = store => next => action => {
  return typeof action === 'function'
  ?action(dispatch, store.getState)
  : next(action);
};
```
* Flux 아키텍처 구현체 중 Redux middleware
    - store, next는 한 번 생성된 후로 바뀌지 않는 속성, action은 매번 변경되는 속성
    - store, next 값이 결정되면 Redux 내부에서 logger 또는 thunk에 값을 미리 넘겨서 반환된 함수를 저장
    - 이후 action만 받아서 처리

## Ch6
### 6-1
Person.prototype

* 생성자 함수(constructor)로 new 키워드와 함께 객체를 생성하면 인스턴스의 __proto__는 자동으로 해당 생성자의 prototype을 참조함
* Person.prototype에는 인스턴스들이 공유하는 메서드가 담기며, suzi.__proto__가 Person.prototype을 참조하므로 getName() 등 메서드에 접근 가능.
* __proto__는 생략 가능하므로 suzi.getName()처럼 바로 호출 가능. 이때 this는 suzi를 가리킴

### 6-2
prototype과 __proto__

* 생성자 함수는 prototype 프로퍼티를 가지고 있고, 그 안에는 메서드나 프로퍼티가 정의됨.
* 인스턴스는 __proto__를 통해 생성자의 prototype과 연결되고, 이 구조를 통해 상속이 이루어짐.

### 6-3
constructor 프로퍼티

* 인스턴스의 __proto__나 생성자의 prototype 안에는 constructor라는 속성이 있어서, 해당 인스턴스를 만든 생성자 함수를 참조할 수 있음.

### 6-4
constructor 변경

* constructor는 객체에 따라 변경 가능하지만, 변경해도 이미 생성된 인스턴스의 구조가 바뀌는 건 아님.
* 생성자 정보를 constructor로 추적하는 건 신뢰성이 떨어질 수 있음.

### 6-5
다양한 constructor 접근 방법

* p1, p2, p3, p4, p5 모두 Person의 인스턴스임

* 아래는 모두 동일한 대상을 가리킴
```js
[Constructor]
[instance].__proto__.constructor
[instance].constructor
Object.getPrototypeOf([instance]).constructor
[Constructor].prototype.constructor
```
* 아래는 모두 동일한 객체(prototype)에 접근할 수 있음
```js
[Constructor].prototype
[instance].__proto__
[instance]
Object.getPrototypeOf([instance])
```

### 6-6
메서드 오버라이드

* 메서드 오버라이드 : 메서드 위에 메서드를 덮어씌웠다는 표현
    - getName이라는 메서드를 찾는 방식은 가장 가까운 대상인 자신의 프로퍼티를 검색하고, 없으면 그 다음으로 가까운 대상인 __proto__를 겁색하는 순서로 진행
* 인스턴스에 메서드를 오버라이드하면, 프로토타입 체인보다 우선 검색되므로 해당 메서드가 실행됨.
* prototype의 메서드를 직접 호출하면 this가 prototype을 가리켜 원하는 결과가 나오지 않을 수 있음 → call/apply로 this를 바꿔서 해결.

### 6-7
배열에서 배열 메서드 및 객체 메서드 실행

* 메서드는 우선 자기 자신에게서 찾고, 없으면 __proto__를 따라가며 검색함. 이를 프로토타입 체이닝이라 부름.

### 6-8
메서드 오버라이드와 프로토타입 체이닝

* 배열(arr)은 Array.prototype을 상속하고, 그 위로 Object.prototype까지 체이닝됨.
* toString()은 이런 체인을 따라가며 실행됨.

### 6-9
Object.prototype에 추가한 메서드에의 접근

* Object.prototype에 메서드를 추가하면 대부분의 데이터 타입에서 사용할 수 있음.
* 반대로 Object 생성자 함수에 메서드를 붙이면 static이므로 인스턴스에서는 호출 불가능.

### 6-10
Grade 생성자 함수와 인스턴스

* Grade는 유사 배열 객체로, 배열처럼 인덱스와 length를 가지지만 배열 메서드를 쓰려면 별도 처리가 필요함.
* 배열 메서드를 사용하려면 call/apply 또는 Grade.prototype을 Array.prototype과 연결해야 함.

## Ch7
### 7-1
Static & prototype method

* prototype method는 인스턴스에서 호출 가능.
* static method는 생성자 함수 자체에서만 호출 가능. 인스턴스에서는 접근 불가.

### 7-2
(예제 6-10) Grade 생성자 함수 및 인스턴스

* Grade는 배열처럼 보이지만 prototype 구조 상 배열이 아님.
* 클래스에 구체적인 데이터를 담으면 인스턴스에 영향을 줄 수 있어, 바람직하지 않음.

### 7-3
length 프로퍼티를 삭제한 경우

* Grade 인스턴스의 length는 삭제 가능.
* 삭제하면 push() 시 prototype 체인에 있는 length를 사용함 → 이상한 결과 초래.

### 7-4
요소가 있는 배열을 prototype에 매칭한 경우

* 클래스의 prototype에 값을 넣으면 인스턴스에 영향을 줌.
* 클래스는 데이터를 가지지 말고 메서드만 가져야 함.

### 7-5
Rectangle, Square 클래스

* Rectangle, Square 클래스 각각 getArea() 메서드 가짐.
* Square는 Rectangle을 상속하도록 설계 가능.

### 7-6
Square 클래스 변형

* Square 클래스에서 height를 width와 동일하게 설정하면 상속 구조가 더 깔끔해짐

### 7-7
Rectangle 클래스를 상속하는 Square 클래스

* Square.prototype = new Rectangle()으로 상속 가능하지만, constructor가 바뀜
* prototype에 데이터가 있어도 인스턴스에 영향 미침 → 문제 발생

### 7-8
클래스 상속 및 추상화 방법(1) - 인스턴스 생성 후 프로퍼티 제거

* Square.prototype에서 데이터 제거하고 동결(freeze)해 변경 방지.
* 클래스는 오직 메서드만 포함되도록 유지하는 방식.

### 7-9
클래스 상속 및 추상화 방법(2) - 빈 함수를 활용

* 중간에 빈 함수(Bridge)를 사용해 prototype 연결 → prototype 상에 인스턴스가 없어지고 구조가 깔끔해짐.
* 즉시실행함수 내부에서 Bridge를 선언해서 이를 클로저로 활용 - 메모리에 불필요한 함수 선언 줄임

### 7-10
클래스 상속 및 추상화 방법(3) - Object.create 활용

* Object.create(SuperClass.prototype)을 통해 prototype 연결 → SuperClass의 인스턴스를 만들지 않아도 됨.

### 7-11
클래스 상속 및 추상화 방법 - 완성(1) - 인스턴스 생성 후 프로퍼티 제거

* (예제 7-8)~(예제 7-10)은 기본적인 상속에 성공했지만 SubClass 인스턴스의 constructor는 여전히 SuperClass를 카리키는 상태
    - SubClass 인스턴스, SubClass.prototype 에는 constructor가 없음 -> SubClass.prototype.constructor가 원래 SubClass를 가리키도록 수정

(예제 7-8) 수정
```js
SubClass.prototype.constructor = SubClass;
```

### 7-12
클래스 상속 및 추상화 방법 - 완성(2) - 빈 함수를 활용

(예제 7-9) 수정
```js
SubClass.prototype.consturctor = SubClass;
Bridge.prototype.constructor = SuperClass;
```

### 7-13
클래스 상속 및 추상화 방법 - 완성(3) - Object.create 활용

(예제 7-10) 수정
```js
SubClass.prototype = Object.create(SuperClass.prototype);
SubClass.prototype.constructor = SubClass;
```

### 7-14
상위 클래스 접근 수단인 super 메서드 추가

* 하위 클래스에서 상위 클래스의 프로토타입 메서드에 접근하고자 할 때, 다른 객체지향 언어들의 클래스 문법 중 super 모방
* (예제 7-13) 에 super 메서드 추가
    - 인자가 비어있을 경우 SuperClass 생성자 함수에 접근하는 것으로 간주, this가 변경되지 않도록 클로저 활용
    - SuperClass의 portotype 내부의 propName에 해당하는 값이 함수가 아닌 경우 그대로 반환/ 함수인 경우 클로저 활용, 매서드에 접근
* SuperClass의 생성자 함수에 접근하고자 할 때는 this.super()
    - SuperClass의 프로토타입 메서드에 접근하고자 할 때는 this.super(propName)
* sq.getArea() 호출 시 SubClass의 메서드 실행 ('size is : 100')
    - sq.super('getArea')() 호출 시 SuperClass 메서드 실행 ('100')
* super()를 직접 구현해 상위 생성자나 메서드 호출 가능하게 함.
* 함수형 언어 스타일로 상위 메서드 접근을 가능하게 만드는 패턴.

### 7-15
ES5와 ES6의 클래스 문법 비교

* ES6 클래스는 class, constructor, static, method 등 문법 제공
* function 키워드 없이도 메서드 정의 가능 / static은 생성자 함수에서만 사용 가능

### 7-16
ES6의 클래스 상속

* extends, super 키워드로 상속 처리
* super()는 상위 생성자 호출, super.method()는 상위 메서드 호출
* ES5보다 훨씬 간결하고 명확한 클래스 구조 제공
