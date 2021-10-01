---
layout: post
title:  "프로그래머스 Level 3 네트워크"
date:   2021-09-28
tags: 코테
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
---
#### 문제 접근 방식

이미 검사한 인덱스는 제외해 가며 검사

dfs를 통해 더 이상 들어갈 수 없는 곳 까지 검색

![Square](?raw=true)

#### 코드

```
#include <string>
#include <vector>
using namespace std;

bool dfs(vector<vector<int>>& computers, int n,int _Cnt) 
{

    if (!computers[n][n])    return false;
  
    computers[n][n] = 0;

    for (int i = 0; i < _Cnt; i++) 
    {
        if (computers[n][i])  
            dfs(computers,i,_Cnt);
    }
    
    return true;
}

int solution(int n, vector<vector<int>> computers) {
    int answer = 0;
    
    for (int i = 0; i < n; i++)
    {
        if (computers[i][i] && dfs(computers, i,n))
            answer++;
    }
    return answer;
}
```

