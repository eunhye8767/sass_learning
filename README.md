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
       


# SASS(CSS Preprocessor
