MySQL/MariaDB 실행 방법

* DB내부의 root계정으로 실행

  ```mysql -uroot -p```

  * 명령 풀이: mysql -u[계정명] -p[패스워드:비워져있으면 물어봄]

  * dragons 계정으로 실행

    ```mysql -udragonq -p```

* 데이터베이스 보기

  ```show database;```

* 데이터베이스 생성

  ```create database [데이터베이스명];```

* 데이터베이스 사용

  ```use [데이터베이스명]```

* 테이블 보기 (데이터베이스 보다 하위 개념)

  ```show tables;```

* 테이블 생성

  ```
create table [테이블명](
  	[필드명 타입],
  	...
  	[필드명 타입]
  	PRIMARY KEY([필드명])
  )
  ```
* 필드 보기 (테이블 보다 하위 개념)

  ```desc [테이블명]```

* 

