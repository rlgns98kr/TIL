# Docker

## 컨테이너

### 외부에서 컨테이너 외부에 명령전달

- -d, -it 옵션으로 컨테이너 실행 후 attach로 해당 컨테이너에 붙는다.

- docker exec 컨테이너ID or 이름 -> 입출력을 공유하며 컨테이너 외부에서 명령을 전달한다. 쉘을 실행하는 명령이면 exit를 해도 컨테이너가 종료되지 않는다.
- ps -ef -> 컨테이너 내에 실행 중인 프로세스

### volume

- host volume 공유
  - -v 옵션을 이용해서 호스트의 볼륨을 공유
  - 호스트의 디렉토리(또는 파일)를  컨테이너의 디렉토리로 마운트
  - docker run -v 호스트디렉토리또는파일의Path:컨테이너디렉토리또는파일의Path ~~ -> 파일이나 디렉토리를 마운트
  - 파일을 수정할 때 gedit이나 vi를 사용하면 파일의 i-node값이 바뀌기 때문에 공유가 취소된다. editor의 옵션에서 i-node값이 변경되지 않도록 설정가능한 경우도 있다.
- 원래 컨테이너에 존재하는 디렉토리에 호스트의 디렉토리를 연결해주면 원래 존재하는 디렉토리의 내용은 사라진다.
- volume container
  - volume container 는 다른 컨테이너들의 data를 다 모아서 호스트의 디렉토리에 연결해주는 역할을 한다.
  - -v 옵션을 적용한 컨테이너들은 모두 볼륨 컨테이너로 이용할 수 있다.
  - --volumes-from 볼륨컨테이너 -> 옵션을 사용하여 volume container에 연결할 수 있다.
  - volume container는 -v 옵션을 통하여 호스트의 디렉토리와 마운트되어있기 때문에 이를 이용하여 호스트에 디렉토리에 접근할 수있다.
- 도커볼륨을 이용하는 방법
  - 도커 자체에서 제공하는 볼륨기능
  - docker volume 명령어 이용



## etc

- !는 이전에 실행했던 명령어