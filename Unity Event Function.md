# Unity 이벤트 함수

---

## 에디터 관련

### Reset 함수

- 에디터에서 처음 오브젝트에 연결될 때
- Reset 명령을 실행했을때 호출 (인스펙터에서 컴포넌트의 Reset버튼 그거에 호출 )

## 실행 관련

### Awake 함수

- Start함수의 전에 호출
- 활성화 직후에 호출
- 씬이 시작할 때에 비활성화 상태일시, 활성화 되기 전에 호출 X

### OnEnable 함수

- 씬 시작할 때에 활성화 상태일시 Awake 이후 Start 이전에 호출
- 활성화 직후에 호출

### Start 함수

- 컴포넌트가 실행될 때
- Awake 함수와 OnEnable 함수 이후에 호출

## 충돌 관련

### OnCollisionXX2D 함수 - 물리적 충돌 O (매개변수 collision2D)

둘 모두 콜라이더, 둘 중 하나라도 리지드바디

- **OnCollisionEnter2D** - 충돌 시 호출
- **OnCollisionStay2D** - 충돌 중 호출
- **OnCollisionExit2D** - 충돌이 끝날 때 호출

### OnTriggerXX2D 함수 - 물리적 충돌 X (매개변수 colliider2D)

둘 모두 콜라이더, 둘 중 하나라도 리지드바디 + 콜라이더에 IsTrigger 체크

- **OnTriggerEnter2D** - 트리거 충돌 시 호출
- **OnTriggerStay2D** - 트리거 충돌 중 호출
- **OnTriggerExit2D** - 트리거 충돌이 끝날 때 호출

## 마우스 관련

### OnMouseXX 함수

콜라이더가 있어야 호출, 터치도 됨

- OnMouseDown - 클릭 시 호출
- OnMouseDrag - 클릭 중 호출
- OnMouseUp - 클릭이 끝날 때 호출

## 반복 관련

### FixedUpdate 함수 - 물리적

- 일정시간마다 호출 (Edit - Project Settings - Time에서 Fixed Timestep으로 조정 가능)

### Update 함수 - 게임 로직

- 매 프레임마다 호출 (프레임이기에 컴퓨터마다 다르게 작용함)

### LateUpdate 함수 - 카메라 이동에 보통 사용

- Update 후에 매 프레임마다 호출

## 카메라 관련