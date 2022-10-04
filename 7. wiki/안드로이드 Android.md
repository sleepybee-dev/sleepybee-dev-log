- 모바일 장치용으로 디자인된 운영 체제
- 리눅스 커널 위에서 동작하며 Java와 Kotlin으로 앱을 만들어 동작한다.
- 구글에 의해 개발 중


### 4대 컴포넌트
각 컴포넌트들은 하나의 독립적인 형태로 존재.
고유의 기능을 수행.
인텐트Intent를 통해 서로 상호작용.

1. 액티비티 Activity
2. [서비스 Service](https://developer.android.com/guide/components/services?hl=ko)
	(1) 포그라운드 서비스와 백그라운드 서비스
		- 포그라운드는 사용자가 눈으로 확인할 수 있다. (예: 앱이 꺼졌어도 떠있는 음악 플레이어)
		- 포그라운드는 사용자가 앱과 상호작용이 가능하다. (예: 음악 일시정지, 다음곡 재생 등)
		- Android 8.0 (API 26) 이상을 타겟팅한다면 [백그라운드 실행이 제한된다.](https://developer.android.com/guide/components/services?hl=ko)
3. 브로드캐스트 리시버 Broadcast Receiver
4. 콘텐트 프로바이더 Content Provider