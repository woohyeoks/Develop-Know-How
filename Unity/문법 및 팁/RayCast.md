### RayCasting

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

