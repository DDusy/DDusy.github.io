---
layout: post
title:  "프로그래머스 Level 2 멀쩡한 사각형"
date:   2021-07-16
tags: 코테
color: rgb(100,150,200)
cover: '../assets/Coding_Test.png'
---


#### 최대공약수 

두 자연수의 공통된 약수 중 가장 큰 수

유클리드 호제법

[참고]

https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95



![gcdImg](https://github.com/DDusy/DDusy.github.io/blob/main/assets/gcd.PNG)

- return은 longlong형

```c++
long long gcd(long long a, long long b)
{
	long long c;
	while (b != 0)
	{
		c = a % b;
		a = b;
		b = c;
	}
	return a;
}

long long solution(int w,int h) {
    
    long long loose= (static_cast<long long>(w)+h) -gcd(w,h);
    long long answer = (static_cast<long long>(w)*h) - loose;
     
    return answer;
}
```

