# VS Code 설정 Tip
## scss 할 때 상황에 맞게 컴파일러를 하기 위한 Tip
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
   - 프로젝트별 저장경로 등 json 편집을 달리하고 싶을 땐,
     해당 프로젝트에 .vscode 폴더 생성 후 settings.json 파일 생성.
      ```
      {
         속성: 속성값 적용
      }
      ```



# VS Code에서 Satch Sass 실행이  안될 때
1. 폴더 영역 추가가 아닌 ★ "폴더 열기"로 해당 폴더를 열어★ 야 한다.



# VS Code 확장 프로그램 설치
## 1.1. Live Sass Compiler
   - 설정 > 사용자, (왼쪽) 확장에서 "Live Sass Compile" 선택
   - Live Sass Compile > settings: Formats 위치, settings.json에서 편집 선택
   - 해당 부분에서 저장경로, map 파일 저장 유무 등 편집 가능.
   - Live Sass Compile 경우, 확장프로그램에서 "Live Sass Compile" 검색 후
   상세 페이지를 보면 "Settings Docs." 이 부분 클릭. (클릭하면 새 창 열리고, 어떻게 커스텀 하는 지 확인 가능)
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


## 1.2. 프로젝트별 setting 설정하기 (Tip 4번참고)
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


## 1.3 Live Server
   - html 페이지에서 오른쪽 마우스 클릭 > Open With Live Server 클릭 (브라우저로 연결 > 페이지 오픈)
   - 또는 아래(상태 표시줄) Go Live 버튼을 클릭해준다. 
   - html 페이지 수정 작업 시, Liver Server로 열린 브라우저에서 자동 확인이 된다.
      > Live Server 열었을 때, Port 에러가 날 경우, 아래 코드를 사용자 설정 .json 파일에서 입력 후 다시 Open With Liver Server로 열어준다.
      >  > - 사용자 설정 json 파일에서 아래 코드를 입력해준다
   ```
   "LiveServer.settings.port": 0
   ```
   - Go Live를 닫고 싶을 땐, 아래 (상태표시줄에서) Port:  부분을 클릭해주면 된다.



## 2. Sass 
## 3. Sass Lint



# SASS(SCSS) Preprocessor
css 작성(생성)을 위한 작고 가벼운 언어이고, Sass와 Scss가 있다.
- Sass : SCSS와 작성하는데 있어서 구조적 차이가 있고 작성이 번거롭고 복잡할 수 있다.
- SCSS : 기존에 알던 CSS와 유사하게 작성할 수 있기 때문에 친근하게 느껴져 배우기가 쉽다. ★


## 1. Sass 컴파일러 방식
- VS Code + Live Sass Compiler ★
- Ruby Gem을 이용한 컴파일러 
- Node.js NPM을 이용한 컴파일러
- Ruby, Node.js 을 이용한 컴파일러는 Scss에 대해 알고 난 후 배워도 무방하다. (=복잡하다)

## 2. Watch Sass
1. .scss 파일을 열면 아래(상태표시줄) Wahch Sass 버튼이 보여진다
2. Wahch Sass 을 클릭하면 컴파일러되면서 .css 파일이 자동 생성이 된다.
3. Wahch Sass 누르고 난 후 해당 부분이 Watching.. 으로 바뀌는데 이 경우 .scss 파일을 작업하면서 저장을 누르면 css 파일에 자동으로 파일이 컴파일러 된다.
4. .css 파일에 자동 적용되지 않게 하려면 watching.. 버튼을 클릭해주면 된다.


## 3. 컴파일러된 css 파일 연결
1. .scss 파일이 아닌 컴파일러된  .css 파일을 html 문서에 link



# Sass Basic Project
sass(scss)는 css를 작성하는 css를 만드는 언어로 css 모든 것을 다 포함. css 그대로 작성해도 무방하다. 
## 01. Variables (변수)
1. 변수를 선언하고 중복되는 값에 적용을 해준다.
2. 변수 선언은 '무조건' $ 로 시작한다.
3. 변수명은 영문으로 시작해야하고 숫자, -(대쉬), _(언더바) 만 포함할 수 있다.
4. 선언한 변수는 css 문법에서 속성명 : 변수 로 쓴다.
```
$bg-color: #00f; ($변수명: 속성값;)

#box1 {
   color: #ff0;
   background-color: $bg-color;  /* 속성명: 변수 */
   width: 100px;
}
```