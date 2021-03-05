
# FrontEndStudy

http://webberstudy.com/html-css/html-1/head-element/

--------------------------------------------------
# React

SPA : 단일 페이지 어플리케이션
1. 모든 정적리소스를 최초에 다운로드 : 초기 구동 느림
2. 트래픽 감소, 속도, 사용성, 반응성 향상
3. 서버 렌더링 : 


#Component : 특정 코드 뭉치를 이식.재사용하기 위해 사용하는 코드 블록 단위
1.생명 주기 : 생성, 변경, 소멸 과정
##Component 생성 과정
  1. render()
   - 화면 내용이 변경되어야 할 시점 호출. return되는 html형식의 코드 그려줌
  2. constructor(props)
   - 가장 먼저, 처음 한 번만 호출, state선언, props초기화 (super(props)) 
  3. getDerivedStateFormProps(props, state)
   - constructor() 다음으로 실행. 컴포넌트가 새로운 props를 받게 됐을 때 state를 변경해 줌
  4. componentDidMount()
   - ‘생성’중 가장 마지막으로 실행. 화면이 모두 그려진 후 실행되어야 하는 이벤트 처리, 초기화 등
* constructor -> rener -> getderivedStateFormProps -> componentDidMount

* Component 변경 과정
  * Props나 State의 변경
  * shouldComponentUpdate(props, state)
* jquery
  * var($‘inputId’).val();
  * render의 return함수 내 html코드에서 inputId의 id에 해당하는 태그의 VALUE값 참조

* props
  * 부모 컴포넌트가 자식 컴포넌트에 데이터를 전달할 때 사용
  * 자식 컴포넌트에선 데이터 수정 불가 (state에 넣어서 변경해야함)
```
className.defaultProps = {
a : ‘a’,
b: 400
}
```
* state값을 update할때 불변성을 유지해야하는 이유
  * shouldcomponentupdate로 성능 조절 (업데이트 해야할때만)
  * {return true; }-> 기본
  * this.setstate를 사용
  * const anotherArray = [...array,3];
  * const anotherArray2 = array.concat(4);
* 불변성 : 객체가 생성된 이후 그 State를 변경할 수 없는 디자인 패턴
  * 의도치 않은 특정 객체가 변경되면 참조하고 있던 객체도 변경이 일어남. side-effect가 발생할 확률과 프로그램 복잡도가 높아짐
  * 변경이 일어난 객체의 프로퍼티만 비교함으로써 최적화 가능(shouldComponentUpdate)
  * 실제로 DOM을 제어하는 것이 아니라 가상의 DOM을 두고 관리함
  * 프레임워크들의 Model
  * 프론트엔드 라이브러리
  * 데이터가 바뀌면 그냥 뷰를 날려버리고(Mutation 하지말고) 새로 만들자

* Virtual DOM
  * JS로 이루어진 가상의 돔. DOM과 비교하여 바뀐부분만 바꿔줌
  * state를 직접 변경하면 forceUpdate() 함수를 사용해야 render가 호출됨
* 함수형 컴포넌트
  * render함수 없이 return만으로 화면을 그려줌
  * hook -> useState(), useEffect()
* <Fragment > </>
  * 하나의 태그로 전체를 감싸지 않으면 에러나므로
* fetch
  * GET : 데이터를 조회해 가져와 사용
  * POST : 서버의 상태나 데이터를 변경하는 수행작업에 사용
  * await fetch
* axios
  * axios.get(http).then(function)
  * post는 response에 호출결과 반환
* Promise
  * then : 이행시
  * catch : 거부시
* onChange
  * 특정 element에 변화가 생겼을 때
* onMouseMove
  * 특정 tag영역 안에서 마우스 커서가 움직일 때
* Ref
  * element가 참조하는 변수에 접근해 변경하고 제어
* 커링
  * 함수의 재사용성을 높이기 위해 함수 자체를 return하는 함수
* 하이오더 컴포넌트
  * 컴포넌트를 인자로 받거나 반환하는 함수
* 컨텍스트API
  * 데이터의 공급자, 소비자를 정의하고 데이터가 필요한 컴포넌트만 사용할 수 있게 구현 가능

