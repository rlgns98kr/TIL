# React_this

- javascript에서 기본적으로 this는 일반적으로 global 객체인 window 이다. react에서는 객체를 사용하기 때문에 해당객체가 일반적인 this가 된다.

  ```jsx
  class My extends React.Component{
      a=3;
      render(){
          console.log(this);
          let b=this.a;
          console.log(b);
          return (<tag />);
      }
  }
  ```

  render()에서 this를 찍어보면 React.Component를 상속받은 My가 나온다. 또한 b는 예상하듯이 3이 된다.

  

- setInterval 함수에서 메소드를 ()없이 호출할 경우 this는 windows가 된다.

  ```jsx
  class My extends React.Component{
      a(){
          console.log(this);
      }
      componentDidMount(){
          setInterval(this.a, 1000);
      }
  }
  ```

  javascript에서 일반적인 함수의 호출은 global 객체가 되기 때문이다.

  

- JSX 태그 내에서의 Onclick event의 호출자는 My이다. 하지만 ()를 사용하지 않을 경우 bound하지 않는다.

  ```jsx
  class My extends React.Component{
      a(){
          console.log(this);
      }
      render(){
          return <button onClick={a}>button</button>
      }
  }
  ```

  따라서 button을 클릭할 경우 console에는 undefined가 출력된다.



- 위 문제들은 모두 함수를 호출할 때 this가 제대로 전달되지 않아서 일어나는 문제이다.

  ```javascript
  setInterval(this.a.bind(this), 1000);
  ```

  위처럼 변경해주면 windows.setInterval()을 호출한 호출자는 My.componentDidMount()이기 때문에 this.a의 (a 함수 내에서의)this를 My로 bind 시키는 것이다. 따라서 console에는 My가 출력된다.

  ```jsx
  return <button onClick={a.bind(this)}>button</button>
  ```

  마찬가지로 bind 메소드를 통해 this를 전달해주면 현재 실행문맥인 My.render()에서 My가 전달된다.

  

  ```jsx
  class My extends React.Component{
      a(){
          console.log(this);
      }
      
      render(){
          return <button onClick={a}>button</button>
      }
  }
  ```

  

- html 태그 onClick에서의 this

  ```html
  <script>
      function a(t){
          console.log(t);
          console.log(this);
      }
  </script>
  <button onClick={a(this)}>button</button>
  ```

  react가 아닌 html 태그에서의 this는 자기자신, 즉 node를 반환한다. 따라서 첫번째 출력은 `<button onClick={a.bind(this)}>button</button>` 가 된다. (this를 함수 a의 매개변수 t로 전달하였다.)

  두번째 출력은 windows객체가 된다. (a의 인자로 this를 전달해주었을 뿐이고 a는 일반적인 호출이기 때문에 this windows객체가 된다.)

  ```html
  <button onClick={a.call(this, 'a')}>button</button>
  ```

  ```html
  <button onClick={a.bind(this, 'a')()}>button</button>
  ```

  위와 같이 수정하면 함수 a에서의 this는 this가 되고 t는 a가 된다.(html에서는 onClick이벤트의 property에 함수의 실행을 값으로 넣는다. bind 메소드는 함수의 주소를 반환하기때문에 다음 ()로 실행을 값으로 넣어줘야 동작한다.)
