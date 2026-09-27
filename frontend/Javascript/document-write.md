# document.write() 사용법

자바스크립트의 `document` 객체는 웹 브라우저에 로드된 웹 페이지 그 자체(HTML 문서)를 의미하는 전역 객체이다.  
`document.write()` 문은 웹 문서(document)에서 괄호 안의 내용을 표시하는 명령문이다.

`document.write()` 의 괄호 안에는 실제 웹 브라우저 화면에 표시할 내용이나 어떤 결과값이 저장된 변수를 넣을 수도 있다.  
괄호 안에서 큰 따옴표나 작은 따옴표 사이에 입력한 내용이 웹 브라우저 화면에 그대로 표시된다.  
물론 HTML 태그도 함께 사용할 수 있다.  

```javascript
<script>
  document.write("<h1>안녕하세요</h1>")
</script>
```

<figure>
  <img src="https://github.com/user-attachments/assets/8c0ed9f2-835d-47df-9b07-904e57044730" alt="결과 화면">
  <figcation>document.write() 문 실행 결과</figcation>
</figure>

웹 브라우저 화면에 표시할 내용과 변수를 섞어서 나타낼 수도 있다. 이 때 + 연산자를 사용하면 된다.  
여기에서의 + 는 더하기 기호가 아니라 **연결 연산자**이다.

```javascript
<script>
  let name= prompt("이름을 입력하세요");
  document.write(name + "님, 환영합니다.");
</script>
```

<figure>
  <img src="https://github.com/user-attachments/assets/b26a134b-c893-4e30-8aad-798ca2af0672" alt="프롬프트 작성 전">
  <img src="https://github.com/user-attachments/assets/b06b131f-4639-470e-8f7a-a5caedc8cf76" alt="화면 표시 결과">
  <figcaption>실행 결과</figcaption>
</figure>