-------------------
# Redux
https://wooder2050.medium.com/%EB%A6%AC%EB%8D%95%EC%8A%A4-redux-%EB%8A%94-%EC%99%9C-%EC%93%B0%EB%8A%94-%EA%B1%B4%EB%8D%B0-2eaafce30f27
https://react.vlpt.us/redux/01-keywords.html
* 상태관련 로직들을 파일로 분리해 효율적으로 관리 가능
* action
  * 상태에 변화 필요시 발생. 하나의 객체로 표현
  * type필드가 있어야 함.
* Action Creator
  * 액션 만드는 함수
  * 일반적으로 export하여 다른 파일에서 불러와 사용
* reducer
  * 변화를 일으키는 함수
  * 현재 상태, 전달받은 액션 참고 새로운 상태 반환
* store
  * 한 애플리케이션 당 하나의 스토어
  * 현재의 앱 상태, 리듀서, 몇 내장함수 포함
* 디스패치
  * 스토어 내장함수 중 하나
  * 액션을 발생시키는 것 dispatch(action)
* subscribe
  * 스토어 내장함수 중 하나
  * 함수 형태의 값을 파라미터로 받아옴
  * 액션이 디스패치 되었을 때마다 전달해준 함수 호출
  * 보통 요거 대신 connect또는  useselector Hook을 사용해 구독함
* 리덕스 3규칙
  * 1애플리케이션 1스토어
  * 상태는 읽기전용
  * 새로운 객체/배열 만들어 교체하는 방식
  * 데이터 변경 감지를 더 간단히 하기 위해서 (얕은복사-깊은복사) 불변성을 유지함
  * 리듀서는 순수한 함수
    * 이전 상태(외부 상태)는 건드리지 않고, 변화를 일으킨 새로운 상태 객체를 만들어 반환
    * 똑같은 파라미터로 호출된 리듀서는 언제나 똑같은 결과를 반환해야함
  * const store = createStore(reducer-function)





* 라우팅
  * 호출되는 url에 따라 페이지(view)이동을 설정하는 것

* StateContext
  * 일반적으로 값을 자손에게 전달하는  방법은 하향식
  * 이를 해결하는 방법은 flux, reflux, redux, mobx
  * ContextAPI로 트리의 모든 레벨에 값을 공유
* React.createContext(defaultValue)
  * <.Provider value = {}>
  * Provider의 Value는 하위 모든 Consumer에서 사용 가능
  * Provider의 하위 모든 Consumer는 Provider의 value가 변경될때마다 재랜더링
  * Hook의 useContext(MyContext) - Context 객체의 value 가져옴

---------------------
# HTML
* <!doctype html> 문서 유형 선언
* 블록 요소 : 줄바꿈이 기본적으로 일어남, 영역의 너비가 상위 영역의 전체 너비만큼 되는 요소
* 인라인 요소 : 줄바꿈 x, 블록 요소와 반대. a, img, strong, span 등
* head : 브라우저에게 정보를 주는 태그
* meta : 문자 세트를 비롯한 문서 정보
* <meta charset=”UTF-8”>
* a
  * 링크로 이동
  * 링크의 타겟 (일반적으로  ID 사용 권장)
* img
  * alt 속성 : 불러들이지 못했을 때 나오는 내용
* ol
  * 순서가 있는 요소
  * li : ol안엔 이것만 가능,  li안에는 ol 중첩 가능
* div : 의미없는 요소. 블록 요소
* span : 의미없는 요소. 인라인 요소
* class : 한 요소에 여러개 가능. css에서 선택자로 사용 (.hello)
* id : 페이지에서 딱 한번만 가능(고유값)
* 주석 : <!--  →
* 표준화 : 여러 규격등을 표준을 정해서 제한하고 통일하는 것
  * HTML (의미) CSS (외형) JS (동작)
  * 열고 닫는 태그를 온전히 닫는 것
  * 블록 요소를 인라인 요소에 넣지 않는 것
* doctype
  * 가장 먼저 선언
  * 어떤 문서의 타입을 사용하는지 선언 (HTML, XHTML등)
* 비사용 권장
  * font, center - CSS로 사용할 것
  * iframe : 프레임 내 다른 웹페이지 사용
  * big, small
  * i, b, s
* abbr
  * 축약어를 나타냄
* dfn
  * 개념(단어)의 정의
* code
  * 프로그래밍 소스 표현
