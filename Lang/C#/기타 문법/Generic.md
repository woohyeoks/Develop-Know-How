### Generic (일반화)

클래스나 메소드 이용할 때 자료형에 구애받지 않고 사용할 수 있습니다.



`필요한 상황` : 자료구조 만들 때 자료형에 구분이 필요합니다. (Int, float )

`Object 이용` : object이용하면 자료형 변환 가능은 하나, 박싱 언박싱 작업이 이뤄지면서 성능이 안 좋습니다.

object는 힙영역 , 기본 자료형은 참조형이라 변환가정 복잡



Generic 클래스, 메소드 이용

```
Class A<T>
void Test<T>(T input)

조건 추가
class A<T> : where T: struct // 값형식
class A<T> : where T: class // 참조형식
class A<T> : where T: Monster // 상속
class A<T> : where T: new() // 기본생성자 있어야 한다.
```



 

 