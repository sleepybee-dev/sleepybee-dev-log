## 커스텀뷰란
[[안드로이드 Android]]에서 기본적으로 제공하는 위젯들(TextView, Button, EditText, ListView 등)이 아니라 내 필요에 맞춰서 만든 View를 말한다.

## 커스텀뷰를 만드는 두 가지 방법
1. 안드로이드 제공 UI를 확장한다.
```Java
class TaggableTextView extends TextView {
 ...
}
```

2. 가장 기본적인 View 또는 ViewGroup에서부터 확장해서 직접 구현한다.
```Java
class TaggableTextView extends View {
 ...
}
```

1번은 느슨한 의미에서의 커스텀뷰이고 2번이 타이트한 의미에서의 커스텀뷰라고 할 수 있겠다.
어찌보면 당연하지만 2번은 성능적으로 상당히 이득을 볼 수 있다. 필요한 기능만 컴팩트하게 직접적으로 구현하기 때문이다. 아주 단순해 보이는 TextView도 내부적으로 보면 상당히 많은 것들이 차려져 있다.

요즘 디바이스 하드웨어가 워낙 좋아서 체감하기 어려울 수 있으나 난 최근에 마시멜로 기기에서 엄청난 성능 상승을 경험했다!
여러 Child View가 동적으로 붙은 UI를 하나의 View로 커스텀하여 구현했더니 딜레이가 4분의 1이 되었다. 난 이 이후로 커스텀뷰를 찬양하기로 했고 앞으로 View를 구현할 때 웬만하면 onDraw에서 그릴 생각이다.(금사빠)

이제부터 이 글의 '커스텀뷰'는 2번의 커스텀뷰를 지칭한다.

## View의 LifeCycle
![[Pasted image 20221125175757.png]]
개발자가 override에서 쓰는 건 on이 붙어 있는 것들이라고 보면 된다.
- onAttachedToWindow() : View가 Window에 연결되면 호출. 
- onMeasure() : View의 크기를 측정하는 단계
- onLayout() : View의 위치와 크기를 할당하는 단계
- onDraw() : View를 그리는 단계


### 무조건 쓰는 팁
1. `drawText()`를 쓸 땐 `Paint`에 antiAlias를 적용하지 않으면 글자가 계단현상을 갖고 그려진다.
```Java
paintText = new Paint(Paint.LINEAR_TEXT_FLAG | Paint.ANTI_ALIAS_FLAG);
```

2. 글자를 가로 길이를 알고 싶을 때
```Java
paintText.measureText(text);
```

3. `Paint`나 `Rect`는 constructor에서 initialize하자.
> Avoid object allocations during draw/layout operations (preallocate and reuse instead)

Paint를 쓰는 onDraw에서 무심코 `new Paint`를 시도하였더니 이렇게 경고가 나온다.
말 그대로 onDraw나 onLayout에서 객체를 할당하지 말라는 경고.
constructor에서 init해주면 된다.
```Java
public TaggableTextView(Context context, String text) {  
    super(context);
    paintText = new Paint(Paint.LINEAR_TEXT_FLAG | Paint.ANTI_ALIAS_FLAG);  
    rect = new Rect();  
}
```

4. WRAP_CONTENT가 안 먹힌다?
이렇게 만든 View에 LayoutParams을 set하려고 할 때 wrap_content가 안 먹을 수가 있다.
View의 LifeCycle을 떠올리면 layout이 draw보다 앞인 것을 알 수 있다. 내가 draw에 뭘 얼마나 그렸는지는 Layout단계에서는 모르는 것이다.
따라서 Layout 전 단계(Measure)에서 직접적으로 Param을 잡아줘야 한다.
```Java
@Override  
protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {  
    super.onMeasure(widthMeasureSpec, heightMeasureSpec);  
    setMeasuredDimension(widthMeasureSpec, dpToPx(56));  
}
```

아니면 setLayoutParams() 후에 requestLayout()로 새로고침하는 방법도 있겠다.
(requestLayout으로 wrap_content가 먹히는지 실제로 해보진 않았지만 View를 올릴 때마다 onDraw를 두 번 타게 되므로 피할 수 있으면 피하는 게 맞다고 생각한다.)



#안드로이드
