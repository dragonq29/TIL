## 리눅스 명령어

* 현재 존재하지 않은 디렉토리의 하위디렉토리까지 생성
  ``` mkdir -p girls/tiffiny ```

* 파일이동(/dev/test 라는 파일을 /var/www/html/test로 이동)
  ```mv /dev/test_folder var/www/html/test_folder```

* 폴더이동(/dev/test_folder 라는 폴더를 /var/www/html/test_folder로 이동)
  ```mv  /dev/test_folder  /var/www/html/test_folder```

* 파일이름변경(/dev/test 라는 파일을  /dev/aaa 로 파일 이름을 변경)
  ```mv  /dev/test  /dev/aaa```

* SSH로 HTTP 다운로드(현재 폴더에 다운로드 됨)
  ```wget http:``//cfile3.uf.tistory.com/image/133BD1594DFD44E33AE5B6```

* Unzip(unzip을 설치한 후에 실행)
  ```unzip happy.zip```

* scp 명령

  ```
  scp 계정@서버주소:원본경로 목적파일명 //기본 포트 사용
  scp -P 포트 계정@서버주소:원본경로 목적파일명 //다른 포트 사용
  scp -r 계정@서버주소:원본경로 목적상위폴더 //폴더 복사
  scp -r testuser@135.79.246.81:/var/www/html/ /var/www/ //예시
  ```

* 프로세스 목록 보기(예: sonar에 관련된)
  ```ps -ef | grep sonar```

* 경로를 알고 싶을때(예: jdk 설치후 java의 경로)
  ```which java```

* 파일 찾기 (예: java)
  ```find -name java```

  * 현재 디렉토리에서, pl 확장자를 가진 모든 파일 찾기

    find -name '*.pl'


    (현재 디렉토리 밑의 하위 디렉토리까지 다 찾습니다.)

  * 루트에서부터, 즉 전체 하드에서, pl 확장자를 가진 모든 파일 찾기

    find / -name '*.pl'

  * 전체 하드 디스크에서, 파일명이 ab 로 시작하는 모든 파일 찾기

    find / -name 'ab*'

  * 전체 하드 디스크에서, 파일명이 .bash 로 시작하는 모든 파일 찾기

    find / -name '.bash*'

  * 전체 하드 디스크에서, 파일명이 .bash 로 시작하는 모든 파일 찾기
    \+ ls 명령 형식으로 출력

    find / -name '.bash*' -ls

* 디렉토리명 찾기

  * 전체 하드 디스크에서, 디렉토리 이름이 et 로 시작하는 모든 디렉토리 찾기

    find / -name 'et*' -type d

    주의! 옵션 순서를 바꾸면 에러가 납니다.

* 파일정보 보기

  * 목록을 자세히 그리고 숨김파일을 포함하여 파일사이즈순으로 용량을 알아보기 쉽게 나열
    ```ls -lahS```
  * 목록을 자세히 그리고 파일사이즈 순으로 하위디렉토리까지 나열함
    ```ls -lSR```

* 환경변수 확인

  * 환경변수 리스트 보기
    ```export```
  * 해당 변수명의 변수값 등록
    ```export [변수명]=[변수값]```
  * 해당 변수값 확인
    ```echo $[변수명]```
  * 변수명에 변수값 추가
    ```export [변수명]=$[변수명]:[변수값]```

* 포트 프로세스 목록 확인

  ```
  netstat -tnlp | grep -v 127.0.0.1 | sed 's/:::/0 /g' | sed 's/[:\/]/ /g' | awk '{print $5"\t"$10}' | sort -ug
  ```

  

* alias 설정 (부팅시 자동으로 실행되게 하려면 ~/.bashrc에 추가)

  ```
  alias rm='rm -i'
  alias cp='cp -i'
  alias mv='mv -i'
  alias ll='ls -l --color'
  ```

* 그룹 추가
  ```gpasswd -a [사용자] [그룹]```

* 파일 또는 폴더 권환을 하위 폴더까지 변경

  ```
  chown -R [폴더명 또는 파일명] [사용자] // 사용자 권한 변경
  chgrp -R [폴더명 또는 파일명] [사용자] // 그룹 권한 변경
  chown -R mongod:mongod <directory name> // 둘다 동시에
  ```

  