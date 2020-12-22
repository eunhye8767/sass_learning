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
   ## 5.9.2 - 1 Partial (파셜)
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

   ## 5.9.3 - 2 Media Queries (미디어쿼리) ★★★
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

   ## 5.9.3 - 3 mixin & Media Queries & if문 ★★★
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