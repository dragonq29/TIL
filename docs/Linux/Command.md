



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

* 파일 찾기 (예: java) [참고)](https://overcode.tistory.com/entry/리눅스-파일-찾기-파일속-문자열-찾기)]
  ```find -name java```
```find / -name ``"elasticsearch.yml"```
  
* 현재 디렉토리에서, pl 확장자를 가진 모든 파일 찾기 (현재 디렉토리 밑의 하위 디렉토리까지 다 찾습니다.)
  ```find -name '*.pl'```
  
* 루트에서부터, 즉 전체 하드에서, pl 확장자를 가진 모든 파일 찾기
  ```find / -name '*.pl'```
  
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

* 현재 있는 폴더의 모든 파일을 지울때
  ```rm -rf * // 현재 디렉토리의 모든 것을 삭제```

* 마운트 가능한(꽂혀있는) 디스크 전체 보기
  ```fdisk -l```

* 퍼미션 유지하며 하위디렉토리 복사하기
  ```cp -Rp /var/lib/mongodb /data```

* 모든 터미널 라인 저장

  ```
  # script [파일명]
  //으로 적고, 끝나고 난 뒤,
  # exit
  //이라고 하면, script ~ exit 까지의 모든 콘솔 출력이 지정된 log 파일로 저장됩니다.
  ```

* 부팅시 자동시작(mariadb의 경우)
  ```# systemctl enable mariadb.service```

* 한페이지에 표지되는 내용이 너무 길때 (q누르면 종료)
  ```ls /usr/bin | less```

* Screen(터미널 내에서 여러 터미널 사용) 사용법

  ```
  screen -list    // 목록보기
  screen -R       // 현재 떠있는 스크린에 들어가기
    
  //Screen 사용중 명령
  Ctrl+a and Ctrl+'   // 다른 스크린으로 이동
  Ctrl+a and c        // 새 스크린 만들기
  Ctrl+a and [ and 방향키 or page up/down // 스크린에서 스크롤 페이지 이동
  ```

* 공유 폴더(Samba 설정)

  * 공유 폴더 src 세팅

    * vi /etc/samba/smb.conf (만약 SnapshotStorage를 추가한다면)

    * ```
      [SnapshotStorage]
      path = /storage/SnapshotStorage
      public = Yes
      writeable = Yes
      create mask = 0777
      directory mask = 0777
      browseable = Yes
      read only = No
      valid users = gk2
      ```

    * 수정 후 sudo service smbd restart 또는 sudo systemctl restart smb

  * 공유 폴더 마운트 확인 (Client 입장)

    - ```
      df -a
      ```

  * 특정 서버의 열린 공유 폴더 확인

    ``` 
    dragonq@localhost:~$ smbclient -L [IP]
    Domain=[MYGROUP] OS=[Windows 6.1] Server=[Samba 4.8.3]
            Sharename       Type      Comment
            ---------       ----      -------
            CIFSTEST        Disk
            TestData        Disk
            IPC$            IPC       IPC Service (Samba Server Version 4.8.3)
            go             Disk      Home Directories
    Domain=[MYGROUP] OS=[Windows 6.1] Server=[Samba 4.8.3]
            Server               Comment
            ---------            -------
            GO2                 Samba Server Version 4.8.3
            Workgroup            Master
            ---------            -------
            MYGROUP              GO2
            WORKGROUP            DESKTOP-QSEQ327
    ```
    
    ADMIN$, C$, IPC$, 이처럼 폴더 이름 뒤에 ‘$’가 붙은 공유 자원은 숨은 공유(또는 관리 공유)라고 하며 실제 공유 폴더 외에는 윈도 사용자에게 보이지 않음
    
    주로 관리자가 공유 자원을 관리하기 위한 목적으로 사용되며 윈도 시스템이 부팅할 때 자동으로 공유
    
    ADMIN$은 윈도 시스템 폴더인 C:\WINDOWS를, C$는 루트 폴더인 C:\를 의미
    
    IPC$는 자원 공유에 필요한 세션 연결, 사용자 인증을 처리하기 위한 공유 자원임
    
  * SmbClient 사용
  
    ``` 
    dragonq@localhost:~$ smbclient //192.168.30.80/sharedFolder
    Enter dragonq's password:
    Domain=[DD] OS=[Windows 10] Server=[Windows 10]
    smb: \> ls
      .                                   DR      0 Mon Apr 22 03:21:33 2015
      ..                                  DR      0 Mon Apr 22 03:21:33 2015
      XXXX.dat                            HS     75 Mon Apr 22 02:21:32 2015
      YYYY.dat                            A         Tue Jul 13 13:42:25 2019
           41097 blocks of size 1043576. 40116 blocks available
    ```
  
    
  
  * 공유 폴더 마운트 연결
  
    - 방법 1 (임시로 설정 방법)
      - ~~sudo mount -t cifs //[타겟IP]/storage /mnt/storage -o username=[타겟ID],password=[타겟비밀번호]~~
        - 마운트된 폴더 권한 확인 해보면 root라서 non-root로는 쓸수 없을 것이다.
          - 아래와 같이 하면 non-root로 됨
            - → sudo mount -t cifs //[타겟IP]/storage /mnt/storage -o username=[타겟ID],password=[타겟비밀번호],uid=[유저],gid=[유저]
    - 방법2 (완전 세팅 방법) - 권장함
      - vi /etc/fstab
        - 대상 행 추가 (맨 뒤에 0 0은 오타가 아님)
          - //192.168.30.187/SnapshotStorage /storage/SnapshotStorage cifs user=[유저],password=[암호],uid=[유저],gid=[유저] 0 0
        - 이후 적용
          - fstab의 내용 모두 다시 적용
            - sudo mount -a (vi /etc/fstab의 내용 모두 실행) -> sudo로 했지만 마운트된 폴더가 non-root 유저 권한으로 됨
          - 하나의 폴더만 적용
            - sudo mount [해당 폴더 경로]
    - 연결이 안될때 확인 해볼 사항
      - Samba 버전이 안맞을 수 있음. 세팅 멘 뒤에 vers=2.1이나 vers=1.0 등을 추가해 볼것
      - mount가 안될때 sudo yum install -y cifs-utils 해서 cifs 클라이언트를 설치할것
      - 서버쪽 139 포트 열려있는지 확인
  
* 서버간 파일 전송
  ```scp -r [src폴더명] [des IP]:/[des폴더명]```

* 현재폴더에 있는 폴더 및 파일 용량 확인
  ```du -hs *```

* 폴더 내에 있는 텍스트 파일들의 내용 중 특정 문자열을 찾아 원하는 문자열으로 일괄 교체(예: GK2~~로 되는 파일들의 "ykpark"을 "1068"로 수정)

  ```find ./GK2* -type f -exec sed -i 's/ykpark/1068/g' {} \;```

* 

* 리눅스 CPU 사용량 (키 "1"을 누르면 맨 위에 현재 CPU의 점유율 나옴)
  ```top -d 1```

* 문서에서 IP 뽑아 내기(정규식 사용)
  ```grep -Eo ‘[[:digit:]]{1,3}[.][[:digit:]]{1,3}[.][[:digit:]]{1,3}[.][[:digit:]]{1,3}’ dnsmasq.log```

* Tail (마지막 20줄을 실시간으로 계속 보여줌)
  ```tail -f -n 20 /var/log/messages```
  
* crul로 파일 받기(url.txt 받기)
  
  ```curl -O https://url.com/url.txt```
  
* 방화벽 관련

  ```
firewall-cmd --zone=public --list-all	// 열린 포트 확인
  firewall-cmd --permanent --zone=public --add-service=http	// http 서비스 추가
firewall-cmd --permanent --zone=public --add-port=5563/tcp	//5563 포트 추가
  firewall-cmd --permanent --zone=public --remove-service=http	// http 서비스 삭제
firewall-cmd --permanent --zone=public --remove-port=80/tcp	// 80 포트 삭제
  firewall-cmd --permanent --zone=public --add-service=samba // 윈도우에서 리눅스 저장소 보려면 필요
  firewall-cmd --reload	// 수정 내역 적용
  ```
```
  
* 네트워크 설정 보기 (게이트웨이 등등)

  '''/etc/sysconfig/network-scripts/[네트워크명]'''

  

* NTP 설정

  * NTP 확인
    * ``` ntpq -p ```
  * NTP 실행
    * ``` vi /etc/ntp.conf ```
      * server 로 시작하는 것들 #으로 주석처리 하고 아래의 문자열 넣기
      * ``` server [ip] iburst``` (iburst가 없으면 10분 이상 차이날때만 동기화됨)
    * ``` sudo service ntpd start ```

  

  ## 예제 중심 설명

  * curl -sL \    https://deb.nodesource.com/setup_6.x \    | sudo -E bash -
    * curl -sL : 정숙 모드. 진행 내역이나 메시지등을 출력하지 않습니다. 리다이렉션이 있을 경우 따라감
    * sudo -E bash - : 모르겠음
  * sed -i -e 's/8080/80/g' server.js
    * Server.js 파일의 8080
      * -i : 변경되는 값을 실제로 파일에 저장하는 옵션
      * -e : sed를 사용하였을 때 출력되는 값을 보여줌
      * /g :단지 첫번째의 것만이 아니라 라인의 모든 부합 패턴 대체가 적용 되게 한다
  * grep -r "aaa" ./*
    * ./(현재 폴더 아래 모든 파일에서) aaa라는 문자열이 있는지 찾기. 하위 디렉토리 모두에서(-r)
  * cat aaa bbb > ccc
    * aaa파일과 bbb파일을 합쳐서 ccc 파일로 저장

```
* 로그 디버깅
  
  * tail -v
  
* CentOS GUI 버전을 시작시 CMD 버전으로 설정 방법

  ```
  systemctl get-default // 현재 상태 확인
  systemctl set-default multi-user.target // CMD 버전으로 세팅 (GUI 버전은 graphical.target)
  reboot
  ```

  

* CentOS에서 NVIDIA 드라이버 설치법

  https://www.cyberciti.biz/faq/how-to-install-nvidia-driver-on-centos-7-linux/

  [https://linux.systemv.pe.kr/nvidia-driver-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/](https://linux.systemv.pe.kr/nvidia-driver-설치하기/)]

* 여러파일 확장자 한방에 변경
  
  ``` 
  for f in *.예전확장자; do mv -- "$f" "${f%.예전확장자}.새확장자"; done
  ```
  
* 여러 파일의 내용 한번에 replace

  ```
  find -name <찾을 파일명> -exec perl -p -i -e 's/<바꿔야할문자>/<바꾼문자>/g' {} \;
  예) find . -name "*.hdr" -exec perl -pi -e 's/STAT=SC/STAT=KC/g' {} \;
  ```

  

* 시스템 상태 정보 분석

  ```bash
  #!/bin/bash
  MEMORY=$(free -m | awk 'NR==2{printf "%.2f%%\t\t", $3*1100/$2}')
  DISK=$(df -h | awk '$NF=="/"{printf "%s\t\t", $5}')
  CPU=$(top -bn1 | grep load | awk '{printf "%.2f%%\t\t\n", $(NF-2)}')}
  
  LOG_DIR=/storage/TEST_LOG
  mkdir -p $LOG_DIR
  
  while [ true ]; do
  	DATE_STR=$(date +"%Y-%m-%d")
  	FILENAME=$DATE_STR.log
  	TIME_NOW=$(date +"%Y-%m-%d_%H:%M:%S")
  	echo "$TIME_NOW Memory: $MEMORY DISK: $DISK CPU: $CPU" >> $LOG_DIR/$FILENAME
  	sleep 1
  done
  ```

* 백그라운드 실행 파일
  ```bash
  #!/bin/bash
  nohup ./파일명.sh 1>/dev/null 2>&1 &
  ```
  
* top 사용법

  ```
  top -d 1
  ```

  * Shift + f : 필터 걸 수 있는 화면 열기
    * 필터 걸고 싶은 항목에서 's' 누르면 제일 상단 오른쪽 쯤에 필터가 걸린 것을 볼수 있음. 필터 걸고 'q' 눌러서 top 화면 돌아감
  
* CentOS 런레벨 바꾸기

  ```
  Runlevel 3은 multi-user.target
  Runlevel 5는 graphical.target
  
  기본 런레벨을 3/5레벨로 바꾸려면 다음 명령어를 입력
  systemctl set-default multi-user.target;
  systemctl set-default graphical.target;
  
  5레벨에서 3레벨로 바꾸려면 다음 명령어를 입력
  systemctl isolate multi-user.target;
  
  3레벨에서 5레벨로 바꾸려면 다음 명령어를 입력
  systemctl isolate graphical.target;
  
  ```

  

* nc 명령 (NetCat)

  * Linux, “nc” 명령을 통해 “Process”에서 장비로 Port 3075로 접속 확인
    * 예시 - “nc 127.x.x.x 3075”