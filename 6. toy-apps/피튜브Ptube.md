<div class="rich-link-card-container"><a class="rich-link-card" href="https://play.google.com/store/apps/details?id=com.gmail.sleepybee410.ptube" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://play-lh.googleusercontent.com/_AHN3yJeSefJQr0qNdCs3Nc0rEzh836xV7C1nx2DVh3ivy5W6kWAJRQeUiw-Bn03Dw=w600-h300-pc0xffffff-pd')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h3 class="rich-link-card-title">PTube - Private Video Channels - Apps on Google Play</h3>
		<p class="rich-link-card-description">
		Create your own private video channel.
		</p>
		<p class="rich-link-href">
		https://play.google.com/store/apps/details?id=com.gmail.sleepybee410.ptube
		</p>
	</div>
</a></div>

Concept
---

-   <**피튜브PTube**>는 유튜브 링크를 게시하는 프라이빗 그룹 앱이다.
- 초대코드로만 들어올 수 있는 그룹(채널) 안에서 유튜브 링크들을 게시해 함께 리스트를 공유할 수 있다.
- 유튜브는 업로드된 영상을 '링크 공개' 상태로 할 수 있는데 그러한 영상들을 모아 보기에 유용하다.
   

why
---

- 난 여행을 가면 꼭 영상을 찍고 편집하는데 대용량이라 유튜브에 올려서 같이 간 친구들에게 공유한다. 다른 사람들이 보는 걸 원하지 않기 때문에 '링크 공개'로 해두는데 이러면 내 채널에 와도 영상을 볼 수 없으며 그 친구들이 훗날 다시 영상을 보고 싶으면 내가 다시 링크를 따서 공유해야 하는 번거로움이 있다.
- 때문에 '비공개 채널'의 개념을 만들어 '링크 자체'를 데이터로 가지고 있는 그룹을 만들면 어떨까 해서 만들었다.
- 실제로 친구들을 초대한 비공개 채널에 여행 영상들을 올리면서 잘 활용하고 있다. 



Simple Scenario
---
- 프라이빗 채널 개설 (또는 초대코드 입력) -> 동영상 업로드 -> 게시된 동영상을 누르면 유튜브로 연결  
   


Dev Story
---

- `Flutter`, `Youtube data API`, `Firebase` 
- Flutter로 처음 만든 앱이라 아키텍쳐가 없다. 여유가 될 때 적용해 볼 예정.
- 누가 봐도 개발자가 디자인했네 하는 디자인이었으나 디자이너 지망생 친구가 연습 삼아 디자인을 붙여줬다. 협업은 XD를 활용했다.
- 이때 디자인한 다이아몬드 모양의 FAB Dial이 Flutter에 마땅한 라이브러리가 없어서 UI 라이브러리까지 만들어서 반영했다. [[diamond_dial_fab (Library)]]


#Flutter
#MVVM 
#Widget