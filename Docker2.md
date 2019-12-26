# Docker

## Dockerfile

### 개요

- Dockerfile이 위치한 곳이 빌드 컨텍스트

- 명령어의 개수를 줄인다.(&& 파이프라인으로 명령어들을 묶어준다 -> 명령어의 개수를 줄인다)
- 명령어의 개수를 줄이면 이미지의 크기가 줄어든다.

- 사용자의 입력을 필요로 하면 오류로 취급

### 명령어

- RUN -> 리눅스 명령어를 실행한다.
- FROM -> 베이스 이미지를 불러온다.
- ADD, COPY -> host의 파일 또는 디렉토리를 이미지 내부로 복사
  - COPY -> host의 로컬 파일만 복사 가능하다
  - ADD -> 외부 URL, tar 파일도 복사가 가능하다(tar 파일인 경우 압축을 해제하여 복사)
- WORKDIR -> cd와 동일, 명령어를 실행할 위치를 지정
- \[ \] 대괄호 형식의 인자 -> JSON 배열 형식, 쉘을 실행하지 않음을 의미한다.
  - 일반 인자 -> /bin/sh -c command 형식으로 실행

- EXPOSE -> 이미지에서 노출할 포트를 설정
- CMD -> 컨테이너가 실행될 때 마다 실행할 명령어 (반드시 한번만 사용이 가능하다)
- ENV -> 환경변수 설정



## 컨테이너

### 명령어

- run -P -> 호스트의 빈 포트를 컨테이너의 EXPOSE된 포트로 매핑

- -p 호스트포트:컨테이너포트 -> 포트포워딩
- docker container rm -> 삭제
- docker container cp HOST_FILE_PATH CONTAINER_ID_or_NAME:CONTAINER_FILE_PATH
- 컨테이너에 있는 파일을 불러오려면? 호스트의 파일을 밀어넣으려면?
  - docker container cp 컨테이너id:path 호스트path -> 호스트로 복사
  - docker container cp 호스트path 컨테이너id:path -> 컨테이너로 복사
- docker stats -> 현재 실행중인 도커의 자원디스플레이
- docker commit -> 컨테이너를 다시 이미지로
- docker container/image prune -> garbage 제거

### 스크립트

- 쉘스크립트를 사용하여 여러 명령들을 하나로 실행할 수 있다.



# QUIZ

## 1

- ./../bin/.a.sh

  . 현재 디렉토리

  .. 상위 디렉토리

  .a 숨김파일

  . 확장자 구분자