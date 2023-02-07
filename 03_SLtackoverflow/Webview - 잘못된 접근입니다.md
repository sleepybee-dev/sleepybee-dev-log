## android Webview JS Error

```bash
I/chromium: [INFO:CONSOLE(1)] "isTestBed :  undefined", source: {URL}ca536681dfacfdeca5.js (1)
I/chromium: [INFO:CONSOLE(1)] "accessToken true nscreen@#dev9407token", source: {URL}1dfacfdeca5.js (1)
I/chromium: [INFO:CONSOLE(1)] "Custom vue error handler:  TypeError: window.NI.device.setBackKeyHandler is not a function [object Object] mounted hook", source: {URL}ca536681dfacfdeca5.js (1)
I/chromium: [INFO:CONSOLE(9)] "Native setOnReady : true", source:{URL}
I/chromium: [INFO:CONSOLE(1)] "set cookie accesstoken=", source: {URL}6681dfacfdeca5.js (1)
```

Webview에서 loadUrl을 했더니 크로미움에서 이런 식의 자바스크립트 에러를 내보낸다.
뷰가 노출되지 않고 '잘못된 접근입니다'라는 시스템 에러창이 떴다.


## setDomStorageEnabled(boolean)
자바스크립트가 로컬 DOM 스토리지를 사용하게끔 해주면 해결된다하여 메소드를 넣었다.

```Java
webSettings.setDomStorageEnabled(true);
```

바로 해결되었다.

한 가지 의문인 점은, 같은 코드로 Android 11 기기에서는 발생하지 않았으나 Android 6.0.1 기기에서 발생한 것이다. Android System Webview 버전이 높아짐에 따라 어느 정도 지원되는 것들이 있는 갑다 하고 추측.

