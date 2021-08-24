---
layout: post
title:  "소수 만들기"
date:   2021-06-26 
tags: 코테
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
---


#### 소수찾기

#### 조합

```
#include <vector>
#include <iostream>
using namespace std;

static int iPrimeCheck=0;

vector<int> _Stack;
vector<bool> check;

bool PrimeCheck(int& _iNum)
{
    for(int i=2;i*i<=_iNum;++i)
    {
        if(0==_iNum%i)
            return false;
    }
     return true;
}

void  combination(int _idx,int _n,int _r,vector<int>& nums)
{

    if(_n==_r)
    {
        int _total=0;
        
        for(auto& i:_Stack) { _total+=i; }
        
        //소수체크
        if(PrimeCheck(_total))
            ++iPrimeCheck;
        
        return;
    }
    
    
    for(int i=_idx;i<nums.size();i++)
    {
        if(check[i])
            continue;
        
        check[i] =true;
        _Stack.push_back(nums[i]);
        combination(i,_n+1,_r,nums);
        _Stack.pop_back();
        check[i] =false;
    }
}

int solution(vector<int> nums) {
    int answer = -1;

    check.resize(nums.size());
    
    
    //조합으로  뽑고  숫자 판별
    combination(0,0,3,nums);

    return iPrimeCheck;
}
```

