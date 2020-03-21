### 델리게이트

델리게이트는 대행자  즉 콜백으로 처리하는 방식이다.

함수자체를 인자로 넘겨줘서 처리하는 방식입니다.



예전에는 직관적이고 순차적으로 진행했다면 

델리게이트는 비서가 연락처와 용건을 남기고 호출하는 방식이라고 생각하면 편합니다.,



### 사용 예

```cs
delegate int OnClicked(); // 형식 
// delegate -> 형식은 형식인데, 함수 자체를 인자로 넘겨주는 형식

// 반환 : int 입력  : void OnClicked 이 delegate 형식의 이름이다.

static void ButtonPressed(OnClicked clickedFunction)
{
    // 함수를 호출();
    clickedFunction();
} 


static int TestDelegate()
{
    Console.WriteLine("Hello Delegate");
    return 0;
} 
static int TestDelegate2()
{
    Console.WriteLine("Hello Delegate2");
    return 0;
}
static void Main(string[] args)
{

    OnClicked clicked = new OnClicked(TestDelegate);
    clicked += TestDelegate2;
    //  clicked();


    // Delegate (대리자)
    ButtonPressed(TestDelegate);
}
```



