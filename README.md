# 1. VS Code 설정 Tip
## 1.1 scss 할 때 상황에 맞게 컴파일러를 하기 위한 Tip
   1. 왼쪽 톱니바퀴 아이콘 이미지 클릭 또는 파일 > 기본설정 > 설정 (ctrl + ,)
   2. 설정 > 명령팔레트 또는 보기 > 명령팔레트 ( ctrl + shift + p), ctrl+p 눌러도 됨
      - ctrl + p 로 할 경우, 명령팔레트 창에서 > 써주면 된다.
   3. 설정 > 명령팔레트 > settings.json 검색 
      - 기본 설정 열기 = vs code 기본 설정값 (수정X)
      - 설정 열기 = 원하는 설정값으로 변경 가능.  =  설정 > 사용자설정
      - 작업 영역 설정 열기 = 해당 프로젝트에만 해당되게 설정값 적용
         - 설정 > 사용자 에서 작업영역 옆 폴더명 선택 후 수정하면 해당 폴더에 .vscode 생성
         - .vscode 폴더 > settings.json 파일 자동 생성
         - 수정한 속성 값을 확인 할 수 있다.
   4. 프로젝트별 settings.json 설정 (확장 프로그램 Live Sass Compile 예시)
      - 설정 > 사용자, (왼쪽) 확장에서 "Live Sass Compile" 선택
      - Live Sass Compile > settings: Formats 위치, settings.json에서 편집 선택
      - 해당 부분에서 저장경로, map 파일 저장 유무 등 편집 가능.
      - 프로젝트별 저장경로 등 json 편집을 달리하고 싶을 땐, 해당 프로젝트에 .vscode 폴더 생성 후 settings.json 파일 생성.
         ```
         {
            속성: 속성값 적용
         }
         ```
   


# 2. VS Code에서 Satch Sass 실행이  안될 때
- 폴더 영역 추가가 아닌 ★ "폴더 열기"로 해당 폴더를 열어★ 야 한다.



# 3. VS Code 확장 프로그램 설치
## 3.1. Live Sass Compiler
   - 설정 > 사용자, (왼쪽) 확장에서 "Live Sass Compile" 선택
   - Live Sass Compile > settings: Formats 위치, settings.json에서 편집 선택
   - 해당 부분에서 저장경로, map 파일 저장 유무 등 편집 가능.
   - Live Sass Compile 경우, 확장프로그램에서 "Live Sass Compile" 검색 후 상세 페이지를 보면 "Settings Docs." 이 부분 클릭. (클릭하면 새 창 열리고, 어떻게 커스텀 하는 지 확인 가능)
   ```
   {
      "liveSassCompile.settings.generateMap": false,
      "liveSassCompile.settings.formats": [
      
         {
               "format": "expanded",
               "extensionName": ".css",
               "savePath": null
         }
      ]
   }
   ```
   - 위 코드 복사 > 복붙하기 
      - "liveSassCompile.settings.generateMap": false = .css.map 파일 생성유무 (false = 저장하지 않는다.)
      - savePath: 저장경로를 입력해준다. (기본값 null = scss 폴더에 그대로 저장하겠다는 뜻.)
         > savePath: "속성값"  
         >  > - "/" = scss 파일이 속한 root 폴더를 의미. root 폴더에 .css 파일 생성 후 저장.
         >  > - "/css" = root 폴더 > css 폴더에 .css 파일 생성 후 저장.
         >  > - "~" = .scss 파일 기준으로 잡을 때 ~ 로 표시
         >  > - "~/css" = scss/css 폴더에 .css 파일 생성 후 저장.
         >  > - "~/../css" = scss 폴더와 같은 라인의 css 폴더에 .css 파일 생성 후 저장.
      ```
      project-a
         css
            1-1. test.css
         scss
            2-1. test.scss
      ```
   - Live Sass Compiler 설치하면 Live Server 도 같이 설치된다. Live Server = 테스팅 서버


## 3.2. 프로젝트별 setting 설정하기 (Tip 4번참고)
   - 해당 프로젝트에 생성된 .vscode > settings.json 파일에 아래 코드를 적용. 
      - css 폴더 생성 경로 경우, savaPath 에 저장경로를 적용해준다. 
      ```
      {
         "liveSassCompile.settings.formats":[
            {
                  "format": "expanded",
                  "extensionName": ".css",
                  "savePath": "~/../css"
            }
         ]
      }
      ```


## 3.3 Live Server
   - html 페이지에서 오른쪽 마우스 클릭 > Open With Live Server 클릭 (브라우저로 연결 > 페이지 오픈)
   - 또는 아래(상태 표시줄) Go Live 버튼을 클릭해준다. 
   - html 페이지 수정 작업 시, Liver Server로 열린 브라우저에서 자동 확인이 된다.
      > Live Server 열었을 때, Port 에러가 날 경우, 아래 코드를 사용자 설정 .json 파일에서 입력 후 다시 Open With Liver Server로 열어준다.
      >  > - 사용자 설정 json 파일에서 아래 코드를 입력해준다
   ```
   "LiveServer.settings.port": 0
   ```
   - Go Live를 닫고 싶을 땐, 아래 (상태표시줄에서) Port:  부분을 클릭해주면 된다.



## 3.4. Sass 
## 3.5. Sass Lint



# 4. SASS(SCSS) Preprocessor
css 작성(생성)을 위한 작고 가벼운 언어이고, Sass와 Scss가 있다.
   - Sass : SCSS와 작성하는데 있어서 구조적 차이가 있고 작성이 번거롭고 복잡할 수 있다.
   - SCSS : 기존에 알던 CSS와 유사하게 작성할 수 있기 때문에 친근하게 느껴져 배우기가 쉽다. ★


## 4.1. Sass 컴파일러 방식
   - VS Code + Live Sass Compiler ★
   - Ruby Gem을 이용한 컴파일러 
   - Node.js NPM을 이용한 컴파일러
   - Ruby, Node.js 을 이용한 컴파일러는 Scss에 대해 알고 난 후 배워도 무방하다. (=복잡하다)

## 4.2. Watch Sass
   - .scss 파일을 열면 아래(상태표시줄) Wahch Sass 버튼이 보여진다
   - Wahch Sass 을 클릭하면 컴파일러되면서 .css 파일이 자동 생성이 된다.
   - Wahch Sass 누르고 난 후 해당 부분이 Watching.. 으로 바뀌는데 이 경우 .scss 파일을 작업하면서 저장을 누르면 css 파일에 자동으로 파일이 컴파일러 된다.
   - .css 파일에 자동 적용되지 않게 하려면 watching.. 버튼을 클릭해주면 된다.


## 4.3. 컴파일러된 css 파일 연결
   - .scss 파일이 아닌 컴파일러된  .css 파일을 html 문서에 link


# 5. Sass Basic Project
- sass(scss)는 css를 작성하는 css를 만드는 언어로 css 모든 것을 다 포함. css 그대로 작성해도 무방하다. 

## 5.1. Variables (변수)
   - 변수를 선언하고 중복되는 값에 적용을 해준다.
   - 변수 선언은 '무조건' $ 로 시작한다.
   - 변수명은 영문으로 시작해야하고 숫자, -(대쉬), _(언더스코어) 만 포함할 수 있다.
   - 선언한 변수는 css 문법에서 속성명 : 변수 로 쓴다.
   ```
   $bg-color: #00f; ($변수명: 속성값;)

   #box1 {
      color: #ff0;
      background-color: $bg-color;  /* 속성명: 변수 */
      width: 100px;
   }
   ```

