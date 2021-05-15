

## 설치

참고:
https://nativescript-vue.org/en/docs/getting-started/installation/
https://docs.nativescript.org/environment-setup.html

* (Vue 개발 환경 설치 - 구글링)

* (Android Studio 설치 - 구글링)

* 환경 변수 추가

  * 안드로이드 관련
    * ANDROID_HOME = %LOCALAPPDATA%\Android\Sdk
    * PATH += %LOCALAPPDATA%\Android\Sdk\platform-tools
  * JAVA 관련 (Andriod Studio의 JDK 이용)
    * JAVA_HOME = C:\Program Files\Android\Android Studio\jre
    * PATH += %JAVA_HOME%\bin

* NativeScript 설치

  ```bash
  npm install -g nativescript
  ```


## 프로젝트 시작 (Initializing)
참고:
https://nativescript-vue.org/en/docs/getting-started/quick-start/

```
1. ns create <project-name> --vue
2. cd <project-name>
3. npm install
4. <Android Studio의 Android Emul 실행 or Android 실기기 Debug모드로 USB 연결>
	- (아래의 "Android Emul. 실행 스크립트 추가" 내용을 package.json에 추가 저장 후)
	- npm run avd-list (목록에 표시되는 avd 이름을 Ctrl+C)
	- npm run avd-start <avd 이름>
5. ns run
```

* (참고) [vue-cli-template](https://github.com/nativescript-vue/vue-cli-template)를 이용하는 방법도 있지만 [vue-cli-template](https://github.com/nativescript-vue/vue-cli-template)가 최신 Vue CLI 버전 적용 안돼서 비추
  
  * [vue-cli-template](https://github.com/nativescript-vue/vue-cli-template)가 Vue CLI 2.x까지만 지원해서(지금 Vue CLI 4.x임) 안쓰는게 좋을 듯...
  
* (Trouble Shooting) PSSecurityException 에러가 뜬다면
  PowerShell을 관리자 권한으로 열고 아래의 명령 실행

  ```
  PS C:\WINDOWS\system32> Set-ExecutionPolicy Unrestricted
  실행 규칙 변경
  실행 정책은 신뢰하지 않는 스크립트로부터 사용자를 보호합니다. 실행 정책을 변경하면 about_Execution_Policies 도움말
  항목(https://go.microsoft.com/fwlink/?LinkID=135170)에 설명된 보안 위험에 노출될 수 있습니다. 실행 정책을
  변경하시겠습니까?
  [Y] 예(Y)  [A] 모두 예(A)  [N] 아니요(N)  [L] 모두 아니요(L)  [S] 일시 중단(S)  [?] 도움말 (기본값은 "N"): Y
  ```

* (편의) Android Emul. 실행 스크립트 추가
  * package.json에 아래의 내용 추가

  ```
  "scripts": {
    "avd-list": "%ANDROID_HOME%\\emulator\\emulator.exe -list-avds",
    // npm run avd-list // 설치된 Android Emul. 리스트 출력 (리스트에 아무것도 없을때는 가상기기 추가할것)
    "avd-start": "%ANDROID_HOME%\\emulator\\emulator.exe -avd"
    // npm run avd-start <가상기기명> // avd-list에서 나온 가상기기명을 입력
  }
  ```



### 기본 앱 실행 화면

![image-20210515141544256](NativeScript_Vue_%ED%99%98%EA%B2%BD_%EC%84%B8%ED%8C%85.assets/image-20210515141544256.png)



### 앱 배포 방법 (Google Play/App Store)

참고:
https://docs.nativescript.org/releasing.html

