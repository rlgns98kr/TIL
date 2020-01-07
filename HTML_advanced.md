# HTML

## 태그(body)

### \<button\>

- submit, reset, button
  - submit은 전달
  - reset은 내용 지우기
  - button은 a태그 안에 내용으로 쓰여지면 댐
- button 옵션은 a태그나 자바스크립트를 이용해서 특정 기능 정의가능
- \<button> 버튼 안에 들어갈 내용\</button>

### \<textarea>

- rows, cols 로 값 설정

- name으로 값 지정

### \<select\>, \<option\>

- name, size, multiple
  - size는 화면에 표시되는 선택항목의 개수, multiple은 다중선택가능
- \<option value="전달값\> 을 추가하면 드롭다운 리스트형식으로 전달값들중 선택할 수 있다.

### \<label\>

- input태그 뒤에 위치함으로써 텍스트라벨을 표시한다.
- \<label for="input id"\>내용</label\>

### \<fieldset>, \<legend\>

- 입력필드 그룹핑 및 라벨 표시
- fieldset으로 묶은 곳은 그룹핑되서 출력된다. legend를 사용하면 그룹핑에 라벨을 표시할 수 있다.

### \<input\>

- 고급 입력 형식을 사용할 수 있다.
- type에 email, URL, tel, search, button, image, hidden, number 등 다양한 형식 지정가능
  - color는 색상코드표
  - number type에 step으로 속성을 주면 증감버튼을 제공한다.
  - range type은 스크롤 바를 제공한다.
- placeholder에 서식예시를 나타낼 수 있다.
- HTML5
  - required, autofocus, disabled 속성을 통하여 사용자에게 필수 입력 항목을 지정할 수 있다.
  - list 속성으로 입력가능한 값들을 제공 할수있다.
  - autocomplete="on|off" 로 자동완성기능을 끄고 킬 수 있다.




## 태그(head)

### \<title\>

- 제목

### \<base\>

- 베이스 폴더지정
- 한번만 사용할 수 있고 지정하지 않으면 웹 서버를 설치할 때 확인했던 기본 디렉터리가 베이스 폴더

### \<meta\>

- UTF-8 등 문자인코딩 방식, 작성자 정보, 문서 내용 설명 등



## CSS3

### 형식

- 선택자(태그단위) {스타일속성1:값; 스타일속성2:값; ...}

### \<style\>

- head에 \<style\> 태그를 붙여 CSS형식대로 지정해준다.
- head에 \<style\> 태그를 붙여 **@import url("CSS 파일의 URL"); or @import url "CSS 파일의 URL";** 을 이용하여 외부 파일을 불러올 수 있다.

### \<link\>

- head에 \<link href="CSS 파일의 URL"\>
- type 이나 ref로 파일종류 지정가능

### @import

- head에 @import url(CSS 파일의 URL);

### 인라인

- style 속성으로 적용가능 대신 해당 태그에만 적용

