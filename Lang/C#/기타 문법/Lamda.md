### 람다

무명함수라고 보면 됩니다.



사용 예 : 가상의 인벤토리 만들 때 등급 별 , 무기 별 찾는데, 함수를 늘려가면서 쓰면 너무 많아서 이를 개선하기 위해 델리게이트를 쓰는데, 이 델리게이트 문법이 조금 복잡했는지 이를 개선한게 람다식이다.



```cs
// 람다식
Item item = FindItem((Item item) => {return item.ItemType == ItemType.Weapon;})
// 델리게이트 활용
Item item = FindItem(delegate(Item item){return item.ItemType == ItemType.Weapon;})
```

