# React_create-react-app

## 개요

npm(노드 패키지 매니저)을 이용하여 facebook이 제공하는 create-react-app을 설치하면 CDN없이 JSX 문법을 사용할 수 있다.

public 폴더는 화면에 랜더링될 html파일을 위치시키고 src 폴더에는 해석될 자바스크립트 파일을 위치시키면 된다.

### note! 

npm start를 이용하여 서버를 구동시키면 package.json에 의해 react-scripts start 라는 명령어가 실행된다. 이후 public에 있는 **index.html**을 찾게 되고 index.html은 명시해주지 않아도 src에 있는 **index.jsx**를 스크립트로서 사용한다.

이후 server의 홈주소로 get요청이 들어오면 react-app은 여러 클래스들을 모두 렌더링하여 3개의 javascript파일과 1개의 html파일로 클라이언트에게 전달한다.



## index.jsx

```jsx
import React from 'react'
import ReactDOM from 'react-dom'
import MenuContainer from './MenuContainer'
import './css/index.css'
//import express from 'express';


ReactDOM.render(
    <MenuContainer/>
    ,
    document.getElementById('container')
);
```

index.jsx에서는 react-dom를 import하여 render 메소드를 실행한다. 형식은 render(jsx에서 지원하는 html, target DOM객체) 이다. jsx에서 지원하는 html에서는 사용자가 정의한 custom tag는 대문자로 그렇지 않은 일반 html tag는 소문자로 시작하는 규칙을 가지고 있다.