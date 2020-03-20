### ver1 각도로 회전하기

 eulerAngles => 주의 증감 연산 사용하면 안됨 360도 넘어가면 이상



```cs
_yAngle += Time.deltaTime * _speed;    

// 절대 회전 값
transform.eulerAngles = new Vector3(0.0f,_yAngle,0.0f);
```



### ver2 Rotate 사용

특정 축을 기준으로 얼만큼 회전하고 싶다.

```
// +- delte값을 특정 x,y,z 축으로 회전하는 값
 transform.Rotate(new Vector3(0.0f, Time.deltaTime * 100.0f, 0.0f));
```



### ver3 쿼터니언 이용 (짐벌락 현상 때문에)

`Quaternion` : transform.rotation 보면 쿼더니언이고, x,y,z,w 를 가지는데, vector3를 안갖고 4개를 갖는 이유는 짐벌락 현상때문이다.

https://www.youtube.com/watch?v=zc8b2Jo7mno

```cs
 transform.rotation = Quaternion.Euler(new Vector3(0.0f, _yAngle, 0.0f));
```



### ver4 가는 방향 바라보기

딱딱 끊기게 이동한다.

```cs
원하는 방향 넣기
transform.rotation = Quaternion.LookRotation(Vector3.forward);
```



### ver 5 부드럽게 방향 바라보기

```cs
블랜딩이랑 비슷 
    Quaternion.Slerp(현재 , 목적지 , [0~1] 목적지 비율)  // 1.0은 위랑 똑같다
transform.rotation = Quaternion.Slerp(transform.rotation, Quaternion.LookRotation(Vector3.forward) , 0.2f);

```

