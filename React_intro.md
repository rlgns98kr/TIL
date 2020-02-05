# React 실습

## 일반 HTML 문서

직접 다 작성해야 한다.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
</head>
<body>
  <div id="container">
    <div>안녕? 클레오파트라</div>
    <div>세상에서 제일가는 포테이토 칩</div>
    <br>
    <div>안녕?? 클레오파트라!</div>
    <div>세상에서 제일가는 포테이토 칩!</div>
    <br>
    <div>안녕??? 클레오파트라!!</div>
    <div>세상에서 제일가는 포테이토 칩!!</div>
    <br>
  </div>
</body>
</html>
```



## 자바스크립트

함수를 이용하여 호출할 수 있다. 하지만 요소에 접근 및 편집하려면 DOM tree 메써드의 동작구조를 알아야 한다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
</head>
<body>

  <div id="container">
  </div>

  <script>
    function cleo(no){
        let question='?';
        let feel='';
        for(let i=1; i<no; i++)
        {
            question+='?';
            feel+='!';
        }
        return '안녕' + question + ' 클레오파트라' + feel;
    }
    function potato(no){
        let feel='';
        for(let i=1; i<no; i++) feel+='!';
        return '세상에서 제일가는 포테이토 칩' + feel;
    }
    for(let i=1; i<=3; i++)
    {
        let tag1=document.createElement('div');
        tag1.innerHTML=cleo(i);
        let tag2=document.createElement('div');
        tag2.innerHTML=potato(i);
        let br= document.createElement('br');

        let paper=document.getElementById('container');
        paper.appendChild(tag1);
        paper.appendChild(tag2);
        paper.appendChild(br);
    }
    </script>

</body>
</html>
```



## jQuery

자바스크립트보다 DOM접근 및 편집이 수월하다. 또한 태그를 생성할 때에도 텍스트 형식으로 \<tag\>를 주면 된다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
</head>
<body>

    <div id="container">
    </div>

    <script>
        function cleo(no){
            let question='?';
            let feel='';
            for(let i=1; i<no; i++)
            {
                question+='?';
                feel+='!';
            }
            return '<div>' + '안녕' + question + ' 클레오파트라' + feel + '</div>';
        }
        function potato(no){
            let feel='';
            for(let i=1; i<no; i++) feel+='!';
            return '<div>' + '세상에서 제일가는 포테이토 칩' + feel +'</div>';
        }

        let answer=''
        for(i=1; i<=3; i++) answer+=cleo(i)+potato(i)+'<br>';
        $('#container').html(answer);
    </script>

</body>
</html>
```



## 리액트

클래스를 이용하여 출력할 수 있다. react CDN과 babel CDN이 필요하다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.26.0/babel.min.js"></script>
</head>
<body>

    <div id="container">
    </div>

    <script type="text/babel">
        class Cleo extends React.Component {
            render() {
                return (<div>안녕{this.props.question} 클레오파트라{this.props.feel}</div>)
            }
        }
        class Potato extends React.Component {
            render() {
                return (<div>세상에서 제일가는 포테이토 칩{this.props.feel}</div>)
            }
        }

        ReactDOM.render(
            <div>
                <Cleo question="?" feel="" />
                <Potato feel="" />
                <br/>
                <Cleo question="??" feel="!" />
                <Potato feel="!" />
                <br/>
                <Cleo question="???" feel="!!" />
                <Potato feel="!!" />
            </div>
            ,
            document.querySelector('#container')
        );
    </script>

</body>
</html>
```

