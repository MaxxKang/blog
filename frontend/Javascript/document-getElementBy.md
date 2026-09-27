# DOM 요소에 접근하기

자바스크립트에서 웹 문서에 있는 이미지나 텍스트, 표 등 특정 요소를 찾아가는 것을 '웹 요소에 접근한다' 라고 한다.  
이렇게 웹 요소에 접근하면 해당 요소의 내용이나 값을 가져오거나 수정할 수 있다.

## getElement* 함수 사용하기

자바스크립트에서 웹 요소에 접근할 때는 id, class, type, tag 등을 선택할 수 있다.

```javascript
let heading = document.getElementById("heading"); // id 선택자
let bright = document.getElementsByClassName("bright"); // class 선택자
let images = document.getElementsByTagName("img"); // tag 선택자
```

## 반환값

사용하는 함수에 따라 자바스크립트가 요소를 찾아 반환하는 결과물의 형태가 다르다. 이 반환값의 형태를 정확히 구분해야 요소를 올바르게 조작할 수 있다.

* **단일 요소 반환 (`getElementById`):**
  HTML 문서에서 `id`는 유일해야 하므로, 조건에 맞는 **단 하나의 HTML 요소 객체**를 반환한다. 찾으려는 `id`가 문서에 존재하지 않으면 `null`을 반환한다. 반환값이 단일 요소이므로 바로 속성에 접근해 조작할 수 있다.

* **컬렉션 반환 (`getElementsByClassName`, `getElementsByTagName`):**
  `class`나 `tag`는 문서 안에 여러 개가 존재할 수 있으므로, 조건에 맞는 모든 요소를 찾아서 **HTMLCollection**이라는 유사 배열 형태로 반환한다. 문서에 해당 요소가 단 1개만 존재하더라도 반드시 배열 형태의 묶음으로 반환된다. 

컬렉션으로 반환된 요소들을 조작하려면 배열처럼 인덱스(`[0]`, `[1]`, ...)를 지정해서 특정 요소에 접근해야 한다.

```javascript
// 1. 단일 요소 반환 (getElementById)
let heading = document.getElementById("heading");
// 요소가 1개뿐이므로 인덱스 없이 바로 textContent 속성에 접근하여 내부 텍스트를 변경한다.
heading.textContent = "제목이 변경되었습니다.";

// 2. 컬렉션 반환 (getElementsByClassName)
let brightElements = document.getElementsByClassName("bright");
// 여러 요소가 묶인 HTMLCollection이 반환되므로, 
// 다음과 같이 대괄호와 인덱스 숫자를 사용해 정확히 몇 번째 요소를 조작할지 지정해야 한다.
brightElements[0].style.color = "red";  // 문서에서 첫 번째로 발견된 bright 클래스 요소의 글자색을 변경한다.
brightElements[1].style.color = "blue"; // 문서에서 두 번째로 발견된 bright 클래스 요소의 글자색을 변경한다.
```

## 예시

```html
<button id="text-change">변경 전</button>
```

```javascript
let change = document.getElementById("text-change");
change.addEventListener("click", function() {
  if (change.innerText === "변경 전") {
    change.innerText = "변경 후";
  } else {
    change.innerText = "변경 전";
  }
});
```

<style>
  #text-change {
    padding: 2px 4px;
    border: 1px solid #3f3f3f;
    border-radius: 4px;
</style>

<button id="text-change">변경 전</button>

<script>
  let change = document.getElementById("text-change");
  change.addEventListener("click", function() {
    // 위에서 설명한 textContent 속성을 사용하여 값을 비교하고 변경합니다.
    if (change.textContent === "변경 전") {
      change.textContent = "변경 후";
    } else {
      change.textContent = "변경 전";
    }
  });
</script>
