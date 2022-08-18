저장소 액세스 정책 변경
--
Android 10 이상을 타겟팅하는 기기부터 외부 저장소 루트는 아예 사용할 수가 없고 몇 가지 허용된 공간만 사용 가능하다. 또, 사용 가능한 외부 저장소에 액세스할 경우에 SAF나 MediaStore를 사용하도록 강제되었다.


<div class="rich-link-card-container"><a class="rich-link-card" href="https://developer.android.com/training/data-storage/shared/media?hl=ko" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://developer.android.com/images/social/android-developers.png?hl=ko')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h3 class="rich-link-card-title">공유 저장소의 미디어 파일에 액세스  |  Android 개발자  |  Android Developers</h3>
		<p class="rich-link-card-description">
		 ---
		</p>
		<p class="rich-link-href">
		https://developer.android.com/training/data-storage/shared/media?hl=ko
		</p>
	</div>
</a></div>

이 저장소 정책은 한참 됐지만 MediaRecorder에서 약간 헤맸는데 솔루션이 있는 웹페이지가 없길래 정리해 둔다.


MediaRecorder
---
    
<div class="rich-link-card-container"><a class="rich-link-card" href="https://developer.android.com/guide/topics/media/mediarecorder?hl=ko" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://developer.android.com/images/social/android-developers.png?hl=ko')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h3 class="rich-link-card-title">MediaRecorder 개요  |  Android 개발자  |  Android Developers</h3>
		<p class="rich-link-card-description">
		---
		</p>
		<p class="rich-link-href">
		https://developer.android.com/guide/topics/media/mediarecorder?hl=ko
		</p>
	</div>
</a></div>
시시콜콜한 것들은 도큐먼트에 잘 나와 있다.



외부저장소에 저장하기
---
```java
recorder = new MediaRecorder(); recorder.setAudioSource(MediaRecorder.AudioSource.MIC); recorder.setOutputFormat(MediaRecorder.OutputFormat.THREE_GPP); recorder.setOutputFile(fileName);
```

여기서 setOutputFile의 fileName은 저장하고자 하는 파일명의 full path만 사용하면 됐다.
이 함수는 내부 저장소(data/data/{app_name})에서는 고대로 사용할 수 있다.
하지만 MediaStore로 접근해야하는 외부 저장소를 사용할 때에는 더이상 String으로된 path로 접근할 수가 없다.

그렇다면 outputFile의 Path를 어떻게 지정할 수 있을까? 
setOutputFile은 FileDescriptor를 파라미터로 갖는 것이 있는데 이를 이용한다.

![[mediarecorder.png]]


- 실수 예제
 
```java
FileDescriptor getFileDescriptor(){
	ContentValues values = new ContentValues(); 
	values.put(MediaStore.Video.Media.DISPLAY_NAME, "filename.MP4"); 
	values.put(MediaStore.Video.Media.MIME_TYPE, "video/*");
	ContentResolver resolver = getContentResolver();
	Uri item = contentResolver.insert(MediaStore.Video.Media.EXTERNAL_CONTENT_URI, values);
	ParcelFileDescriptor fileDescriptor = null;
	try {
		fileDescriptor = resolver.openFileDescriptor(item, "w");
		return fileDescriptor.getFileDescriptor();
	} catch (FileNotFoundException e) {
		e.printStackTrace();
	}
	return null;
}
```

이렇게 FileDescriptor를 얻으면?

안된다.

내부저장소는 full path만 넣으면 파일이 미리 만들어져 있지 않아도 그 위치에 그 파일명으로 write가 되었던 반면, 이렇게 할 때엔 내가 임시 파일을 생성해 두어야 한다.

여기서 기존 코드랑 꼬였어서 조금 헤맸던 거였다.

- 정상 예제
```java
FileDescriptor getFileDescriptor() {
	ContentValues values = new ContentValues(); 
	values.put(MediaStore.Video.Media.DISPLAY_NAME, "filename.MP4"); 
	values.put(MediaStore.Video.Media.MIME_TYPE, "video/*");
	if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.Q) { 
		// 해당 파일을 다른 앱에서 접근하는 것을 막는 플래그.
		values.put(MediaStore.Video.Media.IS_PENDING, 1);
	}
	ContentResolver resolver = getContentResolver();
	Uri item = contentResolver.insert(MediaStore.Video.Media.EXTERNAL_CONTENT_URI, values);
	ParcelFileDescriptor fileDescriptor = null;
	try {
		// file write 추가 
		fileDescriptor = resolver.openFileDescriptor(item, "w");
		if (fileDescriptor != null) {
		// 빈 파일 생성
		String str = "hello";
		byte[] strToByte = str.getBytes();
		FileOutputStream fos = new FileOutputStream(fileDescriptor.getFileDescriptor());
		fos.write(strToByte);
		fos.close();
		if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.Q) {
			values.clear();
			// 해당 파일을 다른 앱에서 접근하는 것을 다시 허용.
			values.put(MediaStore.Images.Media.IS_PENDING, 0); 
			contentResolver.update(item, values, null, null);
		}
		return fileDescriptor.getFileDescriptor();
	} catch (FileNotFoundException e) {
		e.printStackTrace();
	}
	return null;
}
```

Recording이 정상적으로 되는 것을 확인할 수 있다.

서치하다가 못 찾고 궁리해낸 방법이라 제대로 된 솔루션이 따로 있을 수 있다.
지적은 언제나 환영.

\+ 이전 글을 옵시디언으로 옮겼더니 댓글 기능이 없어 지적을 못 받는다. netlify로 deploy된 사이트가 구글 검색에 잘 안 걸린다고 해서 방문객이 없을 것 같지만, 깃헙 블로그 때처럼 Utterances를 붙일 수 있지 않을까 검토해 볼 예정.