## 5.2 Nesting (네스팅)
   - Nesting (네스팅) - tree 구조 (포함관계)
   ```
   #box1 {
      font-size: 40px;
      background-color: #ffcccc;

      border-radius: 20px;
      border: 3px solid #f00;
      box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
   }

   #box1 > a {
      color: #a22;
      text-decoration: none;
   }
   ```
   - 위 구조를 아래와 같이 바꿀 수 있다. 이 기능을 Nesting (네스팅).

   ```
   #box1 {
      font-size: 40px;
      background-color: #ffcccc;

      border-radius: 20px;
      border: 3px solid #f00;
      box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);

      a {
         color: #a22;
         text-decoration: none;  
      }
   }
   ```

   #### 5.2.1 Nesting (네스팅) - &(앰퍼샌드) 를 이용해 바로 하위요소에 적용하기
   - & = 자기자신을 지칭, 즉 여기선 #box1
   - #box1 의 바로 하위요소 a 를 선택하고자 할 때
   - & > a
   ```
   #box1 {
      font-size: 40px;
      background-color: #ffcccc;

      border-radius: 20px;
      border: 3px solid #f00;
      box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);

      & > a {
         color: #a22;
         text-decoration: none;  
         &:hover {
         color: #000;
         text-decoration: underline;
         }
      }
   }
   ```
   - & > a 부분은 css 파일에서 아래와 같이 확인이 된다.
   ```
   #box1 {
   font-size: 40px;
   background-color: #ffcccc;
   border-radius: 20px;
   border: 3px solid #f00;
   box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
   }

   #box1 > a {
   color: #a22;
   text-decoration: none;
   }

   #box1 > a:hover {
   color: #000;
   text-decoration: underline;
   }
   ```
  

   #### 5.2.2 Nesting (네스팅) - & 을 이용해 css 적용하기
   - & 은 자기 자신을 지칭, 자기 자신을 나타내는 이름 그대로도 나타낸다.
   - & = #box1. 즉, #box1-title = &-title 로도 쓸 수 있다.
   ```
   //#box1-title
   &-title {
      font-style: italic;
      text-decoration: underline;
   }
   ```
  

   #### 5.2.3 Nesting (네스팅) - 중복되는 코드가 있을 때
   ```
   &, &-title {
      border-radius: 20px;
      border: 3px solid #f00;
   }
   ```
   ```
   #box1, #box1-title {
      border-radius: 20px;
      border: 3px solid #f00;
   }
   ```
  

   #### 5.2.4 Nesting (네스팅) - 네스팅 기능을 이용한 구조
   ```
   <div class="box1">
      <div class="box2">
         <div class="box3">
         </div>
      <div>
   <div>
   ```
   1번, 기존 css처럼
   ```   
   .box1 .box2 .box3 {}
   ```
   2번, 네스팅 문법대로 (엄격하게 네스팅으로만 작성하지 않아도 된다.)
   ```
   .box {
      .box2 {
         .box3 {

         }
      }
   }
   ```
   3번, 네스팅 & 기본 css 처럼
   ```
   .box1 {
      .box2 .box3 {

      }
   }
   ```
   - 알아보기 쉽게 작성을 하면 된다.
   - 엄격한 sass 네스팅 문법으론 2번처럼 하면 된다.  
  
## 5.3. Nesting - Media Queries (네스팅 - 미디어쿼리)
```
@media screen and (max-width: 500px) {
#box1 {
   font-size: 20px;
}
}
```
- 위 코드를 아래와 같이 표기한다.
```
#box1 {
   font-size: 40px;
   @media screen and (max-width: 500px) {
      font-size: 20px;
   }
}
```

## 5.4. mixin (믹스인)
- css 속성들을 하나의 그룹으로 묶어서 여려 군데에다가 재사용할 수 있는 mixin 기능  
- mixin 기본 구조
```
@mixin name명(변수인자1, 변수인자2 ...) {

}
```
- name명 = 영문으로 시작하되 숫자, -, _ 만 포함 가능하다.
- 변수인자는 $변수명 으로 써주고 구분지을 땐 ,(쉼표)로 한다.
- 변수인자는 해당 mixin {} 블럭 안에서만 사용할 수 있다.

   #### 5.4.1 mixin (믹스인) - 속성은 같은데 속성값이 다를 때
   - font-size 와 background-color 속성을 여러 군데에서 사용해야할 때 mixin을 이용한다.
   - 변수인자에 $fontSize, $bgColor 를 넣어준다. 변수인자는 해당 mixin {} 에서만 사용이 가능하다.
   - 위처럼 mixin 을 만든다.
   - 만들어놓은 mixin을 사용할 때엔 include를 이용해 불러온다.
   ```
   @mixin fontSizeBgColor($fontSize, $bgColor) {
      font-size: $fontSize;
      background-color: $bgColor;
   }
   ```
   
   - 변수인자 첫번째에 font-size, 두번째 background-color 값을 적어주었기 때문에 첫번째엔 font-size 값을 쓰고 두번째엔 background-color 값을 쓴다.
   ```
   #box1 {
      @include fontSizeBgColor(40px, #ffcccc);
   }
   ```
   - 아래 box1 { } 과 같이 .css 파일에서 보여진다.
   ```
   #box1 {
      font-size: 40px;
      background-color: #ffcccc;
   }
   ```
   
   #### 5.4.2 mixin (믹스인) - 변수 인자에 디폴트값(기본값)을 적용할 수 있다.
   - 변수 인자에 :00 으로 기본값을 넣을 수 있다.
   - font-size: 20px, background-color: #fff
   ```
   @mixin linkStyle($textColor, $textDeco: none) {
      color: $textColor;
      text-decoration: $textDeco; 
   }
   ```

   - 인클루드 할 때 값을 입력하지 않으면 기본값이 적용이 된다.
   - 즉, color : #a22 , text-decoration: none 으로 적용이 된다.
   ```
   @include linkStyle(#a22);
   ```

   #### 5.4.3 mixin (믹스인) - 맨 앞자리는 기본값, 2번째 border-color 값만 변경하고 싶을 때
   ```
   @mixin fontSizeBgColor($fontSize:20px, $bgColor:#fff) {
      font-size: $fontSize;
      background-color: $bgColor;
   }
   ```
   - 두 번째 매개 변수를 덮어 쓴다
   - $변수명: 속성값
   - font-size: 20px, background-color: #e9e9e9 로 적용.
   ```
   @include fontSizeBgColor($bgColor: #e9e9e9);
   ```

## 5.5. extend (익스텐드)
- mixin 속성은 같은데 속성값이 다를 때 / extend 같은 속성, 속성값이 동일할 때
- 속성값이 동일할 때 extend 로 등록하여 중복 사용 가능.
- extend 만들 때는 %을 이용해 만든다.
- %사용하고자하는이름 {}
```
%boxShape {
  border-radius: 20px;
  border: 3px solid #f00;
  box-shadow: 0px 3px 11px 0px rgba(0, 0, 0, 0.75);
}
```

- 만든 extend 를 쓸 땐 @(골뱅이)를 이용한다
- @extend %사용하고자 하는 이름;
```
@extend %boxShape;
```

## 5.6. Partial (파셜)
- 여러 코드들을 묶어서 별도의 다른 파일로 나눠서 저장하고 그 파일을 가져다가 쓸 수 있는 Partial(파셜) 기능.
- mixin, extend 등 특정 .scss 파일에서만 쓰는 것이 아니라 ".scss 파일에서 공용으로 쓸 수 있게 하고싶을 때"
   #### 5.6.1 _mixins.scss 파일을 만들고 mixin 코드를 저장한다.
   - partial 은 반드시 _ 로 파일명을 만든다. _mixins.scss
   - .scss 파일을 _ 로 시작을 하면 컴파일이 되질 않는다. (_mixins.scss 로 할 경우, _mixins.css  로 컴파일 되지 않음!!)
   ```
   _mixins.scss
   partial
      _styles.scss
   ```
   - _mixins.scss 파일을 불러와야 하는 파일에서 최상단에 @import "파일명이름"; 써 준다
   - 파일명이름을 쓸 땐, _(언더스코어) 와 .scss(확장자) 는 빼고 파일명이름만 쓴다.
   - 현재 VS Code 에서 partial - import 적용할 때 "확장 다시시작" 관련 메세지창이 보여지는데 해당 부분은 버그로 
   다시시작 버튼을 클릭해주면 몇 초후에 Watch Sass 버튼 보여진다. Watch Sass 클릭하면 다시 자동 컴파일 된다.
   ```
   @import "mixins";
   @import "partial/styles";
   ```

