<div class="rich-link-card-container"><a class="rich-link-card" href="https://play.google.com/store/apps/details?id=com.gmail.sleepybee410.picshelf" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://play-lh.googleusercontent.com/Io_32thL5IlHQOel9o2EWGXRJV36EDa0MS-OwezejyoU7Mt0rwIfOeTb-WQbRmCUCA=w600-h300-pc0xffffff-pd')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h3 class="rich-link-card-title">사진 액자 위젯 - 픽셸프 - Apps on Google Play</h3>
		<p class="rich-link-card-description">
		Check your photos on the home screen.
		</p>
		<p class="rich-link-href">
		https://play.google.com/store/apps/details?id=com.gmail.sleepybee410.picshelf
		</p>
	</div>
</a></div>


Concept
---
![[picshelf_screenshots.png]]
-   <**픽셀프Picshelf**>는 아주 심플한 사진 위젯 앱이다.
- 간단하게 프레임을 씌우거나 사진 이름을 노출할 수 있다. 
- 앱 이름은 책장을 뜻하는 Bookshelf에서 따와서 사진장이라는 뉘앙스로 지었다.
   

why
---
- 선물받은 기프티콘 맨날 안 쓰고 유통기한이 지난다.
- 선물받은 건 카톡으로 알림이라도 오지 당근마켓에 산 기프티콘이나 경품으로 문자로 받은 기프티콘은 알림도 없이 날린다.
- 바탕화면에 기프티콘을 띄워놓고 바로 바코드를 찍게 하고 싶다.



Simple Scenario
---
-   스마트폰 바탕화면 롱클릭하여 위젯 추가 > 픽셀프 선택 > 사진 선택 후 재배치 및 크기 조절   
   

Remarkable
---
- 사진 위젯 앱이 개발 당시에도 많았지만 너무 아무 것도 없거나 너무 많은 게 있거나 해서 개발했다.
- 앱 소개 스크린샷에서는 동생들과 찍은 다정한 사진이 있지만, 실제로는 기프티콘 생기면 바탕화면에 노출하는 용도로만 잘 쓰고 있다.



Dev Story
---
- `Kotlin`, `MVVM`, `AAC`, `AppWidgetManager`
- Widget을 다루는 개발을 안 해봐서 경험 삼아 만들어 본 것도 있다.
- 사이즈가 작은 앱임에도 습관적으로 Bitbucket을 쓰다 보니 소스가 비공개였다. 하지만 취업 전선에서 내 코드 스타일을 보여줄 필요가 있어서 이제와서야 아키텍쳐도 붙이고 GitHub에 공유한다.
- GitHub : https://github.com/sleepybee-dev/picshelf


Release
---
- v.0.1.0 - 2020.12.02
	- 최초 배포


#Kotlin 
#MVVM 
#Widget 
