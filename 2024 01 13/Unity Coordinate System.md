# Unity 좌표계

---

## 좌표를 나타내는 여러 방법

- **World Point** - 실제 물체가 가지는 좌표
- **Viewport Point -** 카메라 범위에서의 위치 비율
- **Screen Point** - 카메라 범위에서의 상대적 좌표 (해상도와 관련)

## 좌표 전환 방법

```csharp
//Wolrd Point to Viewport Point
Camera.main.WorldToViewportPoint(transform.position)

//World Point to Screen Point
Camera.main.WorldToScreenPoint(transform.position)
```

## 좌표계 사용 예제

```csharp
//클릭한 좌표에 테스트 오브젝트 소환
public GameObject testObj;
private Update()
{
	//left click
	if(Input.GetMouseButtonDown(0)){
		GameObject tempObj = Instantiate(testObj);
		Vector3 tempV = Camera.main.ScreenToWorldPoint(Input.mousePosition);
		tempV.z = 0f;
		tempObj.transform.position = tempV;
	}
}
```

*이렇게 하는 이유는 그냥 Input.mousePosition으로 했을시에는 소환되는 위치가 이상하기 때문이다.