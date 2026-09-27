# document.write() 사용법

자바스크립트의 `document` 객체는 웹 브라우저에 로드된 웹 페이지 그 자체(HTML 문서)를 의미하는 전역 객체이다.  
`document.write()` 문은 웹 문서(document)에서 괄호 안의 내용을 표시하는 명령문이다.

`document.write()` 의 괄호 안에는 실제 웹 브라우저 화면에 표시할 내용이나 어떤 결과값이 저장된 변수를 넣을 수도 있다.  
괄호 안에서 큰 따옴표나 작은 따옴표 사이에 입력한 내용이 웹 브라우저 화면에 그대로 표시된다.  
물론 HTML 태그도 함께 사용할 수 있다.  

```javascript
document.write("<h1>안녕하세요</h1>");
```

<figure>
  <img src="https://github.com/user-attachments/assets/8c0ed9f2-835d-47df-9b07-904e57044730" alt="결과 화면">
  <figcaption>document.write() 문 실행 결과</figcaption>
</figure>  

## 연산자 사용하기

웹 브라우저 화면에 표시할 내용과 변수를 섞어서 나타낼 수도 있다. 이 때 + 연산자를 사용하면 된다.  
여기에서의 + 는 더하기 기호가 아니라 **연결 연산자**이다.

```javascript
let name = prompt("이름을 입력하세요");
document.write(name + "님, 환영합니다.");
```

<figure>
  <img src="https://github.com/user-attachments/assets/b26a134b-c893-4e30-8aad-798ca2af0672" alt="프롬프트 작성 전">
  <img src="https://github.com/user-attachments/assets/b06b131f-4639-470e-8f7a-a5caedc8cf76" alt="화면 표시 결과">
  <figcaption>실행 결과</figcaption>
</figure>

# document.write() 의 단점

`document.write()` 는 브라우저 렌더링 과정을 차단하고 예기치 않은 부작용을 일으킬 수 있어, 최신 자바스크립트 환경에서는 지양하는 구식 메서드이다.

`document.write()` 는 브라우저가 HTML 문서를 위에서부터 읽어 내려가는 렌더링 과정을 멈추게 만들어, 스크립트 실행과 텍스트 삽입이 끝날 때까지 화면 그리기가 중단되므로 페이지 로딩 성능이 크게 저하된다.  
또한, 문서 로딩이 이미 완료된 상태에서 `document.write()` 가 실행되면, 브라우저는 기존에 만들어둔 HTML 구조와 적용된 CSS 및 이벤트 리스너를 모두 메모리에서 지워버리고 빈 화면에 새로운 내용만 출력하게 된다.

이러한 전체 화면 초기화 문제를 피하고 렌더링 성능을 높이기 위해서는 상태 변화에 따라 특정 DOM 요소만 세밀하게 업데이트 하는 방식을 사용한다.  
이러한 방식에는 [`document.getElementBy*()`](/frontend/Javascript/document-getElementBy.md) 또는 [`document.querySelector()`]() 가 사용된다.
