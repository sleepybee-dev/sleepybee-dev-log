[미디엄 :  GetX는 Flutter의 앱의 성능과 품질을 저하시켰다](https://honor-driven.dev/flutter-tweet-1-getx는-flutter의-앱의-성능과-품질을-저하시켰다-6de5335e8cb6)

21년 7월 미디엄 글인데 GetX에 대한 네거티브가 트위터에서 논의되고 있다는 것이었다.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">I wish I could turn back time to prevent GetX from being created.<br><br>It is not only bloated, has questionable architecture decisions but misleading.<br><br>I genuinely believe it has decreased performance &amp; quality of Flutter apps using it.<br><br>Lesson learned: do not try to do *everything*.</p>&mdash; creativecreatorormaybenot (@creativemaybeno) <a href="https://twitter.com/creativemaybeno/status/1418148816444923906?ref_src=twsrc%5Etfw">July 22, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

 시발점은 한 개발자의 "**시간을 되돌려 GetX가 만들어지는 걸 막고 싶다**"는 트윗.
 
>GetX는 과잉되어 있으며 아키텍쳐가 의심스럽고 오해를 만든다.
>이걸 사용하는 것이 앱의 성능과 품질을 저하시킨다고 확신한다.
>
>교훈: 이걸로 모든 것을 하려고 하지 말 것.
>
>@creativemaybeno

이에 동조하는 많은 리트윗들이 있었다.
내가 마음 한 켠에서 미심쩍어 하던 것들이 트위터 타래에 서술되어 있어서 놀랍고 반가웠다. 

- 상태관리를 GetX에 의존해야 하는 것에 대한 불안감. 
- 그 패키지가 구글(Flutter)에서 관리되고 있지 않는 것에 대한 불신.
- Context를 쥐고 있는 것에 대한 찝찝함.

실제로 성능 저하를 일으키는 모양이다. (사실 나는 GetX를 걷어내도 나이스한 퍼포먼스를 만들지 못해 체감하질 못했다.)
그리고 일정 구간의 버전에서 심각한 버그가 있었던 모양.

그럼에도 불구하고 **개발이 용이하니까** 다들 사용하고 있는 모양이다.
역시 쉬운 것이 좋은 것은 아니다.
물론 어려운 것이 좋은 것도 아니지만.



