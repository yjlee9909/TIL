## SaSS (Syntactically Awesome Stylesheets), SCSS
	SaSS를 통해 편의 기능들을 사용하여 시간을 절약
    코드 재사용 가능
    
## SaSS
	CSS로 컴파일 되는 스타일 시트 확장 언어
    SaSS 기반으로 개발하여 CSS로 export
    (브라우저는 SaSS 파일 직접 읽지 못함)
    
### SaSS 기술 방식 - .sass, .scss
	일반적으로 css와 유사한 SCSS 사용 (중괄호 사용)
    
    여러 _.scss 파일로 분리하여 메인 파일인 style.scss에 분리된 파일들을 @import 를 통해 
    분리된 파일들을 분할하여 관리하기가 편함
    
    이때) 메인 scss 파일에는 @import 와 주석 외에 다른 코드는 작성 x
    
    '_'를 맨 앞에 붙여서 저장하면 main 파일의 일부분임을 알려주므로 각각의 .css 파일로 저장이 안됨
    
    주석 내용은 sass 내에서만 확인이 가능
    여러 줄 주석은 css 파일에서도 나타남
    
### 중첩 (Nesting)
	HTML 중첩 구조 방식처럼 CSS도 중첩하여 작성하면 가독성이 높아짐
    
~~~scss
//Scss
//Scss에서도 HTML처럼 계층구조로 스타일을 적용할 수 있다.
nav {
	background : #C39BD3;
	ul {
		display: flex;
		justify-content: flex-end;
		li {
			margin-right: 10px;
		} 
	}
}
~~~

~~~css
nav {
  background: #C39BD3;
}
nav ul {
  display: flex;
  justify-content: flex-end;
}
nav ul li {
  margin-right: 10px;
}/*# sourceMappingURL=ex1.css.map */
~~~


### 속성 Nesting
	중첩은 선택자 말고도 background 이름을 가진 속성들 또한 중첩시켜서 표현이 가능하다. : 를 사용
    
~~~scss
.add-icon {
  background : {
    image: url("./assets/arrow-right-solid.svg");
    repeat: no-repeat;
  }
}
~~~

### ampersane 앰퍼샌드
	"&" 는 상위에 있는 부모 선택자를 가리킴
    가상요소, 가상클래스, class 나 id 셀렉터 참조 가능
    
~~~scss
//Scss
.box {
    &:focus{} // 가상선택자 -> .box:focus{}
    &:nth-child(2){}
    &::after{} // 가상요소 -> .box::after{}
    &::before{} 
}
~~~

### @at-root
	중첩에서 벗어나고 싶은 선택자 앞에 작성
    
## 변수
	값이 두 번 이상 반복되는 경우 변수로 만든다.
    보통 폰트 색상, 크기, 글자 간격 등
    
### 변수 생성하기
	$ 기호를 사용하여 스타일 저장함
    
~~~scss
$bgcolor : #FFF; // 사용할 때 : background-color : $bgcolor;
~~~

### 변수 타입
	numbers, strings, color, booleans, lists, maps, null
    
    list에 들어있는 값은 index가 0부터가 아닌 1부터 시작
    
~~~scss
$font-size: 10px 12px 16px;

.text3 {
	font-size: nth($font-size, 2);
}
~~~

## 변수의 Scope

### 지역변수
	선언한 자기를 감싸는 중괄호 안에서만 사용, 하위에서도 사용 가능

### 전역변수
	가장 윗 부분에서 선언하며 파일 내에 어디서든지 사용 가능
    
    !global를 사용하여 전역 변수로 만들어 사용 가능
    
## Operator 
### 비교연산자 (숫자형)
	@debug를 통해 비교한다
    단위가 일치하지 않으면 에러가 발생
    
~~~scss
@debug 100 > 50; // true
~~~

## Mixin
	코드를 재사용하기 위해 만들어진 기능


### Mixin 사용하기
    @mixin 이름{매개변수} // 생성
    @include 이름(인수) // 사용
    
    
~~~scss
@mxin cen-xy {
	display:flex;
    justify-content : center;
}
.abc {
	@include cen-xy;
}
~~~

### 인수 (Arguments)
	매개변수와 인수 개수가 같아야 한다.
    매개변수를 통해 능동적인 스타일 적용이 가능하다.
    
~~~scss
@mixin image-style($url, $size, $repeat, $positionX : 50%, $positionY : 50%) {
  background-image: url($url);
  background-size: $size;
  background-repeat: $repeat;
  background-position: $positionX $positionY;
} 
.profile {
  @include image-style("./assets/user.jpg", cover, no-repeat);
}
~~~

## Extend 
	이미 작성된 스타일 클래스를 extend 하거나 %를 사용해 따로 정의한 후 extend 하여 원하는 선택자에게 스타일을 적용
    mixin - 관계 없는 선택자에서 조금 다른 스타일 적용
    extend - 관계 있는 선택자에서 동일한 소스코드 적용시 사용


### 사용법 - class 이름 가져오기
	@extend .0000;
    
    !!) 다중 선택자 클래스 사용 못함
    
### 사용법 - % 선택자 만들기
	%base-btn {}
    
    -> @extend %base-btn;
    
## 조건문과 반복문, 함수

### @if, @else, @else if
	@if (조건) {}

~~~scss
// circle이 false면 사각형을, true이면 원형으로 스타일함
@mixin avatar($size, $circle: false) {
  width: $size;
  height: $size;

  @if $circle {
    border-radius: $size / 2;
  }
}

.square-av {
  @include avatar(100px, $circle: false);
}
~~~
### @for 

~~~scss
for ($변수) from (시작,이상) through(끝,이하){
	// 반복할 내용
}

// for문을 이용해 nth-선택자에게 각각의 image를 배경에 넣어준다.
@for $lee from 1 through 7 {
    .photo-box:nth-child(#{$lee}) {
        background-image: url("../assets/phoster#{$lee}.png");
    }
}
// 범위 1이상 5이하
// for문에서 1부터 5까지 반복하라는 의미입니다. 총 5번 반복되면서 코드가 실행된다.
// 만약 from 3 throught 8 이라면 3에서 8까지 6번 실행된다.
~~~

### @each
	lists 나 맵의 각각 요소마다 코드 실행해서 적용
    
~~~scss
@each ($변수) in (리스트나 맵){ 
	// 반복할 내용
}
~~~

### @while

~~~scss
@while 조건 {
	// 반복할 내용
}
~~~

### @function
	함수이름() 형태로 호출하고 실행하여 @return 키워드를 통해 값 자체를 반환
    
~~~scss
@function 함수이름($매개변수) {
	// 실행 코드
	@return 값
}
~~~

### 추가 계획
> SaSS 영상 강의 추가로 본 후 내용 보충 예정