## 에러 메시지
> Class has been compiled by a more recent version of the Java Environment (class file version 53.0), this version of the Java Runtime only recognizes class file versions up to 52.0.

읽어보면 자바 버전이 안 맞는다는 얘기다.
이 글을 보는 많은 사람들이 Java8에서 Java11로 점프하려는 과정 중에 있을 것이다.

stackoverflow에 돌아다니는 내용을 이것저것 해봐도 안됐는데 허무하게 해결했다.

## Gradle JDK를 최신으로 변경
![[Pasted image 20221007152025.png]]
1.8에서 11로 바꿔줬다. 내가 설치한 글로벌 자바 버전에 맞춘 것.

## build.gradle에서 프로젝트
원래 1.8에서 컴파일했던 프로젝트의 `app/build.gradle`에 compileOptions 추가.

```Java
android {
	...
	compileOptions {  
	    sourceCompatibility JavaVersion.VERSION_1_8  
	    targetCompatibility JavaVersion.VERSION_1_8  
	}
}
```

삽질 2시간.
The End.
Good Luck.
