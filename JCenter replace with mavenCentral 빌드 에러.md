이미 많이들 아시겠지만 JCenter가 21년 3월 31일 이후로 추가 업데이트를 받지 않았다. 이렇게 서비스 종료 수순을 밟으려다가 커뮤니티의 뭇매를 맞고(ㅎㅎ) read-only 무기한 서비스를 제공하겠다고 하였다.
https://jfrog.com/blog/into-the-sunset-bintray-jcenter-gocenter-and-chartcenter/


```gradle
buildscript {  
    repositories {  
        google()  
        jcenter()
    }
    ...
```

> JCenter Maven repository is no longer receiving updates: newer library versions may be available elsewhere

프로젝트/build.gradle에서 repository에 `jcenter()`를 넣으면 위와 같은 경고 문구가 볼 수 있다.
무작정 `replace with mavenCentral()`을 하면 빌드 에러가 발생한다.

```
* What went wrong:
Execution failed for task ':app:dataBindingMergeDependencyArtifactsDevDebug'.
> Could not resolve all files for configuration ':app:devDebugCompileClasspath'.
   > Could not find com.google.android.exoplayer:exoplayer-core:2.12.1.
     Required by:
         project :app
   > Could not find com.google.android.exoplayer:exoplayer-ui:2.12.1.
     Required by:
         project :app
   > Could not find com.danikula:videocache:2.7.1.
     Required by:
         project :app

```

로그 상 exoplayer와 videocache가 잡혔는데 해결법이 각각 다르다.
exoplayer의 경우 mavenCentral()에 최신 버전부터 올라가 있으므로 dependency 버전을 올려줘야 한다.
videocache의 경우는 찾아보니 아예 mavenCentral에 업데이트가 없어서 JCenter에서밖에 내려받을 수 없다.

이 경우 아래와 같이 **둘다** 선언해주면 빌드 에러는 해결된다.
```gradle
buildscript {  
    repositories {  
        google()  
        jcenter() // for videocache
        mavenCentral()
    }
    ...
```

또는 버전을 올리지 않고 `jcenter()`만 선언하고 JCenter에 올라온 가장 최신 버전을 사용할 수도 있다. 
https://github.com/google/ExoPlayer/blob/release-v2/RELEASENOTES.md
exoplayer의 경우 **2.16.0 (2021-11-04)** 까지 JCenter를 통해 배포되었다.

하지만 android 33까지 가면서 기기 권한 등 많은 것들이 변하고 있기 때문에, target 버전을 올린다면 더이상 업데이트 되지 않는 videocache같은 라이브러리는 걷어내야 할 것이다.

