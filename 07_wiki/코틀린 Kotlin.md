## 자바보다 뭐가 더 나은가?
- Nullable
	- NullSafety를 올릴 수 있다.
- 모든 타입이 클래스 타입
	- Nullable을 위해 기본형 타입도 클래스다.
- Functional Programing
	- OOP, FP 모두 지원
	- 함수가 1급 객체
	- 고차 함수로 사용 가능
- 타입 추론 (사실 난 선호하진 않는다.)

## Kotlin extension
https://kotlinlang.org/docs/extensions.html

> Kotlin은 클래스에서 상속하거나 Decorator와 같은 디자인 패턴을 사용하지 않고도 새로운 기능으로 클래스나 인터페이스를 **확장**할 수 있는 기능을 제공합니다. 이것은 Extension이라는 특별한 선언을 통해 이루어진다.
   예를 들어, 수정할 수 없는 타사 라이브러리에서 클래스나 인터페이스에 대한 새로운 함수를 작성할 수 있습니다. 이러한 함수는 원래 클래스의 메서드인 것처럼 일반적인 방식으로 호출될 수 있다. 이 메커니즘은 `extension function`이라고 불린다. 기존 클래스에 대한 새 속성을 정의할 수 있는 `extension property` 들도 있다.

https://medium.com/til-kotlin-ko/kotlin의-extension은-어떻게-동작하는가-part-1-7badafa7524a

