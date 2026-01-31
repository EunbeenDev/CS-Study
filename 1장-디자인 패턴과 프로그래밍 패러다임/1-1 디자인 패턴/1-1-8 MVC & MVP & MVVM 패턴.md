
## 1-1-8. MVC & MVP & MVVM 패턴

### 1. MVC (Model-View-Controller)

#### 개념

* Model: 데이터와 비즈니스 로직
* View: UI 표현
* Controller: 입력 처리 및 흐름 제어

```scss
User → Controller → Model
                ↓
              View
```

#### 특징

* 관심사 분리
* 웹 서버 구조에 적합

#### 단점

* Controller 비대화 가능

---

### 2. MVP (Model-View-Presenter)

#### 개념

* View와 Model 사이를 Presenter가 완전히 중재
* View는 **수동적(Passive View)**

```scss
View ↔ Presenter ↔ Model
```

#### 특징

* 테스트 용이
* View와 로직 완전 분리

---

### 3. MVVM (Model-View-ViewModel)

#### 개념

* ViewModel이 View 상태를 관리
* **데이터 바인딩** 기반

```scss
View ↔ ViewModel ↔ Model
```

#### 특징

* View와 로직 결합 최소화
* 상태 중심 UI 설계

---

### 4. MVC / MVP / MVVM 비교

| 구분      | MVC        | MVP        | MVVM               |
| ------- | ---------- | ---------- | ------------------ |
| 중재자     | Controller | Presenter  | ViewModel          |
| View 역할 | 능동         | 수동         | 상태 반영              |
| 테스트     | 보통         | 쉬움         | 쉬움                 |
| 사용 예    | Spring MVC | Android 초기 | Android / Frontend |

