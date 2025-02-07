# jQuery 정리

## ✅ 개요

- **jQuery**는 자바스크립트를 더 쉽게 사용할 수 있게 도와주는 **경량 JavaScript 라이브러리**
- DOM 조작, 이벤트 처리, AJAX 통신 등을 간결하게 작성 가능
- HTML, CSS, JS 간의 상호작용을 쉽게 구현할 수 있음

---

## 📦 CDN으로 불러오기

```html
html
복사편집
<!-- 최신 버전 -->
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

```

---

## 🛠️ 기본 문법

### 1. 문서 준비 이벤트

```jsx
javascript
복사편집
$(document).ready(function () {
  // 문서가 로드된 후 실행
});

```

### 2. 선택자

```jsx
javascript
복사편집
$("#id")        // ID 선택
$(".class")     // 클래스 선택
$("div")        // 태그 선택
$("*")          // 전체 선택

```

---

## ✏️ 자주 쓰는 기능 예제

### ✅ 1. HTML/텍스트 조작

```jsx
javascript
복사편집
$("#title").text("새 제목");      // 텍스트 변경
$("#title").html("<b>굵은 글씨</b>"); // HTML 변경

```

### ✅ 2. 값 가져오기/설정

```jsx
javascript
복사편집
$("#input").val();          // 입력값 가져오기
$("#input").val("입력값");  // 입력값 설정

```

### ✅ 3. CSS 조작

```jsx
javascript
복사편집
$(".box").css("color", "red");        // 스타일 변경
$(".box").addClass("active");         // 클래스 추가
$(".box").removeClass("active");      // 클래스 제거

```

### ✅ 4. 이벤트 처리

```jsx
javascript
복사편집
$("#btn").click(function () {
  alert("버튼 클릭됨!");
});

$(".item").hover(function () {
  $(this).css("background-color", "yellow");
});

```

### ✅ 5. 반복문

```jsx
javascript
복사편집
$(".item").each(function (index, element) {
  console.log(index, $(element).text());
});

```

---

## 🔄 AJAX 통신 (비동기 요청)

```jsx
javascript
복사편집
$.ajax({
  url: "/api/data",
  type: "GET",
  success: function (response) {
    console.log("성공", response);
  },
  error: function (xhr, status, error) {
    console.log("실패", error);
  }
});

```

또는 축약형:

```jsx
javascript
복사편집
$.get("/api/data", function (res) {
  console.log(res);
});

$.post("/api/save", { name: "홍길동" }, function (res) {
  alert("저장됨!");
});

```

## ✅ 기본 선택자 종류 정리

| 구분 | 종류 | 사용법 | 설명 |
| --- | --- | --- | --- |
| **직접 선택자** | 전체 선택자 | `$(" * ")` | 문서의 **모든 요소**를 선택 |
|  | 아이디 선택자 | `$("#id명")` | 해당 **아이디(id)**를 가진 요소 선택 |
|  | 클래스 선택자 | `$(".class명")` | 해당 **클래스(class)**를 가진 요소 선택 |
|  | 태그 선택자 | `$("태그명")` | 해당 **태그 이름**을 가진 요소 선택 |
|  | 그룹 선택자 | `$("선택자1, 선택자2, ...")` | 여러 요소를 **동시에 선택** (쉼표 사용) |
| **인접 관계 선택자** | 부모 요소 선택자 | `$(자손요소).parent()` | 선택된 요소의 **직속 부모** 요소 선택 |
|  | 전체 부모 요소 선택자 | `$(자손요소).parents()` | 선택된 요소의 **모든 상위** 요소 선택 |
|  | 조상 요소 중 특정 요소만 선택 | `$(자손요소).parents("태그")` | 조상 요소 중 해당 태그에 **해당하는 요소만 선택** |
|  | 자식 요소 선택자 | `$(부모요소).children()` | 부모 요소의 **직속 자식** 요소 선택 |
|  | 자식 요소 중 특정 요소만 선택 | `$(부모요소).children("태그")` | 자식 요소 중 해당 태그에 **해당하는 요소만 선택** |
|  | 이전(이전 형제 요소) 선택자 | `$(요소).prev()` | 선택한 요소의 **이전 형제 요소 1개** 선택 |
|  | 이전 형제 요소들 모두 선택 | `$(요소).prevAll()` | 선택한 요소의 **이전 형제 요소 전체** 선택 |
|  | 기준 요소 이전 요소들 중 특정 요소까지 선택 | `$(요소).prevUntil("선택자")` | **조건을 만족할 때까지의 이전 형제 요소** 선택 |
|  | 다음(다음 형제 요소) 선택자 | `$(요소).next()` | 선택한 요소의 **다음 형제 요소 1개** 선택 |
|  | 다음 형제 요소들 모두 선택 | `$(요소).nextAll()` | 선택한 요소의 **다음 형제 요소 전체** 선택 |