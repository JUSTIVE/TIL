# prefix sum

구간 합 알고리즘은 주어진 `A_n` 에 대해서 (0 \<= i \<=k \<= n -1 ) 인 i,k 에 대해 `A_i` 부터 `A_k`까지의 합을 구하는 알고리즘이다.
일반적인 구간 합 알고리즘의 시간 복잡도는 `O(n)` 이다.

구간 합의 예시, 백준 11441 (boj.kr/11441)

```python
import sys
dataLen = int(sys.stdin.readline())

rawData = list(map(int, sys.stdin.readline().split(" ")))
data = [0, rawData[0]]
for i in range(1, len(rawData)):
    data.append(data[i]+rawData[i])

testLength = int(sys.stdin.readline())

for i in range(testLength):
    a, b = map(int, sys.stdin.readline().split(" "))
    print(data[b]-data[a-1])
```

위 문제의 경우, 이후에 들어오는 일련의 `x_(n_1)`~`x_(n_2)`까지의 구간합들을 O(1) 안에 처리해야 하므로, 미리 `A_0`~`A_(x_1)`까지의 합을 미리 계산해놓고, `A_(x_2)` - `A_(x_1 - 1)`를 통해 계산한 방법이다.