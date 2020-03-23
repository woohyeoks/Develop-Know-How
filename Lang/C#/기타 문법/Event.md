### 이벤트

델리게이트와 유사하지만  델리게이트는 어디서든 호출가능 한데, 이를 보완한 것이 이벤트 입니다.



이벤트 호출 후 관심있는 사람이 구독 신청 후 이벤트 발생시 구독자에게 알리는 구조 입니다.



### 사용 예

```cs
static void OnInputTest()
{
    Console.WriteLine("Input Received!!");
}

static void Main(string[] args)
{

    InputMnager inputManager = new InputMnager();
    inputManager.InputKey += OnInputTest; // 구독 신청


    while (true)
    {
        inputManager.Update(); // 키 입력시 구독 신청한 함수 호출
    }
    
     //inputManager.InputKey(); // 호출 불가 델리게이트는 가능
}

 class InputMnager
    {
        public delegate void OnInputKey();
        public event OnInputKey InputKey;// 앞에 이벤트 쓰면된다.

        // 사용자가 마우스 키보드 입력하는 것을 알려주는 역활
        public void Update()
        {
            if (Console.KeyAvailable == false)
                return;

            ConsoleKeyInfo info = Console.ReadKey();
            if (info.Key == ConsoleKey.A)
            {
                // 모두한테 알려준다.
                // 여기다 뭔 코드를 넣으면 비효율 적  
                // 의존성 높여서 좋은 구조가 아니다... 콜백 방식 쓰자.
                InputKey();
            }
        }
    }

```

