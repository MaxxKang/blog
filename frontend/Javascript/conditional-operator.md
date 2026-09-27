# 조건 연산자

조건이 복잡하지 않고 `true`와 `false`가 명확할 경우 `if` 문을 사용하지 않고 조건 연산자만으로 체크할 수도 있다.  
조건 연산자 `?`와 `:`를 사용해서 조건과 실행할 명령을 지정하는데, 소스 코드를 간결하게 만들어 주므로 조건을 체크할 때 매우 유용하다.

## 예시

다음과 같이 2개의 값에서 작은 값을 small 변수에 할당할 때 `if..else` 문을 사용하여 작성하였다.

```javascript
if (num1 < num2) {
  small = num1;
} else {
  small = num2;
}
```

이것을 조건 연산자로 작성하면 간단하게 표현할 수 있다.

```javascript
small = (num1 < num2) ? num1: num2;
```

## 예제

사용자가 입력한 숫자가 짝수인지, 홀수인지 구별하는 예제를 만들어 보자.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;   
}

.user-input {
    font-size: 2.4rem;
    border-bottom: 1px solid #3f3f3f;
}
```

```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <title></title>
        <link rel="stylesheet" href="./css/my-even-01.css">
        <script defer src="./js/my-even-01.js"></script>
    </head>
    <body>
        <div class="user-input"></div>
    </body>
</html>
```

```javascript
let userNum = prompt("판별에 사용할 숫자를 입력하세요.");
let userInput = document.querySelector(".user-input");

if (userNum === null) {
    userInput.textContent = "입력이 취소되었습니다. 다시 입력해주십시오.";
} else if (userNum === "") {
        userInput.textContent = "잘못된 입력입니다. 다시 입력해주십시오.";
    } else {
    number = parseInt(userNum);
    (number % 2 === 0) ? userInput.textContent = `${number}는 짝수입니다.`: userInput.textContent = `${number}는 홀수입니다.`;
}
```
