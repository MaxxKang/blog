# form 태그의 버튼 요소에 새로운 이벤트 할당하기

프로그램을 작성하다보면 자주 사용하게 되는 버튼에 새로운 이벤트를 할당하는 방법에 대한 설명이다.  
`addEventListener`를 사용해서 작성하게 된다.

```javascript
document.addEventListener("DOMContentLoaded", function() {
    let resultBtn = document.querySelector(".btn");
    // 매개변수 이름은 e, evt, event 등 자유롭게 지을 수 있다.
    resultBtn.addEventListener("click", function(e) {
        // 폼 전송(새로고침) 기본 이벤트 차단
        e.preventDefault();

        // 차단 이후 실행할 새로운 로직 작성
        console.log("기본 이벤트 차단, 새로운 함수 실행");
    });
});
```

클릭 이벤트가 발생하면 `addEventListener`가 감지하고, 브라우저가 지정된 콜백 함수를 호출하면서 `event`라는 데이터를 첫 번째 인수로 넘겨주는 구조다.

## `function(event)`에서 `event` 매개변수의 기술적 역할과 원리

- 이벤트 객체(Event Object)의 생성: 사용자가 버튼을 클릭하는 순간, 브라우저는 해당 클릭 동작에 대한 모든 상세 정보를 담은 데이터 묶음인 '이벤트 객체'를 생성한다.

- 자동 인수 전달: `addEventListener`는 이벤트가 발생해 함수(`function(event)`)를 실행할 때, 브라우저가 방금 만든 이벤트 객체를 함수의 첫 번째 인수로 자동으로 밀어 넣는다.

- 정보와 제어 기능 포함: 전달받은 `event` 매개변수 안에는 클릭된 대상 요소, 마우스 좌표 등의 데이터뿐만 아니라, 이벤트를 제어할 수 있는 내장 함수(메서드)도 포함되어 있다.

따라서 함수 내부에서 `event.preventDefault()`를 호출하는 것은, 브라우저가 넘겨준 클릭 이벤트에 연결된 기본 동작 대신 지정한 메서드를 호출하라는 명령이 된다.
