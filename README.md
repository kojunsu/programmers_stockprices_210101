# 프로그래머스 코딩테스트 연습(주식 가격)



###문제설명
![문제1](https://user-images.githubusercontent.com/62390565/103440436-d5bb0980-4c88-11eb-8250-143f15ce95a8.PNG)
###





### Solution 1
```python
#solution_1.py

def solution(prices):
    answer = [0] * len(prices)
    for i in range(len(prices)):
        for j in range(i+1, len(prices)):
            if prices[i] <= prices[j]:
                answer[i] += 1
            else:
                answer[i] += 1
                break
    return answer
```

![solution_1](https://user-images.githubusercontent.com/62390565/103440385-50375980-4c88-11eb-98a3-bbc3134e95b0.PNG)





### Solution 2
```python
#solution_2.py
from collections import deque
def solution(prices):
    answer = []
    prices = deque(prices)
    while prices:
        c = prices.popleft()

        count = 0
        for i in prices:
            if c > i:
                count += 1
                break
            count += 1

        answer.append(count)

    return answer

```





### Solution 3
```python
#solution_3.py

def solution(p):
    ans = [0] * len(p)
    stack = [0]
    for i in range(1, len(p)):
        if p[i] < p[stack[-1]]:
            for j in stack[::-1]:
                if p[i] < p[j]:
                    ans[j] = i-j
                    stack.remove(j)
                else:
                    break
        stack.append(i)
    for i in range(0, len(stack)-1):
        ans[stack[i]] = len(p) - stack[i] - 1
    return ans

```




[프로그래머스 코딩테스트 연습](https://programmers.co.kr/learn/challenges)
