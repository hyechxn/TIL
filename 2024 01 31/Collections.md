# 컬렉션

---

데이터의 모음, 자료구조

# List

배열처럼 선형구조로 이루어진 컬렉션.

하지만 배열과는 다르게 **크기가 동적임** 

```csharp
//기본적인 생성 및 사용법
public class CollectionsTest : MonoBehaviour {
	public List<string> strList; //<>안에 타입 지정해서 선언

	void Start () {
		strList = new List<string>(); //리스트 생성
		
		strList.Add("A");//값 추가 인자에는 타입에 맞는 값을 넣어줌
		strList.Add("B");//가장 마지막 인덱스에 추가 됨

		Debug.Log(strList.Count);//2출력
		Debug.Log(strList[0]);//A출력

		//strList.Remove("a");//인자로 들어온 값과 같은 요소 삭제
		strList.RemoveAt(0);//인자로 들어온 인덱스의 요소 삭제
		//strList.RemoveAll();//요소 전체 삭제
		Debug.Log(strList[0]);//B출력

		strList.Insert(0, "C");//1번째 인자값의 인덱스에 2번째 인자값 삽입
		Debug.Log(strList[0])//C출력
	}
}
```

```csharp
//사용예제 이걸 응용해서 인벤토리같은거 만들 수 있음
public class CollectionsPrac : MonoBehaviour {
	List<string> itemList = new List<string>();

	void Start () {
		itemList.Add("A");
		itemList.Add("B");
		itemList.Add("C");

		//foreach(string itemName in itemList)
		//{
		//		Debug.Log(itemName);	
		//}
		for (int i = 0; i < itemList.Count; i++)
		{
				Debug.Log(itemList[i]);
		}
	}
}
```

# Stack

**한 쪽 끝에서만** 자료를 넣거나 뺄 수 있는 컬렉션 LIFO (Last in First Out) 

- 일종의 타워라고 생각
- 인덱스 없이 한 쪽 끝에서만 할 수 있음

```csharp
public class CollectionsTest : MonoBehaviour {
		public Stack<string> strStack;

		void Start() {
				strStack = new Stack<string>(); 

				strStack.Push("A");//현재 스택 상태 A
				strStack.Push("B");//현재 스택 상태 B A
				strStack.Push("C");//현재 스택 상태 C B A

				Debug.Log(strStack.Pop());// C출력, 현재 스택 상태 B A
				Debug.Log(strStack.Count);// 2출력
				
				strStack.Clear();//현재 스택 상태 (비어있음)
		} 
}
```

### 사용처

- 되돌리기 기능 - State를 쌓아서 되돌리기 할때 마지막 State를 불러오는 기능
- 오브젝트 풀링 - 오브젝트를 준비해놓고 사용할 때에 쓰일 수 있음

# 딕셔너리

키(Key)와 값(Value)을 가진 컬렉션

키나 값에는 어떤 타입이든 가능하다.

List가 인덱스를 통해 요소에 접근한다면, Dictionary는 키로 요소에 접근한다.

```csharp
public class CollectionsTest : MonoBehaviour {
		public Dictionary<string, int> testDictionary;

		void Start() {
				testDictionary = new Dictionary<string, int>();, //<>속의 값은 1번째는 키의 타입 2번째는 값의 타입을 의미

				testDictionary.Add("High Score", 10000);
				Debug.Log("High Score : " + testDictionary["High Score"]) // 리스트와 유사하게 대괄호[]를 사용하여 요소에 접근한다
				//출력 High Score : 10000
		}
}
```

### 사용처

- 스킬 정보 가져오기 - 스킬이름을 키로 둬서 그거에 맞는 데미지 등의 값을 가져오는데 사용
- 텍스트 파일 읽기 - 딕셔너리를 이용하여 엑셀 파일의 정보를 읽어서 사용