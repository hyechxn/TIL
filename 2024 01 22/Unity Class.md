# 클래스

---

클래스 내에 중복되는 불필요한 코드 발생시 해결해야함.

# 상속

어떤 한 클래스를 포함한 다른 클래스를 만드는 것.

상속을 하게되면 : 를 기준으로 오른쪽이 부모클래스 왼쪽이 자식클래스인데

부모클래스에서 public 혹은 protected로 선언된 멤버들을 자식클래스로 사용이 가능하다.

### 

![inheritance](/2024%2001%2022/Image/Inheritance.png)

Person은 Babe와 Worker의 부모클래스이다.

즉 모든 Babe와 Worker는 Person이다.

**우리가 사용하는 스크립트는 보통 MonoBehavior을 상속하여 이렇게 구성된다.**

![ObjectInheritance](/2024%2001%2022/Image/ObjectInheritance.png)

*이렇게 사용해야 유니티 오브젝트의 컴포넌트로써 작동을 할 수 있다.

> 위 사진에 대한 간단한 정리
    
     Object에는 ToString, Destroy등의 함수 존재
    
     Component에는 gameObject, tranform, tag 등의 값 존재
    
     Behavior에는 Enable 값
    
     MonoBehavior에는 Start, Update등의 이벤트 함수 존재
    

# 다형성

같은 이름의 코드가 다른 일을 하는 것

### Virtual 과 Override 키워드

부모클래스에서 상속받은 함수를 자식클래스의 이름이 같은 함수에서 재정의 하는 것

- 재정의 받을 최상위 부모클래스의 함수에 virtual
- 재정의 할 자식클래스의  함수에 override

이렇게 하게되면 부모클래스의 함수의 기능은 잃게 된다.

자식에서 부모의 함수 기능에 추가적인 기능을 넣고 싶을때

base.함수명 사용하여 작동시키고 자기꺼 추가적인 코드 작성

# 프로퍼티

변수 값의 범위를 제한하려고 할때.

그냥 하게되면 매번 귀찮게 추가적인 코드를 작성해줘야 한다.

Ex) score = MathF.Clamp(value, a, b)이렇게 value의 값을 a와 b사이로 score에 집어넣는거

이럴때 사용하는게 프로퍼티다.

```csharp
//기본적인 사용법
public int score = 0;
public int Score {

	get {//값을 가져올 때
		return score;
	}
	set {//값을 설정할 때
		score = value; //여기서 value는 입력된 값
	}
}
```

### 추가적인 사용 예시

### 텍스트UI와 함께 사용

```csharp
//이런식으로 텍스트를 바로바로 바꿔주는 것도 가능
public class ScoreManager : MonoBehaviour{
	public text scoreText;
	private int score = 0;
	public int Score {
	
		get {
			return score;
		}
		set {
			score = value;
			scoreText.text = value.ToString();
		}
	}
}
```

```csharp
public class Click : MonoBehaviour {
	public int score;
	public ScoreManager manager;
	private void OnMouseDown()
	{
		manager.Score += score; 
	}
}
```

이렇게 쓰지 않고 그냥 썼다면 값을 추가할때마다 text를 변경해 줘야 함.