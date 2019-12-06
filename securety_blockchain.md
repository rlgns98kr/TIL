블록체인 - 변경은 불가능하지만 공개는 가능한 데이터

비도 - 암호화 강도(128은 2^128 만큼 시도해야 풀 수 있는 암호), 키 길이에 의존한다.

암호화를 할 때 - 암호화 알고리즘을 알고 있어도 KEY를 찾지 못한다면 암호를 도출할 수 없어야한다.

KEY - 접근통제(접근기록, 허용된 사용자들에게 인가)

대칭키 - 암호화와 복호화에 동일한 KEY를 사용한다.(관용 암호화 방식)

비대칭키 - 이산대수의 원리, 소인수분해의 어려움(공개키를 외부에 공개)



기밀성 보장

(송신측) 수신자의 공개키로 암호화하고

(수신측) 수신자의 개인키로 복호화

인증, 서명, 부인방지

(송신측) 송신자의 개인키로 암호화

(수신측) 송신자의 공개키로 복호화



무결성

- 권한있는 사용자가 변경시킨 최종적인 상태가 유지된다.(권한없는 사용자의 접근통제)

- 해쉬값을 사용해서 무결성보장(1비트라도 바뀌면 해쉬값이 바뀐다.)



비대칭키는 키를 교환하는 용도로도 쓰인다.

1. 키를 공개키로 암호화한 것을 개인키로 암호화한 것을 전달

2. 전달 받은 것을 공개키로 복호화한 것을 개인키로 복호화하여 키를 얻음



블록체인

- 도메인, 공공재, 변경은 불가능하지만 공개는 가능한 데이터 등 아이디어



중앙화된 네트워크가 기존의 방식이었다면 Public, Private 등 분산형 네트워크

비트코인은 Public, IBM의 하이퍼렛져는 Private

Public의 관리자는 모든 거래 참여자

컨소시엄 블록체인 -> 반 중앙형 블록체인, 미리 선정된 노드들이 권한을 가지며, 노드간 동의가 일어나야 거래가 생성, 확장이 용이하며 거래속도가 빠름.



# 블록체인의 기술(Stack)



## 구현 스택 분류

인프라스트럭쳐 단 -네트워크 단 - 프로토콜 단 - 서비스와 부가적인 컴포넌트 단 - 어플리케이션 단

​                          코어 기술                                          서비스 기획자, 어플리케이션 개발자



daap - 탈 중앙화 어플리케이션



## 블록

- 유효(서명, 검증)한 트랜잭션 정보의 묶음

- 비트코인 블록 하나에는 평균 1,400개의 트랜잭션 개수, 1.14MB
- 높이 : 0번 블록 이후 블록 추가 시 1씩 증가
- 깊이 : ??



### 1. 헤더(80byte)

- 버전
- 이전 블록 헤더 해쉬 *체인을 보증한다.
- 머클 루트 - 머클트리의 루트에 대한 해쉬
- 타임스탬프
- 난이도 목표 - block 생성에 걸리는 시간을 bit값으로 조정
- 난스 - 값을 변경시키며 헤더로 해쉬를 추출할 때 난이도 목표에 맞는 해쉬가 추출되도록 변경가능한 값

### 2. 바디

- 트랜잭션 카운트
- 코인베이스(채굴자의 계정) 트랜잭션 - 비트코인
- 트랜잭션

### 3. 해시

- 블록의 식별자
- 헤더 정보를 SHA256 해시 함수로 계산한 32바이트 길이의 숫자

### 4. 트랜잭션

- 비트코인의 거래 내역
- 거래 후 남은 잔액이 비트코인이므로, 비트코인의 거래 내역을 기록한 트랜잭션이 곧 비트코인
- 비트코인은 100퍼센트 확인 이전에는 사용할 수 없도록 제한(더 긴 블록의 생성자가 코인을 얻음)



궁금한 점

