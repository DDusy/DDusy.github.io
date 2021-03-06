---
layout: post
title: "Level 2 더 맵게 / 우선순위 큐 사용"
date: 2021-06-01 
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
tags:	코테
---

#### priority_queue 

- <queue> 헤더 사용

- priority_queue<T,Container,Compare>

- compare 는 less 를 기준으로  최대 힙으로 생성

- vector를 기본 컨테이너로 사용

- 최소 / 최대 원소 접근 동작에 O(1)의 시간 복잡도

- 원소 추가는 O(log n) 의 시간복잡도

- 최소/최대 데이터를 맨위까지 끌어올리는 히피파이 알고리즘이 중요

  - 하향식 재구성(TopDown Heapify)

    - 한 노드에서 Leaf까지 내려가면서 힙을 만듬

  - 상향식 재구성(BottomUp Heapify)

    - 한 노드에서 root까지 올라가면서 힙을 재구성

      

###### 추가 및 삭제

- push(element) : 우선순위 큐에 원소추가
- pop(): 우선순위 큐에서 top의 원소 삭제 (최대 / 최소 원소에 대해서만 가능)

###### 조회

- top() : top에 있는 원소 반환

###### 기타 

- Empty() : 비어있으면 true  아닐때 false
- size(): 우선순위 큐에 포함되어 있는 원소들의 수를 반환





~~~c++

int solution(vector<int> scoville, int K) {
   
    int answer = 0;
    int min=0;
    
    priority_queue< int, vector<int>, greater<int> > 	 
        qScovile(scoville.begin(),scoville.end());
    
    while(qScovile.top()<K)
    {
        if(qScovile.size()==1)
              return -1;
            
            min = qScovile.top();
            qScovile.pop();
        
            qScovile.push(min + (qScovile.top() *2));
            
            qScovile.pop();
          
            ++answer;   
    }
    
    return answer;
}
~~~

