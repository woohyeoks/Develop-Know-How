### Tail

> 출처  https://m.blog.naver.com/PostView.nhn?blogId=pcgun70&logNo=220704240292&proxyReferer=http%3A%2F%2F222.99.86.34%2Ftm%2F%3Fa%3DCR%26b%3DWIN%26c%3D300016136421%26d%3D32%26e%3D3102%26f%3DbS5ibG9nLm5hdmVyLmNvbS9wY2d1bjcwLzIyMDcwNDI0MDI5Mg%3D%3D%26g%3D1584426311491%26h%3D1584426310948%26y%3D0%26z%3D0%26x%3D1%26w%3D2019-07-22%26in%3D3102_1525_00016123%26id%3D20200317 

점검이나 로그를 실시간으로 볼때 유용하게 사용됩니다.

[TAIL] 파일의 마지막 부분을 출력합니다.

[문법] tail [option] ... file // 기본 출력은 파일의 마지막 10줄을 보여줍니다.

[옵션]

```
-f : 파일의 마지막 10라인을 실시간으로 계속 출력
-F : 파일 변동 시 실시간으로 보여주되 로그파일처럼 특정 시간이 지난 후 파일이 변하게 되면 새로운 파일을 오픈하여 보여줌
-n : n 만큼의 라인을 출력
-n +n : 마지막 줄이 아니라 첫번째 부터 시작해 n번째 라인 이후 부터 출력
--byte=n : n바이트 만큼의 내용 출력
```

[예제]

```
tail -n 20 anaconda-ks.cfg 
tail -n +20 anaconda-ks.cfg
tail -f /var/log/error.log
```

[응용]

그냥 쌩으로 보는게 아니고 일정 단어가 포함된 라인만 출력하게 해보자!!! 

grep을 활용하면 쉽게할 수 있습니다.

tail [option] [file] | grep [string]

[예제]

```
tail -f error.log | grep 'tomato'

grep -rni tomato error.log
```

