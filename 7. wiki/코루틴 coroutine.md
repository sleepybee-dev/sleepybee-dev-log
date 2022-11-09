비동기적으로 실행되는 코드를 간소화하기 위해 Android에서 사용할 수 있는 동시 설계 패턴.

- 경량 : 단일 스레드에서 많은 코루틴을 실행할 수 있다. 정지
- 메모리 누수 감소
- 기본으로 제공되는 취소 지원
- Jetpack 통합

### 장기 실행 작업 관리
- `suspend` : 현재 코루틴 실행을 일시중지하고 모든 로컬 변수를 저장
- `resume` : 정기된 위치부터 정지된 코루틴을 계속 실행

### 기본 안전을 위해 코루틴 사용
디스패처를 사용하여 스레드 확인.
코루틴은 자체적으로 정지될 수 있으며 디스패처는 코루틴 재개를 담당.

- **Dispatchers.Main** : 기본 Android 스레드. UI와 상호작용하고 빠른 작업을 실행하기 위해서만 사용해야 함.
- **Dispatchers.IO** : 기본 스레드 외부에서 디스크 또는 네트워크 I/O를 실행하도록 최적화. 
- **Dispatchers.Default** : CPU를 많이 사용하는 작업을 기본 스레드 외부에서 실행하도록 최적화. 예) 목록 정렬, JSON 파싱

### withContext()의 성능
상응하는 콜백 기반 구현에 비해 오버헤드를 추가하지 않는다. 일부 상황에서는 능가한다. withContext()를 여러 번 사용하더라도 동일한 디스패처에 유지되고 스레드가 전환되지 않는다. 가능한 한 스레드 전환을 방지하도록 `Dispatchers.Default`와 `Dispatchers.IO` 간의 전환을 최적화.

### 코루틴 시작
- `launch` : 새 코루틴을 시작하고 결과를 반환하지 않는다. '실행 후 삭제' 작업.
- `async` : 새 코루틴을 시작하고  `await`라는 정지 함수로 결과를 반환하도록 허용. 다른 코루틴 내부에서만 사용하거나 정지 함수 내에서 병렬 분해를 실행할 때 사용. [!] await 호출의 일부로 예외를 발생. 일반 함수는 `await`를 호출할 수 없으므로 자동으로 예외 삭제하여 기록되지 않는다.

### 병렬 분해
`suspend` 함수 내에서 시작되는 모든 코루틴은 함수가 반환되면 중지되어야 함. 반환 전에 `await` 를 호출해 완료를 보장해야 할 수 있음. 

### CoroutineScope
`launch` 또는 `async`를 사용하여 만든 코루틴을 추적한다. 진행 중인 작업(실행 중인 코루틴)은 언제든지 `scope.cancel()`을 호출하여 취소 가능.
KTX 라이브러리는 특정 수명 주기 클래스에 자체 CoroutineScope를 제공. (viewModelScope, lifecycleScope 등)


## References
- https://developer.android.com/kotlin/coroutines/coroutines-adv?hl=ko
- 


