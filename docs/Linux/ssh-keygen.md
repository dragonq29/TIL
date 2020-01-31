scp를 사용할 때 비밀번호 없이 하는 방식을 적어볼까 합니당.

step으로 나눠서 적을 껀데요. 이 step은 scp를 사용할 서버에서 하셔야 합니다.

굳이 리눅스 서버들을 나누자면 클라이언트가 아닌 소스코드가 실행되는 서버에서 하셔야 데는거에요!!! 



**Step 1. 터미널을 열고 scp를 사용할 사용자의 home 폴더 아래 있는 .ssh 폴더로 이동한다.**

간단하죠? 터미널(Terminal)을 열어주시고 scp를 사용할 사용자.. 음 저 같은 경우는 걍 저의 아이디니깐요.

즉 터미널에 다음과 같은 명령어를 써주면 데겠죠?

**명령어 : cd /home/사용자아이디/.ssh** 

ssh앞에 점(.)이 있어요 !!! 숨겨진 폴더니깐요. 

**Step 2. 공개키를 생성한다.**

공개키를 생성하기 위해서는 다음과 같은 명령어를 통해서 하실 수 있어요.

**명령어 : ssh-keygen -t rsa**

그럼 Figure 1과 같은 화면이 나올껀데요. 간단해요. ^ ^ 

``` command
$ ssh-keygen -t rsa
Enter file~~~~ : [rsaKeyName]
Enter passphrase~~ : [Enter]
Enter same passphrase agein : [Enter]

```



제일 처음 입력하실 것은 생성할 KEY 이름입니다. 적당한 걸로 해주세영.

다음은 passphrase 로 암호를 사용하지 않으실 예정이면 엔터 엔터 !!! 

그럼 입력하신 KEY 이름으로 RSA KEY가 생성됩니다 !!! 



**Step 3. 공개키를 scp의 대상이 되는 클라이언트 서버로 복사합니다.**



이것도 명령어가 있어요. 캬.



**명령어 : ssh-copy-id userName@client_ip_address**

  **ex  : ssh-copy-id aaaa@111.11.1x.11x**



쉽죠? 위 명령어를 치면 userName에 해당하는 password를 물어볼 겁니다. 입력해주시고 enter 누르면 이제 끝났어요. !!!!



scp를 막 사용해도 비밀번호를 물어보지 않는답니다.



그럼 개발 고고!!!



출처: https://ngee.tistory.com/80