## 5.7. Partial Import Error Solution
- Partial 작업 시 오류 났던 부분은 VS Code 확장프로그램 "Color Highlight" 오류로 colorize 확장프로그램으로 변경

## 5.8. if문
- 속성값을 주는 mixin 만든다   
```
@mixin textAndBgColor($textColor, $bgColor) {
   color: $textColor;
   background: $bgColor;
}
```
- if문을 줄 mixin을 만든다
```
@mixin theme($mood) {
   @if $mood == 'light' {
      @include textAndBgColor(#333, #ff0);
   }
   @else if $mood == 'dark' {
      @include textAndBgColor(#fff, #000);
   }
   @else {
      @include textAndBgColor(#f00, #aaa);
   }
}
```
- 영역별로 @include를 이용해 theme를 적용해준다
```
#box1 {
   @include theme('light');
}
#box2 {
   @include theme('dark');
}
#box3 {
   @include theme('');
}
```
- .css 파일에서 아래와 같이 보여진다.
```
#box1 {
  color: #333;
  background: #ff0;
}

#box2 {
  color: #fff;
  background: #000;
}

#box3 {
  color: #f00;
  background: #aaa;
}
```

## 5.9 Wrap up - Boxes Project (복습)
### 5.9.1 Wrap up - Boxes Project - 1
   #### 5.9.1 - 1. 작업영역(프로젝트별) 설정하기 (.vscode > settings.json)
   - This is Default. : 기본 저장 방법
   - You can add more : 기본 저장 방법 외 추가적으로 저장할 때 ( ex. min.css 파일을 같이 만들때)
   - savePath : 기본값은 null (scss 파일 기준 폴더에 저장)
   - savePath : scss 파일 기준으로 작업할 땐 ~, root 폴더를 기준으로 할 땐 /
   ```
   {
      "liveSassCompile.settings.formats":[
         // This is Default.
         {
            "format": "expanded",
            "extensionName": ".css",
            "savePath": null
         },
         // You can add more
         {
            "format": "compressed",
            "extensionName": ".min.css",
            "savePath": "/dist/css"
         }
      ]
   }
   ```

   #### 5.9.1 - 2 &(앰퍼샌드) 사용 시 주의사항
   - & 를 쓰면 상속 구조가 되지 않는다.
   - .scss 파일에서 보면 .box > .box-inner > .box-inner-title
   ```
   .box {

      width: 300px;
      height: 300px;
      padding: 20px;

      &, &-inner {
         border: 3px solid $color-black;
      }

      // .box-inner
      &-inner {
         
         padding: 10px;
         height: 40px;
         background-color: #ccc;

         // .box-inner-title
         &-title {
               font-size: 20px;
               color: $color-white;
               background-color: rgba(0,0,0,.5);
         }
      }
   }
   ```
   - 컴파일된 .css 파일에서 확인을 해보면 상속 구조가 아닌 별도로 적용 된다.
   ```
   .box {
      width: 300px;
      height: 300px;
      padding: 20px;
   }

   .box, .box-inner {
      border: 3px solid #000;
   }

   .box-inner {
      padding: 10px;
      height: 40px;
      background-color: #ccc;
   }

   .box-inner-title {
      font-size: 20px;
      color: #fff;
      background-color: rgba(0, 0, 0, 0.5);
   }
   ```
   - & 를 이용해 상속구조로 하고 싶을 땐 아래 코드 참고
   ```
   .box {

      width: 300px;
      height: 300px;
      padding: 20px;

      &, & &-inner {
         border: 3px solid $color-black;
      }

      // .box-inner
      & &-inner {
         
         padding: 10px;
         height: 40px;
         background-color: $color-grey;

         // .box-inner-title
         &-title {
               font-size: 20px;
               color: $color-white;
               // background-color: rgba(0,0,0,.5);
               background-color: rgba($color-black,.5);
         }
      }
   }
   ```
   - .box .box-inner .box-inner-title 처럼은 사용할 수 없어서 & 은 상황에 따라 적절하게!
   ```
   .box {
      width: 300px;
      height: 300px;
      padding: 20px;
   }

   .box, .box .box-inner {
      border: 3px solid #000;
   }

   .box .box-inner {
      padding: 10px;
      height: 40px;
      background-color: #ccc;
   }

   .box .box-inner-title {
      font-size: 20px;
      color: #fff;
      background-color: rgba(0, 0, 0, 0.5);
   }
   ```

   #### 5.9.1 - 2 &(앰퍼샌드) 사용 팁
   - 패스트캠퍼스 sass 강의 참고
   - & (앰퍼샌드) = 중첩 안에서 & 키워드는  상위(부모) 선택자를 참조하여 치환
   - 사용 팁 1
   ```
   .btn {
      position: absolute;
      &.active {
         color: red;
      }
   }
   ```
   - Compiled to:
   ```
   .btn {
      position: absolute;
   }
   .btn.active {
      color: red;
   }
   ```
   - 사용 팁 2
   ```
   .fs {
      &-small { font-size: 12px; }
      &-medium { font-size: 14px; }
      &-large { font-size: 16px; }
   }
   ```
   - Compiled to:
   ```
   .fs-small {
      font-size: 12px;
   }
   .fs-medium {
      font-size: 14px;
   }
   .fs-large {
      font-size: 16px;
   }
   ```



   #### 5.9.1 - 3 변수를 이용해 RGBA 값 적용하기
   - 변수 $color-black : #000; 를 이용해 background-color: rgba(0,0,0,.5) 적용하는법
   ```
   // 변수 
   $color-black: #000;

   // Nesting
   .box {

      .box-inner {

         .box-inner-title {
            background-color: rgba($color-black,.5);
         }
      }
   }
   ```

### 5.9.2 Wrap up - Boxes Project - 2
   #### 5.9.2 - 1 Partial (파셜)
   - partial(파셜) 작업을 위해 abstracts 폴더를 생성
   - _(언더스코어)로 .scss 파일을 만든다. (_로 시작하는 파일은 컴파일 되지 않음★)
   - 불러올 땐, 불러와야 하는 파일에 @import "폴더/파일명"; 
   - 파일명을 적을 땐, 앞에 _(언더스코어)를 빼고, 뒤에 .scss 확장자도 뺀다!
   - 01_sass_basics_pj/sass/boxes.scss 파일 참고
   ```
   @import "abstracts/variables";
   @import "abstracts/mixins";
   ```

   - 기본적인 레이아웃 구조 등 설정에 대한 css는 base > _base.scss 로
   - base 폴더를 따로 만들어서 기본 구조 (body 등) 관리

   #### 5.9.3 - 2 Media Queries (미디어쿼리) ★★★
   - _mixin.scss 파일에서 미디어쿼리 문법을 적용한 mixin을 만든다
   ```
   @mixin mq() {
      <!-- 미디어쿼리 기준 적용 -->
      @media screen and (min-width: 1201px) {
      }
   }
   ```
   - @media { } 괄호 안에 @content; 를 써준다
   - @content; 를 써주면 원하는 코드를 작성할 수 있다
   ```
   @mixin mq() {
      @media screen and (min-width: 1201px) {
         @content;
      }
   }
   ```
   - mixin - mq() 를 include 로 불러온다
   - { } (괄호) 안에 코드를 작성해주면 된다
   ```
   @include mq() {
      border: 10px solid $border-color;
   }
   ```

   #### 5.9.3 - 3 mixin & Media Queries & if문 ★★★
   - mixin 에서 if문을 이용하여 브라우저 뷰너비에 따라 미디어 쿼리 적용
   ```
   @mixin mq($screen-width) {
      @if $screen-width == 'phone' {
         // phone
         @media screen and (max-width: 600px) {
               @content;
         }
      }
      @else if $screen-width == 'tablet-land' {
         // tablet-land
         @media screen and (min-width: 601px) and (max-width: 899px) {
               @content;
         }
      }
      @else if $screen-width == 'desktop-big' {
         // desktop-big
         @media screen and (min-width: 1201px) {
               @content;
         }
      }
      @else {
         // desktop
      }
   }
   ```
   - include에서 인자 자리에 이름을 넣으면 if문 조건(뷰너비 기준)에 따라 css 값 적용
   ```
   @include mq('phone') {
      border: none;
   }
   @include mq('tablet-land') {
      border: 2px solid $border-color;
   }
   @include mq('desktop-big') {
      border: 10px solid $border-color;
   }
   ```

