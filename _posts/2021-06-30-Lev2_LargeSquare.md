---
layout: post
title:  "프로그래머스 Level 2 가장 큰 사각형 찾기"
date:   2021-06-30
tags: 코테
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
---
Posting Test

```
#include <iostream>
#include<vector>
#include<algorithm>

using namespace std;

int solution(vector<vector<int>> board)
{
    
    int answer = 1234;
    int iSizeX= board.size();
    int iSizeY= board[0].size();
    int max=0;
    
    if(iSizeX==1 || iSizeY ==1 ) return 1;
    
    for(int i=1;i<iSizeX ;++i)
    {
        for(int j=1;j<iSizeY;++j)
        {   
            
            if(board[i][j]) // 1일때
            { 
                // algorithm - min, max / 이니셜라이즈로 묶을경우 배열 중 작은거
                int min = std::min( {board[i-1][j],board[i][j-1], board[i-1][j-1]} );
                
                board[i][j] = min+1;
                
               max = std::max(max, min+1);
            //   cout<<"i: "<<i<<","<<"j: "<<j<<endl;
               
            }
        }
        
         
    }
    
    return max*max ;
}
```

