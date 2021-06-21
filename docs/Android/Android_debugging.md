Android Studio의 adb를 이용한 디버깅

* 아래와 같이 치면 unauthorized가 아니라 device로 뜸(폰에서 USB 허용 세팅해야함)

  ```
  C:\> adb devices
  List of devices attached
  R39M501473L     device
  ```

* logcat을 이용하여 로그 확인(폰을 ON한 시점부터 로그가 다 뿌려짐)

  ```
  C:\> adb logcat > log.txt
  ```

  