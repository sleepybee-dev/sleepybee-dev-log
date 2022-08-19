Zola 공통 사항
---
- 소유권 확인을 위해 DNS 인증이 아닌 html meta tag 인증을 사용한다. (구매한 도메인이 있다면 DNS 인증도 가능)
- html meta tag는 `/zola/template/base.html`의 header에 추가하면 된다.
- Zola를 비롯한 대부분의 SSG(Static Site Generator)들은 검색 엔진 콘솔에 제출할 수 있는 형식으로 사이트맵을 짜준다. 도메인 뒤에 `/sitemap.xml`만 입력하면 된다.
- 탬플릿 수정 후엔 반드시 netlify에서 deploy를 해준다.


구글 검색
---
- 구글 서치 콘솔 Google Search Console
<div class="rich-link-card-container"><a class="rich-link-card" href="https://search.google.com/search-console" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://ssl.gstatic.com/search-console/scfe/search_console-128.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h3 class="rich-link-card-title">Google Search Console</h3>
		<p class="rich-link-card-description">
		
		</p>
		<p class="rich-link-href">
		https://search.google.com/search-console
		</p>
	</div>
</a></div>

- URL 접두어로 인증
![[Pasted image 20220819122540.png]]
- 사이트맵 추가
![[Pasted image 20220819122655.png]]


    
네이버 검색
---
- 구글 서치 콘솔과 크게 다르지 않다.
- 네이버 서치 어드바이저 
<div class="rich-link-card-container"><a class="rich-link-card" href="https://searchadvisor.naver.com/console/board" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://ssl.pstatic.net/sstatic/search/common/og_v3.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h2 class="rich-link-card-title">[네이버: 로그인]</h2>
		<p class="rich-link-card-description">
		안전한 로그인을 위해 주소창의 URL과 자물쇠 마크를 확인하세요!
		</p>
		<p class="rich-link-href">
		https://searchadvisor.naver.com/console/board
		</p>
	</div>
</a></div>

- 사이트 등록 및 메타 태그 인증
- 사이트맵 추가
 ![[Pasted image 20220819123000.png]]

- 웹페이지 최적화
![[Pasted image 20220819124434.png]]

- 최적화에서 옵시디언 노트들이 들어 있는 docs를 돌려보고, 없는 태그를 `/zola/template/base.html`에 추가한다.


+
---
반영하는 데에 며칠이 걸리는 모양이다.
현재 블로그 내용 어떤 걸 어떤 식으로 검색해도 어디에도 노출되지 않는데 경과를 지켜보자.

