# 피보나치 손코딩

#### `재귀활용`

```python
def fibonacci(n): 
    if n <= 1: 
        return n 
    else: 
        return(fibonacci(n-1) + fibonacci(n-2)) 
    
k = 20
for i in range(1, k): 
    print(fibonacci(i))
```

<br>

#### `DP 활용`

```python
fibo = []
for x in range(0,10): 
    if x < 2: 
        fibo.append(1) 
    else: 
        fibo.append(fibo[x-2] + fibo[x-1]) 
        
print(fibo)
```

#### `공간복잡도도 줄이고 n번으로 끝나는 코드`

```python
num = [1, 1, 0]
for i in range(2, n+1):
	num[i%3] = num[(i-1)%3] + num[(i-2)%3]
```

1 1 2

3 1 2

3 5 2

3 5 8

13 5 8

#### `DP 제대로`

```python
dp = [0]*n
def fibo(n):
	if n == 0 or n == 1: return 1
	if dp[n]: return dp[n]
	
	dp[n] = fibo(n-1) + fibo(n-2)
	return dp[n]
```