# 6. Partial 분할 폴더 구조 ★★★
   #### 6.1. abstracts
   - sass가 제공하는 기능적인 것들에 대한 정의
   - @mixin과 변수와 같은 css로 구체적 변환 전 추상적 정의들

   #### 6.2. base
   - css의 기본적이고 기능적인 설정

   #### 6.3. components 
   - 버튼이나 메뉴같은 마우스 컨트롤 요소들

   #### 6.4. layout
   - 페이지 내용 구성에 따른 각 부분별 요소
   - header, main, footer

# 7. 패스트캠퍼스 - SASS 강의 
## 7.1. 문법
   #### 중첩 - 벗어나기
   - 중첩에서 벗어나고 싶을 때 @at-root 키워드 사용
   - 중첩 안에서 생성하되 중첩 밖에서 사용해야 하는 경우 유용
   - 변수는 { } 로 유효범위 ※ 선언된 { } (중괄호) 안에서만 유효!
   ```
   .list {
      $w: 100px;
      $h: 50px;

      li {
         width: $w;
         height: $h;
      }

      @at-root .box {
         width: $w;
         height: $h;
      }
   }
   ```
   - Compiled to:
   - .list 안에 있는 특정 변수를 범위 밖에서 사용할 수 없기 때문에, @at-root 키워드 사용
   ```
   .list li {
      width: 100px;
      height: 50px;
   }
   .box {
      width: 100px;
      height: 50px;
   }
   ```

   #### 중첩 - 중첩된 속성 정의
   - padding-, margin- 등과 같이 동일한 네임 스페이스를 가지고 속성들을 다음과 같이 사용할 수 있다.
   ```
   .box {
      font: {
         weight: bold;
         size: 10px;
         family: sans-serif;
      };
      margin: {
         top: 10px;
         left: 20px;
      };
      padding: {
         bottom: 40px;
         right: 30px;
      };
   }
   ```
   - Compiled to:
   ```
   .box {
      font-weight: bold;
      font-size: 10px;
      font-family: sans-serif;
      margin-top: 10px;
      margin-left: 20px;
      padding-bottom: 40px;
      padding-right: 30px;
   }   
   ```

   #### 변수 - 전역 설정
   - !global 플래그를 사용하면 변수의 유효범위를 전역(Global)로 설정
   ```
   $color: #000;
   .box1 {
      $color: #111 !global;
      background: $color;
   }
   .box2 {
      background: $color;
   }
   .box3 {
      $color: #222;
      background: $color;
   }
   ```
   - Compiled to:
   - $color 컬러값이 처음 #000 이었지만 box1에서 !global 플래그 사용함으로 컬러값 변경
   - box3 경우 변수를 재정의 -> 변수가 적용되는 곳을 기준으로 가장 가까운 곳에서 선언된 값이 적용
   ```
   .box1 {
      background: #111;
   }
   .box2 {
      background: #111;
   }
   .box3 {
      background: #222;
   }
   ```

   #### 변수 - !default (초깃값 설정)
   - !default 플래그는 할당되지 않은 변수의 초깃값을 설정
   - 즉, 할당되어있는 변수가 있다면 변수가 기존 할당 값을 사용
   ```
   $color-primary: red;

   .box {
      $color-primary: blue !default;
      background: $color-primary;
   }
   ```
   - Compiled to:
   - box에서 blue 로 선언하긴 했지만 !default 플래그를 사용함으로써 red로 "처음 초기값을 설정한 값"이 적용된다.
   ```
   .box {
      background: red;
   }
   ```
   - !default 를 사용하는 예 (라이브러리를 이용할 때)
   - 좀 더 유용하게, ‘변수와 값을 설정하겠지만, 혹시 기존 변수가 있을 경우는 현재 설정하는 변수의 값은 사용하지 않겠다’는 의미로 쓸 수 있습니다.
