# DOM 요소에 접근하기

자바스크립트에서 웹 문서에 있는 이미지나 텍스트, 표 등 특정 요소를 찾아가는 것을 '웹 요소에 접근한다' 라고 한다.  
이렇게 웹 요소에 접근하면 해당 요소의 내용이나 값을 가져오거나 수정할 수 있다.

## getElement+ 함수 사용하기

자바스크립트에서 웹 요소에 접근할 때는 id, class, type, tag 등을 선택할 수 있다.

```javascript
let heading = document.getElementById("heading"); // id 선택자
let bright = document.getElementsByClassName("bright"); // class 선택자
let images = document.getElementsByTagName("img"); // tag 선택자
```

## 반환값

