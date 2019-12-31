# Linux

## 기본 문법

### >>, >

- \>> 는 삽입
  - now >> aaa
  - now >> aaa
  - aaa에는 2개의 시간이 저장된다.
- \> 는 수정
  - now > aaa
  - now > aaa
  - aaa에는 최근시간만 저장된다.



## RAID

### Linear RAID

- 디스크를 추가적으로 계속 선형적으로 사용

- 2개이상의 disk



### RAID 0

- striping - 디스크를 돌아가며 사용

- 2개이상의 disk
- 가장 빠름



### RAID 1

- Mirroring - 백업디스크를 사용
- 2개의 disk
- 결함 허용



### RAID 5

- parity 제공
- 공간 효율도 좋음(RAID 0)
- 3개 이상의 disk



### RAID 6

- 2개의 parity
- 4개 이상의 disk



### 디스크

- /dev/(sda, sda1,sda2, sdb, sdc ...) -> 파티션을 나누면 숫자로 나타낸다.
- ls /dev/sd* (리눅스에서 디스크는 sd로 시작하는 이름으로 나누어진다.)
- fdisk /dev/sd* -> sd*의 디스크를 파티셔닝한다.

- df -> disk free, 디스크의 가용공간을 출력한다.

- mdadm 을 이용하여 RAID를 구성할 수 있다.(apt-get mdadm)