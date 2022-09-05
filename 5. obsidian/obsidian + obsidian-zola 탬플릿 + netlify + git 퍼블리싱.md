이 글을 따라오면 메모-포스팅-발행까지 옵시디언 원툴로 가능해진다.
심지어 무료다.(22년 8월 현재)
 
본 가이드에서 탬플릿은 내가 쓰고 있는 [obsidian-zola](https://github.com/ppeetteerrs/obsidian-zola)를 사용할 것이다. 몇 가지 검토해봤는데 옵시디언 데스크탑 앱이나 공식 퍼플리싱과 레이아웃이 비슷하고 Github에 있는 소스도 이해하기 편해서 선택했다.

> 다른 SGG도 사용가능하지만 obsidian의 데이터 구조를 그대로 활용할 수 있게끔 나온 탬플릿인 것이 좋다. 또한 마크다운 기본 문법이 아닌 아웃링크 \[\[\]\]가 링크화되게끔 처리되어 있어야 편하다.

> **netlify**는 SGG별로 build option을 다르게 주면 통합 처리된다고 하니 다른 SGG를 사용한다면 [여기](https://docs.netlify.com/integrations/frameworks/?_ga=2.155139773.421626894.1662357885-538442470.1660614030)가 참고가 될 것이다.



## 0. 결과물 데모
<div class="rich-link-card-container"><a class="rich-link-card" href="https://peteryuen.netlify.app" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://peteryuen.netlify.app/apple-touch-icon.png')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h3 class="rich-link-card-title">Peter's Second 🧠</h3>
		<p class="rich-link-card-description">
		
		</p>
		<p class="rich-link-href">
		https://peteryuen.netlify.app
		</p>
	</div>
</a></div>

물론 나의 이 블로그도 결과물이다. (그런데, 탬플릿 수정이 약간 있는)  
나의 탬플릿을 활용하고 싶다면 [여기](https://github.com/sleepybee-dev/obsidian-zola-bee)에서 fork 후 READ.ME를 읽고 개인화할 필요가 있다.


## 1. 준비물
Git과 Github에 대한 지식이 필요하다.
Git과 Github이 뭔지 어떻게 쓰는지에 대한 얘기는 다루지 않겠다.


## 2. Github Repository 생성
경험상 블로그로 활용할 vault에 Git을 붙이는 것보다 레파지토리를 Checkout에서 vault로 삼는 게 편하다.
난 [sleepybee-dev-log](https://github.com/sleepybee-dev/sleepybee-dev-log)라는 이름으로 레파지토리를 생성했다.
아직 Checkout 하지 말자.


## 3. netlify Site 생성
netlify는 무료 퍼플리싱 플랫폼이다.
github 레파지토리를 그대로 가져와서 배포해주는 시스템이 잘 돼있다.
무엇보다 무료다.

(1) [netlify](https://www.netlify.com) 가입 & 로그인
(2) Add new site - Import an existing project - Github 클릭 후 내 레파지토리 선택


## 4. Repository에 netlify.toml 파일 만들기
`netlify.toml`는 메타 파일이지만 사실 진입 페이지 UI파일이나 다름없기 때문에 vault에 넣어서 같이 관리해줄 필요가 있는 파일이다. 그래서 Checkout 전에 만든다.

(1) 레파지토리에서 Add File - Create New File - 파일명 `netlify.toml`
(2) obsidian-zola에서 [sample파일](https://github.com/ppeetteerrs/obsidian-zola/blob/main/netlify.example.toml) 내용 복붙
(3) 내 사이트에 맞게 값 수정
	- (필수) **REPO_URL = 내 레파지토리 url**
	- TIMEZONE = "Asia/Seoul"
	- 그밖에 원하는 값 자유롭게 변경


## 5. 최초 배포 (netlify deploy)
netlify.toml이 작성되었다면 netlify에서 이 메타 파일을 한 번은 읽어줘야 한다.
netlify에서 만든 site를 누르면 탭 중에 `Deploys`가 있을 것이다.
우측 중단에 `Trigger deploy - Deploy site`
![[blogguide4.png]]


## 6. Repository Checkout
이제 Checkout하자. 
주의할 점은 다른 PC, 모바일과 동기화를 하려면 iCloud, OneDrive, 구글 드라이브 등 내장되어있는 클라우드 위치에 넣어야 한다는 점이다. obsidian에서 공식 지원하는 건 iCloud, OneDrive 뿐이다.
나의 경우 iCloud를 쓴다.
옵시디언을 설치하면 기본적으로 있는 Obsidian 폴더 안에 레파지토리를 checkout했다.

![[blogguide2.png]]


## 6. Obsidian vault로 열기
'폴더를 보관함으로 열기'를 눌러 방금 checkout한 폴더(sleepybee-dev-log)를 선택한다.
![[blogguide3.png]]

## 7. 글 쓰기
자, 이제 자유롭게 쓰자.
당신이 만든 폴더 구조가 곧 블로그의 메뉴 구조가 될 것이다.
이미지를 붙여넣으면 content 폴더가 생성 될텐데 [obsidian-zola](https://github.com/ppeetteerrs/obsidian-zola)에서 content폴더는 자동으로 invisible해주니 블로그 메뉴엔 보이지 않는다.
글 쓴 후 Git push만 하면 netlify가 레파지토리를 보고 있다가 수정사항에 맞춰 자동으로 사이트를 배포 해준다.


## 8. Obsidian-git 플러그인 사용하기 (Optional)
git command 가 능수능란하다면 필요없겠지만 난 obsidian에서 모든 걸 해결하고 싶기 때문에 git 플러그인도 설치했다.
- obsidian 설정 - 서드파티 플러그인 - 커뮤니티 플러그인 - Obsidian Git 설치 후 Enable
우측에 Source Control이라는 탭이 생겼을 것이다.

![[blogguide5.png]]
Source Control 탭에서 Changes를 +로 스테이지에 올리고 v 버튼으로 커밋 4번째 버튼으로 푸시.
첨부한 이미지 파일 등도 누락되지 않게 Commit, Push 해주어야 한다.

------
이러한 작업을 마친 나는 블로깅을 할 때,
1. 글 쓰기
2. Source Control 에서 Commit & Push

딱 이 작업만으로 발행한다.
폴더 구조를 바꾼다고 블로그의 메뉴 구성을 따로 손 볼 필요도 없다.

이 모든 것이 무료이며, 탁월하다.
노션으로 원툴 블로그하겠다고 애쓰던 나에게 RIP.
여러분도 옵시디언하시고 새 삶을 찾기를 바랍니다.


