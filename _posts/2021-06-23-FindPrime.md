---
layout: post
title:  "프로그래머스 Level 2 소수 찾기"
date:   2021-06-23 
tags: 코테
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
---
#### 에라토스테네스의 체



#### 순열

```c++
#include <string>
#include <vector>
#include <unordered_set>

using namespace std;

unordered_set <int> s;
string str = "";
bool check[7]; // 7이하 

//순열 저장
void find_all_numbers(int depth, int limit, string& numbers){
  
    if(depth == limit) return;
    
    for(int i = 0 ; i < limit ; i++){
        
        if(!check[i]){
            
            check[i] = true;
            str.push_back(numbers[i]);
            s.insert(stoi(str));
            find_all_numbers(depth+1, limit, numbers);
            str.pop_back();
            check[i] = false;
        }
    }
}

int solution(string numbers) {
    int size = numbers.size();
    
    find_all_numbers(0,size, numbers);
    
    int answer = 0;
    
    // 소수 찾기
    for(auto& it : s){
        
        if(it == 1 || it == 0) continue; // 소수가 아니므로 제외
    
        bool isDivided = false;
        
        for(int i = 2 ; i*i <= it ; i++)
        {
            if(it % i == 0) isDivided = true;
        }
        
        if(!isDivided) answer++;
    }
    
    return answer;
}
```

