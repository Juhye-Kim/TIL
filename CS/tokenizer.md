## tokenizer, lexer, parser

**파싱(Parsing)**

- '구문 분석' : 문장을 구성 성분으로 분해하고 그들 사이의 위계 관계를 분석해 문장 구조를 결정하는 것
- CS에서는 문자열을 의미 있는 토큰 단위로 분해하고, parse tree로 변환하는 과정을 뜻함

**파서(Parser)**

- 파싱을 수행하는 프로그램 - 세 가지 구성 요소로 나뉨
  <img width="721" alt="스크린샷 2021-07-26 오후 1 02 35" src="https://user-images.githubusercontent.com/63178953/126931468-1f485b3e-86aa-49b5-a778-9815feddcf61.png">

  1. **tokenizer :** input을 알맞은 토큰 단위로 나눠줌
  2. **lexer :** 나눠진 토큰들을 분석해, 문맥적 의미 부여
  3. **parser :** 분석된 token들을 문법적으로 검사, **parse tree**(**AST**로 나타내기도 함)로 만들어줌
     - tokenizer + lexer를 lexer라고 하기도 함
     - lexer → parser는 연속적으로 작동

**Parse Tree, AST**

- Parse Tree는 input 전체를 구체적으로 표현해 공백, 괄호 모두 들어갑니다.
  <img width="400" alt="스크린샷 2021-07-26 오후 1 02 35" src="https://jsnow.netlify.app/static/aabb9e6b362564089bf1b3b1d0806542/664c8/Untitled.png">

- AST는 input을 축약하여 표현해 부모가 없고, 괄호가 들어가지 않습니다.
  <img width="400" alt="스크린샷 2021-07-26 오후 1 02 35" src="https://jsnow.netlify.app/static/b146e3e150c9a6e62b3f01b308c0e8f2/3d84d/mpdm.png">