예를 들어, Bootstrap 같은 외부 Sass(SCSS) 라이브러리를 연결했더니 변수 이름이 같아 내가 작성한 코드의 변수들이 Overwrite(덮어쓰기) 된다면 문제가 있겠죠.
반대로 내가 만든 Sass(SCSS) 라이브러리가 다른 사용자 코드의 변수들을 Overwrite 한다면, 사용자들은 그 라이브러리를 더 이상 사용하지 않을 것입니다.
이럴 때 Sass(SCSS) 라이브러리(혹은 새롭게 만든 모듈)에서 사용하는 변수에 !default 플래그가 있다면 기존 코드(원본)를 Overwrite 하지 않고도 사용할 수 있습니다.
   - 다음은 Bootstrap 코드(_variables.scss)의 일부.
   ```
   // stylelint-disable
   $white:    #fff !default;
   $gray-100: #f8f9fa !default;
   $gray-200: #e9ecef !default;
   $gray-300: #dee2e6 !default;
   $gray-400: #ced4da !default;
   $gray-500: #adb5bd !default;
   $gray-600: #6c757d !default;
   $gray-700: #495057 !default;
   $gray-800: #343a40 !default;
   $gray-900: #212529 !default;
   $black:    #000 !default;
   ```

   #### 변수 - 문자 보간 {}
   - #{}를 이용해서 코드의 어디든지 변수 값을 넣을 수 있다
   - Sass의 내장 함수 unquote() => 문자에서 따옴표를 제거
   ```
   $family: unquote("Droid+Sans");
   @import url("http://fonts.googleapis.com/css?family=#{$family}");
   ```
   - Compiled to:
   ```
   @import url("http://fonts.googleapis.com/css?family=Droid+Sans");
   ```

   #### 여러파일 가져오기
   - , (콤마)를 이용해 가져오기 가능하다
   ```
   @import "header", "side-menu";
   ```

   #### 연산
   - Sass는 기본적인 연산 기능을 지원
   - 레이아웃 작업시 상황에 맞게 크기를 계산을 하거나 정해진 값을 나눠서 작성할 경우 유용
   - 산술 연산자 :
   ```
   +	더하기	
   -	빼기	
   *	곱하기	: 하나 이상의 값이 반드시 숫자(Number)    ex. 10px * 10px = error (단위끼리 곱하면 안됨.)  => 10px * 10 
   /	나누기	: 오른쪽 값이 반드시 숫자(Number)         ex. 10px / 2px  = error  =>  10px / 2
   %	나머지	
   ```
   - 비교 연산자 :
   ```
   ==	동등
   !=	부등
   <	대소 / 보다 작은
   >	대소 / 보다 큰
   <=	대소 및 동등 / 보다 작거나 같은
   >=	대소 및 동등 / 보다 크거나 같은
   ```
   - 논리(불린, Boolean) 연산자 :
   ```
   and	그리고
   or	   또는
   not	부정
   ```

   #### 연산 - 숫자
   - 상대적 단위 연산
   ```
   width: 50% - 20px;            // 단위 모순 에러(Incompatible units error)
   width: calc(50% - 20px);      // 연산 가능
   ```
   - 나누기 연산 충족 조건 (/를 나누기 연산 기능으로 사용하려면 다음과 같은 조건을 충족)
   - 값 또는 그 일부가 변수에 저장되거나 함수에 의해 반환되는 경우
   - 값이 ()로 묶여있는 경우
   - 값이 다른 산술 표현식의 일부로 사용되는 경우
   ```
   div {
      $x: 100px;
      width: $x / 2;               // 변수에 저장된 값을 나누기
      height: (100px / 2);         // 괄호로 묶어서 나누기
      font-size: 10px + 12px / 3;  // 더하기 연산과 같이 사용
   }
   ```
   - Compiled to:
   ```
   div {
      width: 50px;
      height: 50px;
      font-size: 14px;
   }
   ```

   #### 연산 - 문자
   - 문자 연산에는 +가 사용
   - 문자 연산의 결과는 첫 번째 피연산자를 기준
   - 첫 번째 피연산자에 따옴표가 붙어있다면 연산 결과를 따옴표로 묶는다
   - 반대로 첫 번째 피연산자에 따옴표가 붙어있지 않다면 연산 결과도 따옴표를 처리하지 않는다
   ```
   div::after {
      content: "Hello " + World;
      flex-flow: row + "-reverse" + " " + wrap
   }
   ```
   - Compiled to:
   - content 경우 "Hello " 에 따옴표가 붙어있어서 "Hello World" 로 출력
   - flex-flow 경우 row 문자가 " 없이 적용되었기 때문에 row-reverse wrap 로 출력
   ```
   div::after {
      content: "Hello World";
      flex-flow: row-reverse wrap;
   }
   ```

   #### 연산 - 색상
   - 색상도 연산이 가능하다
   - RGBA에서 Alpha 값은 연산되지 않으며 서로 동일해야 다른 값의 연산 가능
   ```
   div {
      color: #123456 + #345678;
      // R: 12 + 34 = 46
      // G: 34 + 56 = 8a
      // B: 56 + 78 = ce
      background: rgba(50, 100, 150, .5) + rgba(10, 20, 30, .5);
      // R: 50 + 10 = 60
      // G: 100 + 20 = 120
      // B: 150 + 30 = 180
      // A: Alpha channels must be equal
   }
   ```   
   - Compiled to:
   ```
   div {
      color: #468ace;
      background: rgba(60, 120, 180, 0.5);
   }
   ```
   - Alpha 값을 연산하기 위한 다음과 같은 색상 함수(Color Functions)를 사용할 수 있다 
   - opacify() - 더 불투명하게, transparentize() - 더 투명하게
   ```
   $color: rgba(10, 20, 30, .5);
   div {
      color: opacify($color, .3);                    // 30% 더 불투명하게 / 0.5 + 0.3
      background-color: transparentize($color, .2);  // 20% 더 투명하게 / 0.5 - 0.2
   }
   ```   
   - Compiled to:
   ```
   div {
      color: rgba(10, 20, 30, 0.8);
      background-color: rgba(10, 20, 30, 0.3);
   }
   ```

   #### 연산 - 논리
   - Sass의 @if 조건문에서 사용되는 논리(Boolean) 연산에는 ‘and 그리고’ , ‘or 또는’ , ‘not 부정’ 이 있다
   - 자바스크립트 문법에서 &&, ||, !와 같은 기능
   - and 는 모두 참일 때, or 은 둘 중 한 개만이라도 참일 때
   ```
   $width: 90px;
   div {
      @if not ($width > 100px) {
         height: 300px;
      }
      
      @if ($width > 10px and $width < 100px ) {
         color: #f00;
      }
   }
   ```
   - Compiled to:
   ```
   div {
      height: 300px;
      color: #f00;
   }
   ```

   #### 재활용 (Mixin) - Mixin, include
   - mixin : 재사용 할 CSS 선언 그룹 을 정의하는 아주 훌륭한 기능
   - Mixin 두 가지만 기억 : 선언하기(@mixin)와 포함하기(@include) 
   - 선언하기 @mixin
   - Mixin은 선택자를 포함 가능하고 상위(부모) 요소 참조(& 같은)도 할 수 있다
   ```
   @mixin large-text {
      font: {
         size: 22px;
         weight: bold;
         family: sans-serif;
      }
      color: orange;

      &::after {
         content: "!!";
      }

      span.icon {
         background: url("/images/icon.png");
      }
   }
   ```
   - 포함하기 @include
   ```
   h1 {
      @include large-text;
   }
   div {
      @include large-text;
   }
   ```
   - Compiled to:
   ```
   h1 {
      font-size: 22px;
      font-weight: bold;
      font-family: sans-serif;
      color: orange;
   }
   h1::after {
      content: "!!";
   }
   h1 span.icon {
      background: url("/images/icon.png");
   }

   div {
      font-size: 22px;
      font-weight: bold;
      font-family: sans-serif;
      color: orange;
   }
   div::after {
      content: "!!";
   }
   div span.icon {
      background: url("/images/icon.png");
   }
   ```

   #### 재활용 (Mixin) - 인수
   - Mixin은 함수(Functions)처럼 인수(Arguments)를 가질 수 있다
   - 하나의 Mixin으로 다양한 결과를 만들 수 있다
   ```
   // SCSS
   @mixin 믹스인이름($매개변수) {
      스타일;
   }
   @include 믹스인이름(인수);
   ```
   - 매개변수(Parameters)란 변수의 한 종류로, 제공되는 여러 데이터 중 하나를 가리키기 위해 사용된다.
   - 제공되는 여러 데이터들을 전달인수(Arguments) 라고 부른다.
   ```
   @mixin dash-line($width, $color) {
      border: $width dashed $color;
   }

   .box1 { @include dash-line(1px, red); }
   .box2 { @include dash-line(4px, blue); }
   ```
   - Compiled to:
   ```
   .box1 {
      border: 1px dashed red;
   }
   .box2 {
      border: 4px dashed blue;
   }
   ```
   
   #### 재활용 (Mixin) - 인수 기본값 설정
   ```
   @mixin 믹스인이름($매개변수: 기본값) {
      스타일;
   }
   ```
   ```
   @mixin dash-line($width: 1px, $color: black) {
      border: $width dashed $color;
   }

   .box1 { @include dash-line; }
   .box2 { @include dash-line(4px); }
   ```
   - Compiled to:
   ```
   .box1 {
      border: 1px dashed black;
   }
   .box2 {
      border: 4px dashed black;
   }
   ```

   #### 재활용 (Mixin) - 키워드 인수
   - 인수는 매개변수에 순서대로 정의가 된다. 
   - @include 믹스인이름(인수); 로 적용하면 인수 값이 A, B 각각 들어가게 된다.
   - ex. $매개변수A는 기본값으로 주고 $매개변수B에만 값을 지정해줘야 할 때
   ```
   @mixin 믹스인이름($매개변수A: 기본값, $매개변수B: 기본값) {
      스타일;
   }
   
   @include 믹스인이름($매개변수B: 인수);
   ```
   - Mixin에 전달할 인수를 입력할 때 명시적으로 키워드(변수)를 입력하여 작성할 수 있다
   - 별도의 인수 입력 순서를 필요로 하지 않아 편리하게 작성할 수 있다
   - 단, 작성하지 않은 인수가 적용될 수 있도록 기본값을 설정해 주는 것이 좋다
   - 속성값으로 null이 사용되면 컴파일하지 않는다.
   ```
   @mixin position( $p: absolute, $t: null, $b: null, $l: null, $r: null ) {
      position: $p;
      top: $t;
      bottom: $b;
      left: $l;
      right: $r;
   }

   .absolute {
      // 키워드 인수로 설정할 값만 전달
      @include position($b: 10px, $r: 20px);
   }
   .fixed {
      // 인수가 많아짐에 따라 가독성을 확보하기 위해 줄바꿈
      @include position(
         fixed,
         $t: 30px,
         $r: 40px
      );
   }
   ```
   - Compiled to:
   ```
   .absolute {
      position: absolute;
      bottom: 10px;
      right: 20px;
   }
   .fixed {
      position: fixed;
      top: 30px;
      right: 40px;
   }
   ```

   #### 재활용 (Mixin) - 가변 인수
   - 때때로 입력할 인수의 개수가 불확실한 경우가 있다
   - 그럴 경우 가변 인수를 사용할 수 있는데,가변 인수는 매개변수 뒤에 ... 을 붙여준다
   ```
   @mixin 믹스인이름($매개변수...) {
      스타일;
   }

   @include 믹스인이름(인수A, 인수B, 인수C);
   ```
   - 특정 매개변수 ...  = 인수의 개수에 상관없이 받아준다.
   ```
   // 인수를 순서대로 하나씩 전달 받다가, 3번째 매개변수($bg-values)는 인수의 개수에 상관없이 받음
   @mixin bg($width, $height, $bg-values...) {
      width: $width;
      height: $height;
      background: $bg-values;
   }

   div {
      // 위의 Mixin(bg) 설정에 맞게 인수를 순서대로 전달하다가 3번째 이후부터는 개수에 상관없이 전달
      @include bg(
         100px,
         200px,
         url("/images/a.png") no-repeat 10px 20px,
         url("/images/b.png") no-repeat,
         url("/images/c.png")
      );
   }
   ```
   - 인수를 받는 매개변수에 ...을 사용하여 가변 인수를 활용
   ```
   div {
      width: 100px;
      height: 200px;
      background: url("/images/a.png") no-repeat 10px 20px,
                  url("/images/b.png") no-repeat,
                  url("/images/c.png");
   }
   ```
   ###### - 가변 인수를 전달할 값으로 사용할 때
   ```
   @mixin font(
      $style: normal,
      $weight: normal,
      $size: 16px,
      $family: sans-serif
   ) {
      font: {
         style: $style;
         weight: $weight;
         size: $size;
         family: $family;
      }
   }
   div {
      // 매개변수 순서와 개수에 맞게 전달
      // 변수에 배열처럼 값을 전달할 수 있다.
      // Lists 데이터 형식 (https://heropy.blog/2018/01/31/sass/ 데이터종류 참고)
      $font-values: italic, bold, 16px, sans-serif;
      @include font($font-values...);
   }
   span {
      // 필요한 값만 키워드 인수로 변수에 담아 전달
      $font-values: (style: italic, size: 22px);
      @include font($font-values...);
   }
   a {
      // 필요한 값만 키워드 인수로 전달
      // Maps 데이터 형식 (https://heropy.blog/2018/01/31/sass/ 데이터종류 참고)
      @include font((weight: 900, family: monospace)...);
   }
   ```
   - Compiled to:
   ```
   div {
      font-style: italic;
      font-weight: bold;
      font-size: 16px;
      font-family: sans-serif;
   }
   span {
      font-style: italic;
      font-weight: normal;
      font-size: 22px;
      font-family: sans-serif;
   }
   a {
      font-style: normal;
      font-weight: 900;
      font-size: 16px;
      font-family: monospace;
   }
   ```

   #### 재활용 (Mixin) - @content (상단 내용(미디어쿼리)도 참고)
   - 선언된 Mixin에 @content이 포함되어 있다면 해당 부분에 원하는 스타일 블록 을 전달할 수 있다
   - 이 방식을 사용하여 기존 Mixin이 가지고 있는 기능에 선택자나 속성 등을 추가할 수 있다
   ```
   @mixin 믹스인이름() {
   스타일;
      @content;
   }

   @include 믹스인이름() {
      // 스타일 블록
      스타일;
   }
   ```
   - { 작성한 코드는 } @content 위치에 적용된다.
   ```
   @mixin icon($url) {
      &::after {
         content: $url;
         @content;
      }
   }
   .icon1 {
      // icon Mixin의 기존 기능만 사용
      @include icon("/images/icon.png");
   }
   .icon2 {
      // icon Mixin에 스타일 블록을 추가하여 사용
      @include icon("/images/icon.png") {
         position: absolute;
      };
   }
   ```
   - Compiled to:
   ```
   .icon1::after {
      content: "/images/icon.png";
   }
   .icon2::after {
      content: "/images/icon.png";
      position: absolute;
   }
   ```
   - Mixin에게 전달된 스타일 블록은 Mixin의 범위가 아니라 스타일 블록이 정의된 범위에서 평가됩니다.
   - 즉, Mixin의 매개변수는 전달된 스타일 블록 안에서 사용되지 않고 전역 값으로 해석됩니다.
   - 전역 변수(Global variables)와 지역 변수(Local variables)를 생각하면 좀 더 쉽습니다.
   ```
   $color: red;

   @mixin colors($color: blue) {
      // Mixin의 범위
      @content;
      background-color: $color;
      border-color: $color;
   }

   div {
      @include colors() {
         // 스타일 블록이 정의된 범위
         color: $color;
      }
   }
   ```
   - Compiled to:
   ```
   div {
      color: red;
      background-color: blue;
      border-color: blue;
   }
   ```

   #### 확장 - Extend
   - 특정 선택자가 다른 선택자의 모든 스타일을 가져야하는 경우
   ```
   // @extend 선택자;

   .btn {
      padding: 10px;
      margin: 10px;
      background: blue;
   }
   .btn-danger {
      @extend .btn;
      background: red;
   }
   ```
   - Compiled to:
   ```
   .btn, .btn-danger {
      padding: 10px;
      margin: 10px;
      background: blue;
   }
   .btn-danger {
      background: red;
   }
   ```
   ###### extend - 추천하지 않는 이유
   - 결과를 보면 ,로 구분하는 다중 선택자(Multiple Selector)가 만들어진다.
   - @extend는 다음과 같은 문제를 고려해야 한다
      1. 내 현재 선택자(위 예제의 .btn-danger)가 어디에 첨부될 것인가?
      2. 원치 않는 부작용이 초래될 수도 있는가?
      3. 이 한 번의 확장으로 얼마나 큰 CSS가 생성되는가?
      4. 결과적으로 확장(Extend) 기능은 무해하거나 혹은 유익할 수도 있지만 그만큼 부작용을 가지고 있을 수 있다
      5. 따라서 확장은 사용을 권장하지 않으며, 위에서 살펴본 Mixin을 대체 기능으로 사용.
   - extend 를 권장하지 않는 자세한 이유가 궁금할 땐 https://sass-guidelin.es/ko/#extend

   #### 함수(Functions)
   - 자신의 함수를 정의하여 사용
   - 함수와 Mixins은 거의 유사하지만 반환되는 내용이 다르다
   - Mixin은 지정한 스타일(Style)을 반환하는 반면, 함수는 보통 연산된(Computed) "특정 값"을 @return 지시어를 통해 반환.
   ```
   // Mixins
   @mixin 믹스인이름($매개변수) {
      스타일;
   }

   // Functions
   @function 함수이름($매개변수) {
      @return 값
   }
   ```
   - 사용하는 방법에도 차이가 있다
   - Mixin은 @include 지시어를 사용하는 반면, 함수는 함수이름으로 바로 사용
   - 함수이름();
   ```
   $max-width: 980px;

   @function columns($number: 1, $columns: 12) {
      @return $max-width * ($number / $columns)
   }

   .box_group {
      width: $max-width;

      // box1 ~ 3번까지 columns 기본값 12 적용
      .box1 {
         width: columns();  // 1   - $number 도 기본값 적용으로 1을 굳이 쓰지 않아도 된다.
      }
      .box2 {
         width: columns(8);
      }
      .box3 {
         width: columns(3);
      }
   }
   ```
   - Compiled to:
   ```
   .box_group {
      /* 총 너비 */
      width: 980px;
   }
   .box_group .box1 {
      /* 총 너비의 약 8.3% */
      width: 81.66667px;
   }
   .box_group .box2 {
      /* 총 너비의 약 66.7% */
      width: 653.33333px;
   }
   .box_group .box3 {
      /* 총 너비의 25% */
      width: 245px;
   }
   ```

   #### 함수 - 함수 이름 중복
   - 함수는 @include 같은 별도의 지시어 없이 사용하기 때문에 내가 지정한 함수와 내장 함수(Built-in Functions)의 이름이 충돌할 수 있다
   - ★ 내가 지정한 함수에는 별도의 접두어를 붙여주는 것이 좋다 ★   
      - 예를 들어, 색의 빨강 성분을 가져오는 내장 함수로 이미 red()가 있다.
      - 같은 이름을 사용하여 함수를 정의하면 이름이 충돌하기 때문에 별도의 접두어를 붙여 extract-red() 같은 이름을 만들 수 있다
      - ex. my-custom-func-red()  
    
   - 내장 함수란, 응용 프로그램에 내장되어 있으며 최종 사용자가 액세스 할 수 있는 기능이다. 예를 들어, 대부분의 스프레드 시트 응용 프로그램은 행이나 열의 모든 셀을 추가하는 내장 SUM 함수를 지원한다.
  
   ```
   // 내가 정의한 함수
   @function extract-red($color) {
      // 내장 함수
      @return rgb(red($color), 0, 0);
   }

   div {
      color: extract-red(#D55A93);
   }
   ```
   #### 함수 - IF함수
   - 조건의 값(true, false)에 따라 두 개의 표현식 중 하나만 반환
   - ★ 조건부 삼항 연산자(conditional ternary operator)와 비슷하다 ★
   - 조건의 값이 true이면 표현식1을, 조건의 값이 false이면 표현식2를 실행한다
   ```
   // if(조건, 표현식1, 표현식2)
   
   $width: 555px;
   div {
      width: if($width > 300px, $width, null);
   }
   ```
   - Compiled to:
   ```
   div {
      width: 555px;
   }
   ```

   #### 조건문 - @if (지시어)
   - @if 지시어는 조건에 따른 분기 처리가 가능하며, ★ if 문(if statements)과 유사 ★
   - 같이 사용할 수 있는 지시어는 @else, if 가 있습니다.
   - 추가 지시어를 사용하면 좀 더 복잡한 조건문을 작성할 수 있다

   ```
   // @if
   @if (조건) {
      /* 조건이 참일 때 구문 */
   }

   // @if @else
   @if (조건) {
      /* 조건이 참일 때 구문 */
   } @else {
      /* 조건이 거짓일 때 구문 */
   }

   // @if @else if
   @if (조건1) {
      /* 조건1이 참일 때 구문 */
   } @else if (조건2) {
      /* 조건2가 참일 때 구문 */
   } @else {
      /* 모두 거짓일 때 구문 */
   }
   ```

   - 조건에 ()는 생략이 가능하기 때문에, () 없이 작성하는 방법이 좀 더 편리히다
   ```
   $bg: true;
   div {
      @if $bg {
         background: url("/images/a.jpg");
      }
   }
   ```

   - SCSS (예제) :
   - 조건에는 논리 연산자 and, or, not을 사용힐 수 있다
   ```
   $color: orange;
   div {
      @if $color == strawberry {
         color: #FE2E2E;
      } @else if $color == orange {
         color: #FE9A2E;
      } @else if $color == banana {
         color: #FFFF00;
      } @else {
         color: #2A1B0A;
      }
   }
   ```
   - Compiled to:
   ```
   div {
      color: #FE9A2E;
   }
   ```

   #### 함수와 @if문 예제 01
   - limitSize 함수를 만들고 0보다 같거나 크고 200px보다 작거나 같은 if문 조건 생성
   ```
   @function limitSize($size) {
      @if $size >= 0 and $size <= 200px {
         @return 200px;
      }
      @else {
         @return 800px;
      }
   }

   div {
      width: limitSize(180px);
      height: limitSize(340px);
   }
   ```
   - Compiled to:
   ```
   div {
      width: 200px;
      height: 800px;
   }
   ```

   #### 함수와 @if문 예제 02
   - position 속성을 이용해 같은 정렬을 하려고 한다
   - unitless() : 단위가 붙어 있는 지 없는 지 확인해주는 내장함수
   ```
   @mixin positionCenter($w, $h, $p: absolute) {
      // position 값이 relative 이거나 static 이면 값이 null 이기때문에 컨파일되지 않음.
      @if (
         $p == absolute or
         $p == fixed or 
         not $p == relative or
         not $p == static
      ) {
         // if함수를 이용해서 단위표시가 없으면 px 같 붙여주기
         // unitless() - 내장함수로 단위 표시가 없는 것을 확인하는 함수
         // $w에 단위 표시가 없으면 px를 붙여주라는 뜻
         // #{변수}px - #{}를 이용해서 코드의 어디든지 변수 값을 넣을 수 있다
         width: if(unitless($w),#{$w}px, $w);
         height: if(unitless($h),#{$h}px, $h);
         position: $p;
         top: 0;
         bottom: 0;
         left: 0;
         right: 0;
         margin: auto;    
      }
   }

   .box1 {
      @include positionCenter(10px, 20px);
   }
   .box2 {
      @include positionCenter(50, 50, fixed);
   }
   .box3 {
      @include positionCenter(100, 200, relative);
   }
   ```
   - Compiled to:
   - .box3은 if문 조건에 따라 relative 이기 때문에 값이 null > 컨파일 되지 않았다.
   ```
   .box1 {
      width: 10px;
      height: 20px;
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      margin: auto;
   }

   .box2 {
      width: 50px;
      height: 50px;
      position: fixed;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      margin: auto;
   }
   ```

   #### 반복문 - @for
   - for는 스타일을 반복적으로 출력한다. (= for 문과 유사)
   - @for는 through를 사용하는 형식과 to를 사용하는 형식으로 나뉜다. 두 형식은 종료 조건이 해석되는 방식이 다르다
   - @for 에서 $변수 = 매개변수 의미
   ```
   // through
   // 종료 만큼 반복
   @for $변수 from 시작 through 종료 {
      // 반복 내용
   }

   // to
   // 종료 직전까지 반복
   @for $변수 from 시작 to 종료 {
      // 반복 내용
   }
   ```
   - 변수는 $i, $index 를 사용한다.
   ```
   // 1부터 3번 반복
   @for $i from 1 through 3 {
      .through:nth-child(#{$i}) {
         width : 20px * $i
      }
   }

   // 1부터 3 직전까지만 반복(2번 반복)
   @for $i from 1 to 3 {
      .to:nth-child(#{$i}) {
         width : 20px * $i
      }
   }
   ```
   - Compiled to:
   - to는 주어진 값 직전까지만 반복해야할 경우 유용하다
   - :nth-child()에서 특히 유용하게 사용되는 @for는 일반적으로 through를 사용하길 권장
   ```
   .through:nth-child(1) { width: 20px; }
   .through:nth-child(2) { width: 40px; }
   .through:nth-child(3) { width: 60px; }

   .to:nth-child(1) { width: 20px; }
   .to:nth-child(2) { width: 40px; }
   ```

   #### 반복문 - @each
   - @each는 List와 Map 데이터를 반복할 때 사용한다
   - for in 문과 유사하다.
   ```
   @each $변수 in 데이터 {
   // 반복 내용
   }
   ```

   ###### @each - List 데이터 반복 예제 01
   - List 데이터는 () 를 생략할 수 있다
   - @each 반복문 - List 데이터는 왼쪽 순으로 반복이 된다.
   - li 태그를 반복해야 하기 때문에 @each { li {} }
   ```
   // List Data
   $fruits: (apple, orange, banana, mango);

   .fruits {
      @each $fruit in $fruits {
         li.#{$fruit} {
            background: url("/images/#{$fruit}.png");
         }
      }
   }
   ```
   - Compiled to:
   ```
   .fruits li.apple {
      background: url("/images/apple.png");
   }
   .fruits li.orange {
      background: url("/images/orange.png");
   }
   .fruits li.banana {
      background: url("/images/banana.png");
   }
   .fruits li.mango {
      background: url("/images/mango.png");
   }
   ```

   ###### @each - List 데이터 반복 예제 02
   - index() 내장 함수를 사용한 @each - List 반복문
   - index 값이 필요할 때 사용한다
   ```
   $fruits: apple, orange, banana, mango;

   .fruits {
      @each $fruit in $fruits {
         // 데이터에서 변수가 몇 번째인지 인덱스값 추출
         $index: index($fruits, $fruit);
         
         li:nth-child(#{$index}) {
            left: 50px * $index;
            background: url("/images/#{$fruit}.png");
         }
      }
   }
   ```
   - Compiled to:
   ```
   .fruits li:nth-child(1) {
      left: 50px;
      background: url("/images/apple.png");
   }

   .fruits li:nth-child(2) {
      left: 100px;
      background: url("/images/orange.png");
   }

   .fruits li:nth-child(3) {
      left: 150px;
      background: url("/images/banana.png");
   }

   .fruits li:nth-child(4) {
      left: 200px;
      background: url("/images/mango.png");
   }

   ```

   ###### @each - Map 데이터 반복 예제 03
   - 동시에 여러 개의 List 데이터를 반복 처리할 수도 있다
   - ★ 단, 각 데이터의 Length가 같아야 한다 ★
   - Map 데이터는 () 필수
   ```
   // Map 데이터는 () 필수
   $fruits-data: (
      // key: value,
      apple: korea,
      orange: china,
      banana: japan
   );

   // Map 데이터는 Key, Value 값을 받을 변수가 각각 필요하다
   // @each $key, $value in $fruits-data {}
   @each $fruit, $country in $fruits-data {
      .box-#{$fruit} {
         background: url("/images/#{$country}.png");
      }
   }
   ```
   - Compiled to:
   ```
   .box-apple {
      background: url("/images/korea.png");
   }

   .box-orange {
      background: url("/images/china.png");
   }

   .box-banana {
      background: url("/images/japan.png");
   }
   ```

   ###### @each - Map 데이터 반복 예제 04
   - Map 데이터는 index() 함수 사용 불가!! List 데이터만 가능하다
   - map 데이터 경우, map-keys(데이터 변수명) 또는 map-values(데이터 변수명)을 통해 list 데이터 형태로 추출할 수 있다.
   - list 데이터 형태로 추출한 후에 index() 함수를 사용한다.
   - $fruits-data--key-list 변수에 map-keys 함수를 이용하여 $fruits-data를 list 데이터 형태로 추출한다.

   ```
   $fruits-data: (
      // key: value,
      apple: korea,
      orange: china,
      banana: japan
   );

   @each $fruit, $country in $fruits-data {
      
      // map-keys($fruits-data)   => (apple, orange, china)
      // map-values($fruits-data) => (korea, china, japan)
      
      $fruits-data--key-list: map-keys($fruits-data);
      $index: index($fruits-data--key-list, $fruit);

      
      .box-#{$fruit} {
         width: 100px * $index;
         background: url("/images/#{$country}.png");
      }
   }
   ```
   - Compiled to:
   ```
   .box-apple {
      width: 100px;
      background: url("/images/korea.png");
   }

   .box-orange {
      width: 200px;
      background: url("/images/china.png");
   }

   .box-banana {
      width: 300px;
      background: url("/images/japan.png");
   }
   ```

   #### 반복문 - @while
   - @while은 조건이 false로 평가될 때까지 내용을 반복한다
   - ★ while 문과 유사하게 잘못된 조건으로 인해 컴파일 중 무한 루프에 빠질 수 있다 ★
   - 사용을 권장하지 않는다 (조건이 명확할 때에만 사용하는 것을 권장한다)
   ```
   @while 조건 {
      // 반복 내용
   }
   ```
   ```
   $i: 6;

   @while $i > 0 {
      .item-#{$i} {
         width: 2px * $i;
      }
      $i: $i - 2;
   }
   ```
   - Compiled to:
   ```
   .item-6 { width: 12px; }
   .item-4 { width: 8px; }
   .item-2 { width: 4px; }
   ```

