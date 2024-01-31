# Singleton (디자인패턴)

---

# 싱글톤 오브젝트

여러 매니저류와 같이 게임 내에 유일한 독립체로 존재하는 오브젝트

# 싱글톤 특징

1. 클래스의 인스턴스가 하나만 생성되야 함
2. 어디서든지 그 인스턴스에 접근 가능

# 기본 사용법

```csharp
public class TestManager : MonoBehaviour {
	
		public static TestManager instance;
	
		void Awake(){
				if (instance != null)
						Destroy(this.gameObject);
				else
						instance = this;
						//DontDestroyOnLoad(gameObject);
				}
}//사람마다 구현하는 방식은 다를 수 있음
```

싱글톤이지만 DontDestroyOnLoad를 안쓸 수 도 있음

DontDestroyOnLoad는 모든 씬에서 필요한 오브젝트에만

# 추가적인 사용법

```csharp
public class TestManager : MonoBehaviour {
	private static TestManager instance;
	public static TestManager Instance{
		get {
				if (instance == null) {		
						GameObject tempTM = new GameObject ("GameManager");
						instance = tempGM.AddComponent<TestManager>();
						//DontDestroyOnLoad (tempTM);
				}
				return instance
	}	
}
```

이러한 방식은 Awake로 생성을 해도 다른 오브젝트의 Awake에서 호출이 되는경우 문제가 생길 수 있기에 get할때에 생성이 되도록 코드를 짬 + instance가 public으로 있을 때에 수정 될 수도 있으니까 아무래도