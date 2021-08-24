---
layout: post
title:  "Level 2 타겟 넘버"
date:   2021-06-30
tags: 코테 
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
---
#### BFS(Breadth First Search)



#### DFS()

#### 

```
#include <string>
#include <vector>
#include<iostream>
using namespace std;

int answer=0;

void dfs(vector<int> numbers, int target, int sum, int count)
{
    // target을 찾거나
    if (count == numbers.size())        // 마지막일때
    {
        if (sum == target) answer++;    
        return;
    }
    
    // 덧셈 뺄셈 반복
        dfs(numbers, target, sum + numbers[count], count + 1); 
        dfs(numbers, target, sum - numbers[count], count + 1);
}

int solution(vector<int> numbers, int target) 
{
    dfs(numbers, target, 0, 0);
    
    return answer;
}
```

