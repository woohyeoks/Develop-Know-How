```cs
struct MyVector
{
    public float x;
    public float y;
    public float z;


    // 거리 (크기) 구할 때 사용 
    public float magnitude
    {
        // 피타고라스 정리
        get { return Mathf.Sqrt(x*x + y*y + z*z); }
    }

    // 순수 방향 구할 때
    public MyVector normalized {
        get { return new MyVector(x / magnitude , y/magnitude , z/magnitude);}
    }

    public MyVector(float x, float y, float z)
    {
        this.x = x;
        this.y = y;
        this.z = z;
    }
    
    public static MyVector operator +(MyVector a, MyVector b)
    {
        return new MyVector(a.x + b.x, a.y + b.y, a.z + b.z);
    }
    
    public static MyVector operator -(MyVector a, MyVector b)
    {
        return new MyVector(a.x - b.x, a.y - b.y, a.z - b.z);
    }
    
    public static MyVector operator *(MyVector a, float b)
    {
        return new MyVector(a.x * b, a.y * b, a.z * b);
    }
}
```

```cs
 MyVector to = new MyVector(10.0f, 0.0f , 0.0f);
        MyVector from = new MyVector(5.0f , 10.0f , 0.0f);

        MyVector dir = to - from; // (5.0f , 0.0f , 0.0f)
        dir = dir.normalized;

        MyVector newPos = from + dir * _speed;
        // 방향 벡터
        // 1. 거리 (크기) 5 magnitude
        // 2. 실제 방향 -> normalized
```

