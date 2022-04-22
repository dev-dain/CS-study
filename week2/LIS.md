
# LIS.md

작성자 : 김다인

---

### Longest Increasing Subsequence, 최장 증가 부분 수열
임의의 수열이 주어질 때, 수열에서 몇 개의 수들을 제거해 만들 수 있는 부분수열 중 오름차순으로 정렬된 가장 긴 수열을 **최장 증가 부분 수열**이라고 부른다.  
보통 이 최장 증가 부분 수열 자체를 구하거나 그 길이를 구하는 것이 문제로 나오는데, 이는 다이나믹 프로그래밍으로 풀 수 있는 대표적인 문제이다.  

#### 완전탐색으로 풀기
O(2^N)으로 풀 수 있는, 가장 떠올리기 쉬운 해결법이다. lis 함수를 재귀적으로 호출하는 풀이이다. 
```python
def lis(arr):
  if not arr:
    return 0
    
  res = 1
  for i in range(len(arr)):
    nxt = []
    for j in range(i+1, len(arr)):
      if arr[i] < arr[j]:
        nxt.append(arr[j])
    res = max(res, 1 + lis(nxt))
  return res	
```

#### DP로 풀기
이 해결법은 리스트의 크기만큼 1로 초기화된 DP 테이블을 만들고, i번 원소까지 나올 수 있는 최대 LIS 길이를 갱신하는 방법이다. 시간복잡도는 O(n^2)이다.
```python
def lis(arr):
  dp = [1 for _ in range(len(arr))]

  for i in range(len(arr)):
    for j in range(i):
      if arr[i] > arr[j]:
        dp[i] = max(dp[i], dp[j]+1)
  
  return max(dp)
```

#### 이진탐색으로 풀기
DP로 푸는 방법은 유명하지만 이진탐색으로 푸는 방법은 그보다는 조금 덜 알려져있다.  
이 방법은 dp[0]~dp[i-1]의 최댓값을 알고 있다면 dp[i]를 구하기 위해 굳이 또 전 값을 확인하는 반복을 할 필요가 없다는 아이디어에서 시작한다.  
파이썬에서는 bisect 모듈을 사용해서 코드를 짤 수 있다. 이 방법은 n개의 수들에 대해 이진 탐색을 하므로 시간복잡도 O(nlogn)으로 LIS를 구할 수 있다.
```python
import bisect

def lis(arr):
  dp = [arr[0]]
  
  for i in range(len(arr)):
    # 현재 위치 값이 이전 위치 원소들보다 크면 dp에 추가
    # 이게 가능한 이유는 dp[-1]은 항상 dp에서 제일 큰 값이 될 것이기 때문
    if arr[i] > dp[-1]:
      dp.append(arr[i])
    # 현재 위치 값이 이전 위치 원소보다 작거나 같다면
    else:
      # 이전 위치 원소 중 가장 큰 원소 인덱스 구하기
      idx = bisect.bisect_left(dp, arr[i])
      # dp idx 원소를 arr[i]로 변경
      dp[idx] = arr[i]
      
  return len(dp)
```

### 예제 문제

* [백준 11053 가장 긴 증가하는 부분 수열](https://www.acmicpc.net/problem/11053)
* [백준 12015 가장 긴 증가하는 부분 수열 2](https://www.acmicpc.net/problem/12015)
* [백준 14002 가장 긴 증가하는 부분 수열 4](https://www.acmicpc.net/problem/14002)
* [백준 14003 가장 긴 증가하는 부분 수열 5](https://www.acmicpc.net/problem/14003)

---
[가장 긴 증가하는 부분 수열(LIS) 완전 정복 - 백준 파이썬](https://seohyun0120.tistory.com/entry/%EA%B0%80%EC%9E%A5-%EA%B8%B4-%EC%A6%9D%EA%B0%80%ED%95%98%EB%8A%94-%EB%B6%80%EB%B6%84-%EC%88%98%EC%97%B4LIS-%EC%99%84%EC%A0%84-%EC%A0%95%EB%B3%B5-%EB%B0%B1%EC%A4%80-%ED%8C%8C%EC%9D%B4%EC%8D%AC)  
[LIS의 길이를 구하는 3가지 알고리즘](https://shoark7.github.io/programming/algorithm/3-LIS-algorithms)