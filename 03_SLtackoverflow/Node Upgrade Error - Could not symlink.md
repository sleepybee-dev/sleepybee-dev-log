---
date: 2022-09-30
---

Firebase CLI를 사용하기 위해서는 Node 일정 버전 이상이 필요하다.

> Firebase CLI v11.12.0 is incompatible with Node.js v12.14.0
> Please upgrade Node.js to version ^14.18.0 || >=16.4.0


### brew를 통한 업그레이드
```bash
brew upgrade node
```
이렇게 간단하게 끝날 줄 알았으나,

### Node.js 버전 체크
```bash
node -v
```
버전 체크를 해보면 그대로다.
서치해보니 brew로 간단하게 link가 된다고 한다.

### 인스톨한 Node.js를 시스템에 연결
```bash
brew link --overwrite node
```
이렇게 또 간단할 줄 알았으나,

### Write 권한 문제
```bash
Error: Could not symlink include/node/common.gypi

/usr/local/include/node is not writable.
```
권한 문제 발생.
어째선지 `/usr/local/inclue`를 `chown` 명령어로 소유자 변경하여도 똑같았다.

### brew의 소유자 변경하기
```bash
sudo chown -R {USER_NAME} $(brew --prefix)/*
brew link node
```
그래서 아예 brew 명령어에 소유자 변경을 걸었다.
\* **-R** = Recursive : 하위 폴더까지 함께 소유자 변경

최신 버전의 Node.js가 성공적으로 link되었다.

소유권을 여기저기 뿌리는 것은 보안적으로 좋은 방법은 아니겠으나 brew를 쓰는 이상 감수할만하다고 생각된다.

Good Luck.

