# mongoDB

몽고디비는 NoSQL(not only sql)이다.



## 설치 및 연결

### 터미널

- mongod 명령어로 db서버시작 전에 C:\data\db 폴더를 생성해야한다.
- mongod 명령어를 입력하여 서버를 시작한다.
- 다른 터미널로 mongo를 입력하여 서버에 접속한다.
- show dbs, show collections 명령어로 db와 collection(테이블)을 볼 수 있다.
- use 데이터베이스이름 명령어로 해당 데이터베이스를 사용한다.
- CRUD 는 db.collection.save({json}),find({where}),update({where},{$set:{json}}),remove({where}) 4가지 명령어로 가능하다.



## Node.js

### CRUD

- npm i mongodb 로 설치

- ```javascript
  const mongo=require('mongodb');
  
  mongo.MongoClient.connect(url, function(err, DB){
      DB.db('데이터베이스이름').collection('콜렉션(테이블)이름').find({}, function(){
          //조회완료!
      })
  })
  ```

- find()대신 save(), updateOne(), deleteOne() 등 몽고디비에서 제공하는 메소드들을 사용가능하다. 형식은 터미널과 동일