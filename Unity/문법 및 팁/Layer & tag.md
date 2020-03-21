### Layer

이제 어떤 연산을 할 때 내가 연산하고 싶은 애들만 연산할 수 있게 해줍니다.

Layer 추가 후 등록해보자!!



### 활용법

```cs
 // 비트 플래그 이용
 // 기본적으로 32비트 사용하고 있다...

 int mask = (1 << 8) | (1 << 9); // Monster , Wall 레이어 키기
 Physics.Raycast(ray, out hit, 100.0f ,mask))  // 레이어에 해당하는 객체만 연산 처리
     
     
// 비트 플래그 대체하는 방법
 LayerMask mask = LayerMask.GetMask("Monster") | LayerMask.GetMask("Wall"); // 묵시적으로 int 반환
```





### Tag

옷에 태그 붙이는 것 처럼 추가적인 정보를 남기는 것이다.

```cs
GameObject.FindGameObjectWithTag(TagName); // 태그로 오브젝트 찾기

Debug.Log($"RayCast Camera @ {hit.collider.gameObject.tag}"); // 충돌한 객체 태그 이름
```