## 7.2. 내장함수
   #### 내장 함수(Built-in Functions)
   - Sass에서 기본적으로 제공하는 내장 함수에는 많은 종류가 있다
   - 주관적 경험에 의거해 필요하거나 필요할 수 있는 함수 정리
   - Sass Built-in Functions (https://sass-lang.com/documentation/modules) 에서 모든 내장 함수 확인 가능하다
      1. 내장함수 목록을 볼 때, [ ]는 선택 가능한 인수(argument)
         - 예시 : str-slice($string, $start-at, [$end-at])
      2. Zero-based numbering을 사용하지 않는다 (sass 에서는 0부터 숫자를 세지 않는다)
   
   #### 색상(RGB / HSL / Opacity) 함수
   ```
   mix($color1, $color2)
      : 두 개의 색을 섞습니다.

   lighten($color, $amount) 
      : 더 밝은색을 만듭니다.

   darken($color, $amount) 
      : 더 어두운색을 만듭니다.

   saturate($color, $amount) 
      : 색상의 채도를 올립니다.

   desaturate($color, $amount) 
      : 색상의 채도를 낮춥니다.

   grayscale($color) 
      : 색상을 회색으로 변환합니다.

   invert($color) 
      : 색상을 반전시킵니다.

   rgba($color, $alpha) 
      : 색상의 투명도를 변경합니다.

   opacify($color, $amount) / fade-in($color, $amount) 
      : 색상을 더 불투명하게 만듭니다.

   transparentize($color, $amount) / fade-out($color, $amount) 
      : 색상을 더 투명하게 만듭니다.
   ```

   #### 문자(String) 함수
   ```
   unquote($string) 
      : 문자에서 따옴표를 제거합니다.

   quote($string) 
      : 문자에 따옴표를 추가합니다.

   str-insert($string, $insert, $index) 
      : 문자의 index번째에 특정 문자를 삽입합니다.

   str-index($string, $substring) 
      : 문자에서 특정 문자의 첫 index를 반환합니다.

   str-slice($string, $start-at, [$end-at]) 
      : 문자에서 특정 문자(몇 번째 글자부터 몇 번째 글자까지)를 추출합니다.

   to-upper-case($string) 
      : 문자를 대문자를 변환합니다.

   to-lower-case($string) 
      : 문자를 소문자로 변환합니다.
   ```
   ###### str-insert, str-index, str-slice 예제
   ```
   div {
      width: str-insert("abcd", "xxx", 4);
      height: str-index("abcd", "c");
      position: str-slice("abcd", 2,3);
      // 끝까지 잘라내야할 땐 생략이 가능하다
      position: str-slice("abcd", 3);
   }
   ```
   - Compiled to:
   ```
   div {
      width: "abcxxxd";
      height: 3;
      position: "bc";
      position: "cd";
   }
   ```

   #### 숫자(Number) 함수
   ```
   percentage($number) 
      : 숫자(단위 무시)를 백분율로 변환합니다.

   round($number) 
      : 정수로 반올림합니다.

   ceil($number) 
      : 정수로 올림합니다.

   floor($number) 
      : 정수로 내림(버림)합니다.

   abs($number) 
      : 숫자의 절대 값을 반환합니다.

   min($numbers…) 
      : 숫자 중 최소 값을 찾습니다.

   max($numbers…) 
      : 숫자 중 최대 값을 찾습니다.

   random() 
      : 0 부터 1 사이의 난수를 반환합니다.
   ```

   #### List 함수
   - 모든 List 내장 함수는 기존 List 데이터를 갱신하지 않고 새 List 데이터를 반환한다
   - 모든 List 내장 함수는 Map 데이터에서도 사용할 수 있다
   ```
   length($list) 
      : List의 개수를 반환합니다.

   nth($list, $n) 
      : List에서 n번째 값을 반환합니다.

   set-nth($list, $n, $value) 
      : List에서 n번째 값을 다른 값으로 변경합니다.

   join($list1, $list2, [$separator]) 
      : 두 개의 List를 하나로 결합합니다.

   zip($lists…) 
      : 여러 List들을 하나의 다차원 List로 결합합니다.

   index($list, $value) 
      : List에서 특정 값의 index를 반환합니다.
   ```

   #### Map 함수
   - 모든 Map 내장 함수는 기존 Map 데이터를 갱신하지 않고 새 Map 데이터를 반환한다
   ```
   map-get($map, $key) 
      : Map에서 특정 key의 value를 반환합니다.

   map-merge($map1, $map2) 
      : 두 개의 Map을 병합하여 새로운 Map를 만듭니다.

   map-keys($map) 
      : Map에서 모든 key를 List로 반환합니다.

   map-values($map) 
      : Map에서 모든 value를 List로 반환합니다.
   ```

   #### 관리(Introspection) 함수
   ```
   variable-exists(name) 
      : 변수가 현재 범위에 존재하는지 여부를 반환합니다.(인수는 $없이 변수의 이름만 사용합니다.)

   unit($number) 
      : 숫자의 단위를 반환합니다.

   unitless($number) 
      : 숫자에 단위가 있는지 여부를 반환합니다.

   comparable($number1, $number2) 
      : 두 개의 숫자가 연산 가능한지 여부를 반환합니다.
   ```

   #### 참고 자료(References)
   - http://sass-lang.com/documentation
   - https://www.sitepoint.com/sass-basics-operators/
   - https://sass-guidelin.es/ko/
   - http://www.thesassway.com/