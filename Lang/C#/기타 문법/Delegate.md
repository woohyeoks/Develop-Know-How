### 델리게이트

* 단점 : 델리게이트는 어디서나 사용이 가능하다... 그래서 이를 보완한 것이 Event입니다.



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



### 제네릭 활용

좀 더 범용적인 델리게이트 사용하기 위해 사용 됩니다.



* 사용 예

```cs
 delegate Return MyFunc<T,Return>(T item);

 static Item FindItem(MyFunc<Item,bool> selector)
 {
     foreach (Item item in _items)
     {
         if (selector(item))
         {
             return item;
         }
     }
     return null;
 }

MyFunc<Item, bool> selector = (Item item) => { return item.ItemType == ItemType.Weapon; };

Item item = FindItem(selector);
Console.WriteLine(selector);

```



위 사용 예는 리턴 이나 변수 개수에는 유연하지 않습니다. 그래서 이를 추가해줘야 합니다. 

직접 만들지 않아도, 이미 만들어진 애들이 존재합니다.



* Func : 반환 타입이 있을 경우 
* Action : 반환 타입이 없으면  







