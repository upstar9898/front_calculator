아래는 제공된 계산기 코드를 기반으로 작성한 **README.md 예시**입니다.
(학습용 프로젝트라는 점을 고려하여 구조, 개념 설명, 코드 동작 원리까지 포함해 비교적 자세히 작성했습니다.)

---

# 📟 jQuery + Bootstrap 계산기

간단한 **웹 계산기(Calculator)** 프로젝트입니다.
HTML, CSS, JavaScript, jQuery, Bootstrap을 이용하여 **기본 사칙연산(+ − × ÷)** 기능을 구현한 예제입니다.

이 프로젝트는 **웹 프론트엔드 학습용 예제**로 다음 내용을 연습하기 위해 제작되었습니다.

- Bootstrap Grid 레이아웃
- jQuery 이벤트 처리
- JavaScript 변수 관리
- DOM 제어
- 간단한 계산 로직 구현

---

# 1. 프로젝트 화면

### 계산기 UI 특징

- Bootstrap Grid 기반 버튼 배치
- 입력값 표시 디스플레이
- 경고 메시지(Alert)
- 반응형 UI

구성 요소

```
┌─────────────────┐
│      계산기      │
│  ─────────────  │
│   입력 / 결과창  │
│  ─────────────  │
│ 7  8  9   /     │
│ 4  5  6   *     │
│ 1  2  3   -     │
│ 0  C  =   +     │
└─────────────────┘
```

---

# 2. 사용 기술 (Tech Stack)

| 기술        | 설명                     |
| ----------- | ------------------------ |
| HTML5       | 웹 페이지 구조           |
| CSS3        | 스타일 및 레이아웃       |
| JavaScript  | 계산 로직 구현           |
| jQuery      | DOM 제어 및 이벤트 처리  |
| Bootstrap 5 | UI 스타일 및 Grid 시스템 |

CDN 사용

```
Bootstrap 5.3.3
jQuery 3.7.1
```

---

# 3. 프로젝트 구조

```
calculator-project
│
├── index.html
└── README.md
```

모든 코드가 **단일 HTML 파일 안에 포함된 구조**입니다.

구성

```
HTML  → 화면 구조
CSS   → 계산기 스타일
JS    → 계산 기능 구현
```

---

# 4. 핵심 기능

## 1️⃣ 숫자 입력

숫자 버튼을 누르면 입력값이 화면에 표시됩니다.

예

```
7 → 78 → 789
```

구현 방식

```javascript
$(".number").click(function () {
  let num = $(this).data("num");
  currentInput += num;
  $("#display").val(currentInput);
});
```

설명

1. 버튼 클릭 이벤트 발생
2. `data-num` 속성 값 가져오기
3. 기존 입력값 뒤에 숫자 추가
4. 화면에 출력

---

# 2️⃣ 연산자 입력

연산자 버튼을 누르면

1️⃣ 첫 번째 숫자를 저장
2️⃣ 연산자를 저장
3️⃣ 두 번째 숫자 입력 준비

```javascript
$(".operator").click(function () {
  firstNumber = currentInput;
  operator = $(this).data("op");
  currentInput = "";
});
```

예

```
입력 : 7
연산 : +
입력 : 3
```

저장 상태

```
firstNumber = "7"
operator = "+"
secondNumber = "3"
```

---

# 3️⃣ 계산 수행 (=)

equal 버튼을 누르면 계산이 수행됩니다.

```javascript
let num1 = parseFloat(firstNumber);
let num2 = parseFloat(secondNumber);
```

문자열을 **숫자로 변환** 후 계산합니다.

연산 처리

```javascript
if (operator == "+") {
  result = num1 + num2;
}
```

지원 연산

```
+
-
*
/
```

---

# 4️⃣ 초기화 (C 버튼)

모든 입력값을 초기화합니다.

```javascript
$("#clear").click(function () {
  $("#display").val("");

  firstNumber = "";
  secondNumber = "";
  operator = "";
  currentInput = "";
});
```

초기화되는 값

```
firstNumber
secondNumber
operator
currentInput
display
```

---

# 5️⃣ 예외 처리 (Alert 메시지)

잘못된 입력이 발생하면 경고 메시지를 출력합니다.

예

```
숫자를 입력하세요!
두번째 숫자를 입력하세요!
```

코드

```javascript
function showAlert(msg) {
  let output = `<div class="alert alert-danger">
                <strong>Fail!</strong>${msg}
                </div>`;

  $(".alertArea").html(output);
  $(".alertArea").show(1000);
}
```

Bootstrap의 **Alert 컴포넌트**를 사용합니다.

---

# 5. 주요 변수 설명

| 변수         | 역할              |
| ------------ | ----------------- |
| firstNumber  | 첫 번째 입력값    |
| secondNumber | 두 번째 입력값    |
| operator     | 연산자            |
| currentInput | 현재 입력 중인 값 |

예

```
입력 과정

7  → currentInput = "7"

+  → firstNumber = "7"
      operator = "+"

3  → currentInput = "3"

=  → secondNumber = "3"
```

---

# 6. Bootstrap Grid 사용

버튼 배치는 **Bootstrap Grid System**으로 구성됩니다.

예

```html
<div class="row">
  <div class="col-3">
    <button>7</button>
  </div>
</div>
```

설명

```
row     → 행
col-3   → 12칸 중 3칸 사용
```

따라서

```
12 / 3 = 한 줄에 4개 버튼
```

---

# 7. CSS 디자인

계산기 스타일

```css
.calculator {
  width: 320px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 15px;
  background-color: white;
}
```

특징

```
둥근 모서리
중앙 정렬
그림자 효과
```

---

# 8. 실행 방법

1️⃣ 프로젝트 다운로드

```
git clone 프로젝트주소
```

또는 파일 다운로드

---

2️⃣ HTML 실행

```
index.html
```

브라우저에서 열기

---

3️⃣ 바로 실행

```
더블 클릭
```

또는

```
Live Server
```

---

# 9. 향후 개선 가능 기능

추가하면 좋은 기능

### 기능 개선

- 소수점 계산
- 연속 계산
- 키보드 입력 지원
- 계산 기록

### UI 개선

- 다크모드
- 애니메이션
- 모바일 최적화

---

# 10. 학습 포인트

이 프로젝트에서 학습할 수 있는 핵심 내용

### 프론트엔드

- DOM 제어
- 이벤트 처리
- UI 구성

### JavaScript

- 문자열 누적 입력
- 상태 변수 관리
- 조건문 기반 계산 로직

### jQuery

- `$(selector)`
- `.click()`
- `.val()`
- `.data()`

---

# 11. 라이선스

학습용 예제 프로젝트입니다.

자유롭게 수정 및 활용 가능합니다.

---

원하시면 **이 코드를 기준으로 학생 교육용으로 더 좋은 README (예: 수업용, 실습 문제 포함)**도 만들어 드리겠습니다.
또는 **GitHub에 올리기 좋은 수준의 README (스크린샷, 기능 GIF 포함)**도 만들어 드릴 수 있습니다.
