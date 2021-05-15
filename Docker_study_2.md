# Dockerfile
 - Dockerfile은 Docker 이미지 설정 파일이다. 
 
 - Dockerfile에 설정된 내용대로 이미지를 생성한다.
 
# Dockerfile 관련 명령어들
**1. build 명령어로 이미지 생성하기**
```sh
~/example$ docker build --tag hello:0.1
````

- docker build <옵션> <Dockerfile 경로> 형식이다.

- --tag 옵션으로 이미지 이름과 태그를 설정할 수 있다.

**2. .dockerignore**

- 컨텍스트(context) = Dockerfile과 같은 디렉터리에 들어있는 모든 파일

- 이런 컨텍스트에서 파일이나 디렉터리를 제외하고 싶을 때 .dockerignore 파일을 사용한다.

**3. FROM**
```sh
FROM ubuntu:14.04
````

- FROM <이미지>:<태그>의 형식이다.

- FROM은 항상 설정해야 하고 맨 처음에 와야 한다.

- FROM을 여러개 설정 할 수 있고 그 개수만큼 이미지가 생성된다.

**4. MAINTAINER**

- MAINTAINER <작성자 정보> 형식이다.

**5. RUN**
```sh
RUN apt-get install -y nginx
````
- RUN <명령> 형식이다. 

**6. CMD**
```sh
CMD touch /abc/hello/hello.txt
````
- CMD <명령> 형식이다.

- 컨테이너가 시작되었을 때 스크립트 혹은 명령을 실행한다.

- Dockerfile에서 한번만 사용할 수 있다.

**7. ENTRYPOINT**
```sh
ENTRYPOINT touch /abc/hello/hello.txt
````
- ENTRYPOINT <명령> 형식이다.

- 컨테이너가 시작되었을 때 스크립트 혹은 명령을 실행한다.

- Dockerfile에서 한번만 사용할 수 있다.

**8. EXPOSE**
```sh
EXPOSE 80 443
````
- EXPOSE <포트 번호> 형식이다.

- EXPOSE 하나로 포트 번호를 두 개 이상 설정할 수 있다.

**9. ENV**
```sh
ENV GOPATH /go
````
- ENV <환경 변수> <값> 형식이다.

**10. ADD**
```sh
ADD hello-dir /hello-dir
````
- ADD <복사할 파일 경로> <이미지에서 파일이 위치할 경로> 형식이다.

- <복사할 파일 경로>는 절대 경로 사용 불가

- <이미지에서 파일이 위치할 경로>는 절대 경로로 설정

- <이미지에서 파일이 위치할 경로>에서 마지막이 /로 끝나면, 디렉터리 생성 및 그 아래에 파일 복사

**11. COPY**
```sh
COPY hello-dir /hello-dir
````
- COPY <복사할 파일 경로> <이미지에서 파일이 위치할 경로> 형식이다.

- 파일을 이미지에 추가한다.

- ADD와 달리 <복사할 파일 경로>에서 압축 파일에서 압축 해제하지 않고, 파일 URL도 사용 불가

**12. VOLUME**
```sh
VOLUME /data
````
- VOLUME <컨테이너 디렉터리> 형식이다.

- 디렉터리의 내용을 컨테이너에 저장하지 않고 '호스트'에 저장하도록 설정한다.

**13. WORKDIR**
```sh
WORKDIR /var/www
````
- WORKDIR <경로> 형식이다.

- RUN, CMD, ENTRYPOINT의 명령이 실행될 디렉터리를 설정한다.

**14. ONBUILD**
```sh
ONBUILD RUN touch /hello.txt
````
- ONBUILD <Dockerfile 명령> <Dockerfile 명령의 매개 변수> 형식이다.

- 생성한 이미지를 기반으로 다른 이미지가 생성될 때 명령을 실행한다.

- 최초에 사용하면 아무 명령도 실행되지 않고, 다음에 FROM으로 사용될 때 미리 하도록 '예약'한다고 생각하자.