- 트랜잭션의 해시값을 적절히 조정하여 최종적으로 블록 해시값을 일치하게 할 수 있는가?
- SHA-256 알고리즘은 어떻게 동작하는가?



### 5. 미사용출력=UTXO

- 암호화폐를 저장하는 자료
- 트랜잭션에서 나의 미사용출력만 찾아서 모아놓는 다면 자산이 댐

- 다른 사람에게 일정량의 암호화폐를 받을 때 생성
- 자산을 기준으로 broadcast - 지연없고 Rollback 없음



### 6. 암호화 알고리즘

- 시저암호
- 대칭키
- 비대칭키



### 7. 해시와 암호화 통신

- 암호화 통신은 양방향성이지만 해시는 해시값을 추출할 수만 있고 
- 해시값을 이용하여 제시하는 수보다 작은 수를 찾는 난이도만족 방법과 주어진 앞의 0의 개수를 찾는 난이도만족 방법이 있다.
- SHA-256 -> 256비트(32바이트)(4bit짜리 16진수 64개) 길이의 해시값을 생성
- RIPEMD-160 -> 160비트 길이의 해시값을 생성



### 8. nonce와 difficulty

- 출력된 해쉬값이 가지는 0배열(앞의 0)의 개수를 difficulty로 정의한다.
- difficulty를 조정하여 10분당 1~2개의 블록이 생성되는 것을 보장한다.
- nonce를 조절하여 difficulty를 만족하는 해시값을 찾는다.



### 9. 머클트리

- 1979년 개발된 이진 해시트리 구조
- 머클루트만으로 트랜잭션의 유효성을 보장할 수 있다.
- n개의 데이터 중 문제있는 데이터를 검증할 때 logn번의 검사를 통하여 찾을 수 있다.



### 10. 합의

- 모든 참여자의 원장이 일치하는지 확인하는 메커니즘
- 중앙 집중형의 합의방식은 의도 또는 악의적인 사용자의 공격을 통해 기록 조작이 가능

- 분산 환경에서의 합의는 비잔틴 장군 문제 해결(?)
- 거래 및 거래 실행 순서에 대한 동의
- 새로운 코인이 왔을 때 100 컨펌후에 사용가능하게 함.
- 최종성이 결여되어있다.



### 11. javaScript를 이용한 block 객체 구현

```javascript
	function Blockchain(){
		this.difficulty ='0000';
		this.chain =[];
		this.pendingTransactions=[];
	}
	
	Blockchain.prototype.createNewBlock = function(previousBlockHash, nonce, hash){
		const newBlock ={
				index : this.chain.length +1,
				timestamp : Date.now(),
				transaction : this.pendingTransactions,
				nonce : nonce,
				hash : hash,
				previouseBlockHash : previousBlockHash
		};
		
		this.pendingTransactions = [];
		this.chain.push(newBlock);
		
		return newBlock;
	}
	Blockchain.prototype.getLastBlock = function(){
		return this.chain[this.chain.length-1];
	}
	
	
	Blockchain.prototype.createNewTransaction = function(sender, recipient, amount){
		const newTransaction = {
				sender : sender,
				recipient : recipient,
				amount : amount
		}
		
		this.pendingTransactions.push(newTransaction);
		
		return;
	}

	const sha256 =require('sha256');
	
	Blockchain.prototype.hashBlock=function(previousBlockHash, currentBlockData, nonce){
		const data = previousBlockHash + nonce.toString() + JSON.stringify(currentBlockData);
		const hash = sha256(data);
		
		return hash;
	}

	Blockchain.prototype.pow = function(previousBlockHash, currentBlockData){
		let nonce = 0;
		let hash= this.hashBlock(previousBlockHash, currentBlockData, nonce);
		while(hash.substring(0,4) != this.difficulty)
		{
			nonce++;
			hash =this.hashBlock(previousBlockHash, currentBlockData, nonce);
		}
		return nonce;
	}
```



# 마크업

## 예시

- <태그 attribue='값'>내용</태그>