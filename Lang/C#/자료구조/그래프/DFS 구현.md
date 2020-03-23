### DFS

DFS 를 사용할 때는 시작점이 있어야 합니다.

1) 우선 now 방문하고

2) now 와 연결된 정점들을 하나씩 확인해서, 아직 미발견 상태라면 방문!



방문 후 하는 행동이 똑같기 때문에 재귀함수 사용에 용이



배열이용한 방법

```cs
 private bool[] visited = new bool[6];
// 1) 우선 now 방문하고 
// 2) now와 연결된 정점들을 하나씩 확인해서 [아직 미발견 상태라면] 방문한다!!
public void DFS(int now)
{
    Console.WriteLine(now);

    visited[now] = true; //  1) 우선 now 방문하고 

    for (int next = 0; next < adj.GetLength(0); next++)
    {
        if (adj[now, next] == 0)// 연결 되어 있지 않으면 스킵
            continue;
        if (visited[next]) // 이미 방문한곳 이면 스킵 
            continue;
        DFS(next);
    }

}
```

리스트 이용한 방법

```cs
 public void DFS2(int now)
 {
     Console.WriteLine(now);
     visited[now] = true; //  1) 우선 now 방문하고 

     foreach (int next in adj2[now])
     {
         if (visited[next])
             continue;
         DFS2(next);
     }
 }
```



그래프 끊겨 있는 상황에선 모두 순회가 불가능하다

```cs
 public void SearchAll()
 {
     visited = new bool[6];
     for (int now = 0; now < 6; now++)
     {
         if (visited[now] == false)
             DFS(now);
     }
 }
```