* table
  * tr : 행
  * td : 셀
  * colspan : 열 합침 <td colspan=”2”>참가자</td>
  * rowspan : 행(세로)합침
  * caption : 표의 제목
  * scope : th 요소에서 사용. 어느 셀에 영향 미치는가 지정
http://webberstudy.com/html-css/html-2/table-symactic/




---------------------------------
# CSS
* 태그 : 태그 그 자체
* 요소 : 태그가 적용 된 것
* 선택자
  * 요소 : p, h1등
  * ID : #abc
  * class : .abc
  * 중첩가능 (p.box
  * 묶음 : h1, div, p {}
  * 후손 : .box2 .name {} (box2요소 안에 name요소 선택)
  * 묶음 & 후손 : .box1 .name, .box2 .name
  * 우선순위
    * 나중 우선
    * 후손 선택자라면 더 많은 단계로 표현된 선택자
    * 다른 단일 선택자보다 ID가 우선
    * 스타일이 안겹치면 그 스타일이 없어지진 않음
  * 자식 선택자 : > (.contry > span
  * 인접 형제 선택자 : + p+p (P요소 다음에 오는 p 요소를 선택)
  * 일반 형제 선택자 : ~
  * 가상 클래스 선택자
    * :link - href 속성 갖고있는 요소 선택
    * :visited : 링크 중 방문한 링크
    * :hover : 호버 상태
    * :active : 클릭 상태

* font-family : 서체
* text-decoration : 밑줄, 취소선 등
* 상대주소 : 현재 파일 기준 (../)
* 절대주소
* background-repeat : 이미지로 넣은걸 반복할건지
    * position
    * px : 절대값
    * % 이미지 기준 상대값
    * left, right : x축
    * top, bottom : y축
    * inherit : 부모 속성 상속받음
    * 인라인, 블록 요소의 background 차이

* border(테두리)
  * 네 가지 방향 : border-top, right, left, bottom
  * border-top-width : 3px
* em : 상재거인 단위. 글자 크기 기준
* 박스모델
  * margin : 요소와 요소와의 간격 (바깥 여백)
  * padding : 요소 안 (내부 여백)
  * width, height : 블록요소만 적용 가능
* 리스트 스타일
  * list-style-type
* 크로스 브라우징 : 모든 브라우저에서 잘 나오게끔 하는 작업
  * 브라우저 엔진 (레이아웃 엔진)
  * 브라우저를 렌더링함
  * 크로스를 위해 엔진 파악 필요
  * 브라우저 자체적으로 CSS 스타일을 가지고 있음
  * CSS 초기화 : 차이점을 편하게 작업
  * { margin : 0, padding : 0}
  * 초기화에 너무 많은 스타일x
  * 속성의 상속을 무시하게 만들지 말 것
* link : 공통 초기화 (스타일 시트 여러개) - 다중 스타일 시트
* display
  * 요소를 어떻게 보여줄지 지정하는 속성 (block, inline)
  * display: none vs visibility: hidden
  * 후자는 해당 영역을 남겨놓음(빈공간)
* overflow
  * 컨텐츠가 넘칠때
* float
  * http://webberstudy.com/html-css/css-2/float-layout/
  * 이미지 등 요소를 띄워서 왼쪽이나 오른쪽에 배치
  * 스타일을 준 요소의 상위 요소가 해당 요소를 온전히 감쌀수 있도록
* clear
  * 이미지 아래에서 새로운 섹션 시작

---------------------------------

# 자바 스크립트
* var, let, const
  * var : 재선언, 재할당 가능
  * let : 재할당 가능
  * const : 둘 다 불가
* … (전개 연산자)
* map vs. foreach : map은 기존배열 건드리지 않고 반환
  * Map_arr.map(x=>x*2)


* 변수 : 값을 넣어놓는 공간
* 자료형
  * 원시 타입
    * 숫자형(Infinity - 가장 큰 수, NaN - 너무 큰 값, 유효하지 않은 값), 문자형, 불린형, 심볼형, null(비어있는 값), undefined(변수 정의, 아무 값도 할당받지 않은 상태)
  * 참조 타입
    * 객체 (속성들의 집합) 순서도 크기도 고정되어있지 않음
    * 값의 메모리 주소를 변수에 할당하여 값을 참조함
* for-in
  * for (var item in store)
* 객체
  * 값들을 그룹으로 묶은 데이터 모음
  * 키와 값 한쌍 -> 속성(Property)
  * 1Key 1Value
  * JSOn과 유사한 구조
* 단축 속성명
  * var family = {address, members, addFamily, getHeadcount};
  * 비구조화할당 : 배열이나 객체의 값을 새로운 변수에 할당
* 심볼형
  * Symbol(‘key’) -> 늘 고유한 값 반환

* 예외 처리
  * throw -> try-catch-finally 실행 블록 빠져나감
  * arguments: (전달인자) : 함수가 호출될 때 전달되는 값, 매개변수 : 함수 선언 시 작성되는 변수
* 나머지 매개변수
  * function(parameter, ...restParameter) {}
* 스코프
  * 변수와 매개변수가 어디까지 유효한지
  * 렉시컬 스코프 : JS. 코드 작성 시점에 스코프 결정
* 함수 호이스팅
  * 해석-실행 으로 나눔. 해석 단계에서 선언 문장 초기화&스코프 형성 -> 실행 단계에서 값을 할당, 계산
  * 함수를 선언하기 전에 호출 가능

* 스코프 체인
  * 실행 컨텍스트 : 코드가 실행되기 위해 필요한 정보 가지고 있음
  * Stack 이용
  * 렉시컬 환경
```
ExcutionContext = {
LexicalEnvironment: {
EnvironmentRecord: {
},
OuterLexicalEnvironment: 참조 -> 각 실행 컨텍스트가 체인처럼 연결
}
}
```

* 클로저
  * 함수가 정의될 때의 렉시컬 환경을 기억하는 함수
  * const counter1 = createCounterClosure();
* 속성 기술자
  * 자기 자신에 대한 정보를 담고 있음
  * JS의 모든 객체 속성이 가지고 있음
```
let user = {};
Object.getOwnPropertyDescriptor
Object.defineProperty(user, “age”, {
get : function() {return this._age},
set : function (age) {;;;;}
enumerable: true
```
* get set을 통해 속성접근 관리 가능
* 객체지향 프로그래밍
  * 프로그램들을 객체들로 구성하고 객체들 간에 서로 상호작용하도록 작성하는 방법
  * 객체는 특징적인 행동(메소드)과 변경 가능한 상태(외 다른값)를 가짐
* classification : 타입을 정의하는 작업
* Prototype : 모든 객체는 다른 객체의 원형이 될 수 있음 (__proto__설정)

* 생성자 함수
  * function Teacer(name, age, subject) { this.name=name;;;;}
* class
  * 상속 : extends
* static 정적 메소드


* this
  * 생성자 : 객체 내부 가리킴 (객체 자신이 됨)
  * 객체 안 메소드 : 객체 자신 (해당 메서드를 호출한 객체로 바인딩)
  * 일반 함수 : 전역 객체
  * 람다 함수 : 부모 환경. bind를 통해 변경 불가 (상위 스코프)
  * bind : var func2 = function(val1, val2) {}.bind(this, 'param1', 'param2')
  * call : func2.call(this, 'param1', 'param2')
  * apply : func2.apply(this, ['param1', 'param2'])
    * bind는 선언시, clall과 apply는 함수 호출시 this와 파라미터를 지정
    * apply는 첫번째 인자로 this, 두번째 인자로 넘겨주는 파라미터를 배열로 전달
* 모듈
  * 코드의 묶음 단위. 애플리케이션 하나의 구성요소
  * import : 모듈 가져오기
  * export :  모듈 내보내기
  * 런타임 로딩 : 의존관계가 형성된 모듈들을 애플 구동 시점에 HTTP 요청으로 불러오고 실행함
  * 번들링 : 의존 관계가 형성된 모듈들을 하나의 파일로 묶어줌
  * default : 모듈 기본값. 한 파일에서 하나의 값만 정의가능
  * export default class Hello {}
* as
  * import * as add from ‘./add.js’
  * 다른 모듈에서 가져온 값들은 얕은 복사. 

* 표준 내장 객체
  * 전역 스코프 안에 객체 참조
* 내장 함수 객체
  * 표준 내장 객체중 함수처럼 호출 가능한 것
  * new 지시자 통해 함수 형태로 호출
* typeof
  * 특정 원시 자료형 확인, 원시와 객체형 구분
* instanceof
  * 객체 확인
* isNaN
* isArray
* isInteger
* pareseInt
  * 문자열 to 숫자형 정수
* parseFloat
* trim
  * 문자열 양 끝 공백 없애기
* slice(시작 인덱스, 종료 인덱스)
  * 문자열 자르기
  * 음수 가능. 뒤에서부터
* substring(시작 인덱스, 종료 인덱스)
  * 문자열 자르기
  * 음수 불가
* substr(시작인덱스, 길이)
  * 문자열 자르기
* concat(str11…)
  * 문자열 합치기
* charAt(n)
  * 특정 위치 문자 반환
* indexOf(str)
  * 특정 문자열 위치 확인
  * 없으면 -1
* lastIndexOf(str)
  * 특정 문자열 위치 확인
  * 뒤에서부터
* includes(str)
  * 특정 문자열 포함 여부 확인
* toLowerCase, toUpperCase
  * 대소문자 변환
* from(배열로 변환될 값, 변환된 배열 내부 요소에 대한 callback 함수)
* 배열 요소를 분할/변환하기
  * split(str구분자)
    * 문자열을 특정 구분자에 의해 배열로 나누기
* push : 배열 뒤 요소 추가
* unshift : 배열 앞 요소 추가
* join(str 구분자) : 배열에 특정 구분자 넣어 문자열로 병합
* pop : 배열 마지막 요소 추출
* shift : 배열 맨 앞 요소 추출
* slice : 배열 특정 위치 요소 추출
* splice(시작 인덱스, 삭제할 요소 갯수, 추가될 요소들…) : 배열 인덱스로 특정 요소 수정
* forEach(callback함수) (배열 순환)
  * arr.foreach((el) => {console.log(el.n ame);});
* sort(function a, b) {return 비교값}
  * 비교값 > 0 a가 b보다 앞에 위치 (작은인덱스) =0이면 위치변경안함

* reverse() : 배열 순서 반대로 나열
* some(function return bool) : 배열 요소가 특정 요소 맞는지확인. 하나라도 있으면 true
* every : 모든 배열 요소가 특정 조건 만족하는지 확인
* filter(function return bool) : 배열의 특정 조건을 기준으로 필터링
* find : 배열의; 특정 조건을 충족하는 요소 찾기
* map : 배열 요소 일괄 변경. callback함수에 리턴값에 따라 반환되는 배열 값이 바뀜
* reduce(누적된 값, 현재 요소 값, 현재 인덱스, 원본 배열)
  * 배열요소를 순환하면서 누적
  * 배열 내 값을 누적시키기
    * numArr.reduce((acc.el) => {return acc+el}, 0);
  * 중첩된 배열을 단일하게 만들기
    * arr.reduce((acc,el) => {return add.concat(el);}, []);
* keys : 객체에서 키만 추출
* values : 객체에서 값만 추출
* entries : 객체를 배열로 [키:값] -> [키,값]
* freeze : 객체 변경되지 않도록
* seal : 객체에 속성 추가 못하게 (기존 속성은 변경가능)
* assign(반환될 객체, ...병합될 다른 객체들) : 객체 병합 확장
* 진수 변환
  * toString(2)
  * pareInt(bin, 2)
* random() : 0,1사이 랜덤
  * Math.random() * (max - min + 1) + min);
* round() 반올림
  * round(val * 10) / 10 소수점 둘째자리 반올림
  * round(val / 10) * 10 일의 자리 반올림
* Date객체
  * getFullYear
  * getMonth
  * getDate
  * Date.UTC()
* Math.floor((diff = diff / 1000) % 60); // 초 구하기, diff는 date2.getTime() - date1.getTime()
* JSON.parse(값, 리플레이서)
* 정규표현식(regexp, regex) : / / 표현식. 일치하는 문자열 찾거나 반환. 일괄 치환
  * search(str정규표현식) : 위치확인 (없으면 -1)
  * match(str정규표현식) : 해당 값 반환
  * test(str정규표현식) : 정규표현식에 맞으면 true
  * str정규표현식.exec(str) : 정규표현식과 일치하는 문자열 반환
* 배열로 반환 [1, index: , input: ]
  * str.replace(교체 대상 문자열 또는 정규식, 대체될 문자열 또는 함수)
* 반복 가능한 객체
* 반복 가능한 규약
* 반복자 규약 (iterator : 반복자 규약을 충족하는 객체)
* for-of
  * 문자열 순환
* next 호출 결과로 반환된 객체의 done속성이 true일때까지
* Map
  * 키와 값을 한 쌍. 중복키X, Key는 다양한 자료형 값 가능
  * Object는 문자, Symbol자료형만 Key 가능
  * Symbol.iterator가 기본적으로 정의
  * Object는 없음
  * get, set, has, delete, size
  * keys, values, entries
* for-of, foreach : Map 객체 순환
* for(let key of map.keys())
* for(let value of map.values())
* for(let [key, value] of map)
* map.forEach((value, key) => {});
* Set
  * 값으로만 이루어짐, 중복값허용X
  * add, delete, has, size
  * new Set(array);
  * keys, values, entries
* setTimeOut(function, 지연시간)
* setInterval(function, 1000) 1초마다 실행
  * 반환된 id값을통해 clearInterval(id)로 취소 가능
* Promise
  * 비동기 처리
  * 객체로서 언젠가 완료될 일(계산)
  * 대기중(Pending) : 아직 결과가 없음. 약속만 함
  * 이행됨(Fulfilled) : 비동기 처리가 성공적으로 완료하여 약속 이행. 결과로 하나의 값 전달
  * 거부됨(Rejected) : 비동기 처리 실패. 거절된 이유 전달
  * settled : 일단 결론이 난 상태 (약속이 지켜졌든 아니든)
  * then(onFulfilled, onReject) : 약속 완료시 호출될 함수 전달
  * catch(onReject) : 약속 거부 시 호출될 함수 등록
  * Promise 끼리의조합
  * Promise.catch(function) 비동기 작업이 중간에 에러 날 때
  * Promise.all : 여러 비동기 작업이 모두 완료되었을 때 작업 진행
  * var promise = function(param) {return new Promise(function)과  var promise = new Promise(function)의 차이
    * 후자는 즉시 실행
    * 후자는 여러번 호출되어도 한번 이미 실행되었으므로 동일하게 Reject혹은 fulfill이 수행됨

* Async
  * 함수 안의 await구문과 함께 비동기 작업 제어
  * 
* 문서 객체 모델 (DOM)
  * HTML과 XML을 위한 프로그래밍 인터페이스
  * 문서의 구조, 스타일, 내용 변경 가능
* <script> 태그가 필요한 이유 : 앞의 태그들을 브라우저가 먼저 읽어야 JS코드가 해석되기전에 DOM이 만들어져 <script>태그 내 JS에서 해당 DOM에 접근 가능하므로
* 노드 트리 구조로 표현 가능
* Tag의 Attribute, DOM의 Property
* .appendChild() 생성 .remove() 삭제
* .style.
* 이벤트
  * 모든 요소는 이벤트를 발생함
  * addEventListner(‘keydown’,e => {});
  * 이벤트 버블링
  * 이벤트 캡처링
* 스크롤 고정하기
  * window객체의 속성을 이용해 상단 차이가 커질경우 상단에 고정
  * 스크롤할때마다 호출되는 리스너 함수 등록
* 문서 이동
  * location.assign(‘’);


* Array 시간복잡도
    * arr[i] O(1)
    * arr.push(5)  O(1)
    * arr.slice() O(n)
    * arr.pop()  O(1)
    * arr.includes(5)  O(n)
* Q
* Part
* A
* for, for-in, for-of, foreach 차이점
* JS

* for in : 객체의 property 확인용
* for of : 배열 값 순환

* for와 for in 은 반복변수의 index를 리턴
* forEach와 for of는 해당 값을 리턴

```
const array = ['가','나','다','라'];
console.log("size : "+array.length);
const size = array.length;
//객체의 반복 in, 배열 of
console.log("basic");
for(let i=0; i<size; i++){
  console.log(array[i]);
}
 
console.log('forEach');
array.forEach(function(j){
  console.log(j);
});
 
console.log('for of');
for (let k of array){
  console.log(k);
}
 
console.log('for in');
for (let z in array){
  console.log(array[z]);
}
```
