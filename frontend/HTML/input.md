# `Input` 태그

input 태그는 사용자가 데이터를 입력할 수 있는 폼(`form`) 컨트롤을 생성하는데 사용되는 요소이다.
프론트엔드에서 데이터를 수집해 백엔드로 전달하는 가장 기본적인 창구 역할을 하게 된다.
다음의 다양한 속성값들을 알아본다.

## `type`

입력 컨트롤의 유형을 결정한다. 이 값에 따라 브라우저에 렌더링되는 UI와 기본 동작이 달라지게 된다.
- 기본 텍스트: `text`, `password`, `email`, `number`, `tel`, `url`
- 선택: `radio`(단일 선택), `checkbox`(다중 선택)
- 기타: `data`(날짜 선택기), `file`(파일 업로드), `color`(색상 선택기), `range`(슬라이더)
- 버튼: `submit`(폼 제출), `button`(일반 버튼), `reset`(초기화)

## `name`과 `value`

- `name`: 폼 제출 시 서버로 전달되는 데이터의 키(key) 이름이다. 이 속성이 없으면 해당 입력 필드의 데이터는 서버로 전송되지 않는다.
- `value`: 입력 필드의 초기값을 설정하거나, 라디오/체크박스에서 서버로 전송될 실제 데이터를 지정한다.
- `placeholder`: 입력 필드가 비어 있을 때 사용자에게 입력해야 할 내용의 힌트를 희미하게 텍스트로 보여준다.
- `required`: 폼 제출 시 반드시 값이 채워져 있어야 함을 브라우저에 알리는 검증 속성이다.
- `disabled`: 입력 필드를 비활성화하여 사용자가 값을 변경하거나 클릭할 수 없게 만든다. 이 속성이 있는 필드는 폼 제출 시 데이터가 전송되지 않는다.
- `readonly`: 사용자가 값을 수정할 수는 없지만, 텍스트를 드래그해서 복사할 수 있고 폼 제출 시 데이터도 정상적으로 전송된다.
- `id`/`class`: CSS 스타일링을 적용하거나, 자바스크립트 DOM 조작, 그리고 `<label>` 태그의 `for` 속성과 연결하기 위해 사용한다.

```html
<!-- 사용자 가입 폼 예시 -->
<form action="/signup" method="POST">
    <!-- 
      type="text": 일반 텍스트 입력
      id="username": label 태그와 연결 및 JS 제어용
      name="username": 백엔드에서 이 필드의 값을 찾을 때 사용하는 키 (예: req.body.username)
      placeholder: 사용자가 어떤 값을 넣어야 할지 힌트 제공
      required: 값이 비어있으면 브라우저 단에서 폼 제출을 차단함
    -->
    <label for="username">사용자명:</label>
    <input type="text" id="username" name="username" placeholder="영문, 숫자 조합" required>

    <!-- 
      type="password": 입력한 문자가 마스킹 처리되어 보이지 않음
    -->
    <label for="userpw">비밀번호:</label>
    <input type="password" id="userpw" name="password" required>

    <!-- 
      type="radio": name 속성이 동일한 항목끼리 그룹화되어 단일 선택만 가능
      value="basic" / "premium": 사용자가 화면의 글자('기본형', '프리미엄')를 클릭해도 서버로는 value에 지정된 영어 문자열이 전송됨
    -->
    <p>요금제 선택:</p>
    <label><input type="radio" name="plan" value="basic" checked> 기본형</label>
    <label><input type="radio" name="plan" value="premium"> 프리미엄</label>

    <!-- 
      type="checkbox": 다중 선택 가능
      disabled: 현재 체크할 수 없도록 비활성화 상태로 만듦
    -->
    <label><input type="checkbox" name="newsletter" value="yes"> 뉴스레터 수신 동의</label>
    <label><input type="checkbox" name="event" value="yes" disabled> 이벤트 알림 수신 (준비중)</label>

    <!-- 
      type="submit": form 내부에 있으면 클릭 시 form의 action 경로로 HTTP 요청을 전송함
    -->
    <input type="submit" value="가입하기">
</form>
```

## 백엔드와의 데이터 매핑 관점

위의 폼(form) 코드에서 `method="POST" action="/signup"`으로 설정되어 있으므로, 사용자가 가입하기 버튼을 누르면 실무 API 명세 기준 POST /signup 요청이 발생한다.  
이때 브라우저는 각 `<input>` 태그의 `name`을 키로, 사용자가 입력하거나 선택한 `value`를 값으로 묶어서 HTTP 요청의 Body(Payload)에 담아 백엔드로 전송하게 된다.  
백엔드 개발자는 이 `name` 속성 이름들을 기준으로 Pydantic 모델이나 데이터 수신 로직을 설계해야 한다.
