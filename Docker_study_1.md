# Docker란?
- 2013년 3월에 출시한 오픈소스 컨테이너 프로젝트

- Go 언어로 작성

- 서버를 구축함에 있어서 클라우드 환경으로 넘어가게 되고, 그 과정에서 Immutable Infrastructure라는 패러다임이 나옴.

  **-Immutable Infrastructure**
  
  : 서비스 운영 환경을 이미지로 생성하여 관리하기 때문에 관리와 배포가 체계적이고 편리하다.

  : 이미지 하나로 서버를 계속 찍어낼 수 있어서 서비스 확장이 가능하다.

  : 개발자의 PC나 테스트 서버에서 이미지를 실행하기만 하면 서비스 운영 환경과 동일하기 때문에 테스트가 쉽다.

  : 운영체제와 서비스 운영 환경을 분리하여 가볍고 어디서든 실행 가능하다.

- Docker는 이러한 Immutable Infrastructure를 구현한 프로젝트다.

- Docker는 크게 '이미지'와 '컨테이너'라는 개념이 존재한다.


# Docker의 기본 명령어들
1. search 명령으로 이미지를 검색하기
```sh
$ docker search
````

2. pull 명령으로 이미지 받기
```sh
$ docker pull ubuntu:latest
````
- docker pull <이미지 이름>:<태그> 형식이다.
 
- latest를 설정하면 최신 버전을 받는다.

3. images 명령으로 이미지 목록 출력하기
```sh
$ docker images
````

4. run 명령으로 컨테이너 생성하기
```sh
$ docker run -i -t --name hello ubuntu /bin/bash
````
- docker run <옵션><이미지 이름><실행할 파일>

- -i -t 옵션을 쓰면 실행된 Bash 셸에 입출력을 할 수 있다.

- --name 옵션으로 컨테이너의 이름을 지정할 수 있다. 지정하지 않으면 Docker가 알아서 자동으로 생성한다.

5. ps 명령으로 컨테이너 목록 확인하기
```sh
$ docker ps -a
````
- -a 옵션을 쓰면 정지된 컨테이너까지 모두 출력한다.
 
6. start 명령으로 컨테이너 시작하기
```sh
$ docker start hello
````
- docker start <컨테이너 이름>
 
7. restart 명령으로 컨테이너 재시작하기
```sh
$ docker restart hello
````

8. attach 명령으로 컨테이너에 접속하기
```sh
$ docker attach hello
````

9. exec 명령으로 외부에서 컨테이너 안의 명령 실행하기
```sh
$ docker exec hello echo "Hello World"
````
- docker exec <컨테이너 이름><명령><매개 변수> 형식이다.

- 컨테이너가 실행되고 있는 상태에서만 사용할 수 있다.

10. stop 명령으로 컨테이너 정지하기
```sh
$ docker stop hello
````
- docker stop <컨테이너 이름> 형식이다.
 
11. rm 명령으로 컨테이너 삭제하기
```sh
$ docker rm hello
````
- docker rm <컨테이너 이름> 형식이다.
 
12. rmi 명령으로 이미지 삭제하기
```sh
$ docker rmi ubuntu:latest
```` 
- docker rmi <이미지 이름>:<태그> 형식이다.

- 이미지 이름만 쓰면 태그는 다르지만 ubuntu 이름을 가진 모든 이미지가 다 삭제된다.
