## Docker 명령어

- sudo usermod -aG docker [사용자ID]

  - docker 그룹에 사용자ID를 추가

- docker ps

- docker ps -a

  - 중지된 컨테이너 까지 보임. -a 안붙이면 안보임

- docker rm CONTAINER

  - 컨테이너 삭제

- docker rmi IMAGE

  - 이미지 삭제

- docker images

  - 다운 받은 이미지 확인

- docker pull <IMAGE_NAME[:latest] or IMAGE_NAME:TAG>

  - 예시 : docker pull ubuntu:lastest

- docker diff CONTAINER

  - Inspect changes to files or directories on a container's filesystem

- docker run -i -t --name ubuntu01 ubuntu /bin/bash

  - 새로운 컨테이너 생성
    * -i : interactive
    * -t : tty
    * --name : 컨테이너 이름 지정 (현재 ubuntu01)
    * /bin/bash : 해당 컨테이너의 bash shell실행 (exit하면 컨테이너도 stop 됨)
    * -d : detached mode(백그라운드모드)
    * -p : 컨테이너 포트와 호스트 포트 연결 (1234:5678 호스트의 1234포트를 컨테이너의 5678에 연결)
    * -rm : 종료시 컨테이너 자동 제거
    * -e :컨테이너 내부 환경 변수 설정
    * 등등

- docker start CONTAINER

  - 기존 컨테이너 실행

- docker restart CONTAINER

- docker attach CONTAINER

  - 가동중인 컨테이너에 접속
  - 꼭!! 명령 후 엔터를 쳐야 셀이 실행됨.


> run -it 옵션과 attach 명령을 쓰지 않으면 bash shell로 들어갈 수 없고, 들어가더라도 exit 치게되면 컨테이너는 멈춰버린다.
>
> * run -it 은 컨테이너의 입출력을 interactive 하게 하고 TTY 터미널을 에뮬레이션 하는 옵션일 뿐인 것이고
>   * (run -it -d 하게되면 interactive 쉘이 background로 동작. 즉 run으로 돌려놓고 빠져나왔을지 몰라도 attach같은걸로 들어갔다가 나오면 또 컨테이너는 멈춤)
> * attach 는 리모트 쉘 개념이 아니라, Host의 표준입출력을 해당 컨테이너에 붙인 것일 뿐이다. (무한루프로 돌려놓은 시스템에 쉘로 접속하려면 attach로는 안되고 exec로 내부에 있는 쉘을 실행시켜야 한다.)
>
> 즉 컨테이너는 자신이 집중하는 서비스를 실행하기 위해서만 존재하고 준비되어 있다고 생각하면 될 듯

> 컨테이너 안의 백그라운드 작업들은 컨테이너가 멈추는 것을 막을 수 없다. (백그라운드 여려개 띄워놔도 exit 해버리면 컨테이너 종료됨)
> 컨테이너가 계속 실행되게 하려면, 실행 되어야 하는 작업이 fore ground로 나와야 한다.

- docker logs [OPTIONS] CONTAINER
- ex: docker logs -f --tail=5 CONTAINER
    - 최근 로그 5개만 계속 모니터링
- docker exec -it 2e6a6e4f9f2 /bin/bash

  - Docker container에 접속 방법
- docker cp /path/foo.txt mycontainer:/path/foo.txt

  - 호스트에서 컨테이너로 파일 전송하는 방법
- docker cp mycontainer:/path/foo.txt /path/foo.txt

  - 컨테이너에서 호스트로 파일 전송하는 방법
- docker info

  - 공식 저장소의 주소 확인



참고 사이트

* [https://www.popit.kr/개발자가-처음-docker-접할때-오는-멘붕-몇가지/](https://www.popit.kr/개발자가-처음-docker-접할때-오는-멘붕-몇가지/)
* https://nicewoong.github.io/development/2017/10/09/basic-usage-for-docker/