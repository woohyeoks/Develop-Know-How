### RayCasting 

* 주의 : 레이캐스팅은 부하가 심하니, 레이어를 이용해서 연산 필요한 객체만 레이캐스팅 하자!!

레이케스팅은 레이저 쏘는거라 생각하면 된다.

우리가 스크린 (2D) 에서 클릭시 3D 오브젝트 선택되는 피킹 이나, 

FPS 충돌 , 카메라 충돌 처리 사용할 때 주로 사용됩니다.



### 사용 예

```cs
바라보는 방향으로 쏘기 위해서는 
로컬 좌표 -> 월드 좌표 변환 필요하다
Vector3 look = transform.TransformDirection(Vector3.forward); 

개발자가 눈으로 직접 확인하기 위해 쏴본다.
Debug.DrawRay(transform.position + Vector3.up, look * 10, Color.red);

// 레이 충돌 처리
RaycastHit hit;
if (Physics.Raycast(transform.position + Vector3.up, look, out hit, 10))
{
    Debug.Log($"RayCast {hit.collider.gameObject.name}!");
}



// 다수 충돌 처리
RaycastHit[] hits;
hits = Physics.RaycastAll(transform.position + Vector3.up, look * 10, 10);


foreach (RaycastHit hit in hits)
{
    Debug.Log($"RayCast {hit.collider.gameObject.name}!");
}      
```







### 피킹

1. Ver1

```cs
클릭한 지점 월드 좌표 구하기
Vector3 mousePos = Camera.main.ScreenToWorldPoint(new Vector3(Input.mousePosition.x, Input.mousePosition.y,
               Camera.main.nearClipPlane));

// 카메라에서 클릭한 지점에 방향 구하기 
Vector3 dir = mousePos - Camera.main.transform.position;
dir = dir.normalized;

// 확인
Debug.DrawRay(Camera.main.transform.position, dir * 100.0f, Color.red, 1.0f);

//레이 캐스팅
RaycastHit hit;
if (Physics.Raycast(Camera.main.transform.position, dir, out hit , 100.0f))
{
    Debug.Log($"RayCast Camera @ {hit.collider.gameObject.name}");
}
```

2. Ver2 => Ver1은 스텝바이 스텝으로 진행한 것이고, 방향 구하는 함수 이용

```cs
Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
           Debug.DrawRay(Camera.main.transform.position, ray.direction * 100.0f, Color.red, 1.0f);
RaycastHit hit;
if ( Physics.Raycast(ray, out hit, 100.0f ))
{
    Debug.Log($"RayCast Camera @ {hit.collider.gameObject.name}");
}

```



