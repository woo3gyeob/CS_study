# 퀵정렬 손코딩

피벗 : 5

왼쪽에서 부터 피벗보다 큰 데이터 선택 : 7

오른쪽에서부터 피벗보다 작은 데이터 선택 : 4

둘이 교환

![image-20210725214630598](README.assets/image-20210725214630598.png)

계속 진행

왼쪽 : 9

오른쪽 : 2

둘이 교환

![image-20210725214706057](README.assets/image-20210725214706057.png)

계속 진행

왼쪽 : 6

오른쪽 : 1

하지만 위치가 엇갈리는 경우, 피벗과 작은 데이터의 위치를 서로 변경

![image-20210725214715014](README.assets/image-20210725214715014.png)

이렇게 계속 피벗 기준으로 데이터 묶음을 나누는 걸 분할(Divide)라고 함

![image-20210725214729342](README.assets/image-20210725214729342.png)



```python
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array, start, end):
    if start >= end: # 원소가 1개인 경우 종료
        return
    pivot = start # 피벗은 첫 번째 원소
    left = start + 1
    right = end
    while(left <= right):
        # 피벗보다 큰 데이터를 찾을 때까지 반복 
        while(left <= end and array[left] <= array[pivot]):
            left += 1
        # 피벗보다 작은 데이터를 찾을 때까지 반복
        while(right > start and array[right] >= array[pivot]):
            right -= 1
        if(left > right): # 엇갈렸다면 작은 데이터와 피벗을 교체
            array[right], array[pivot] = array[pivot], array[right]
        else: # 엇갈리지 않았다면 작은 데이터와 큰 데이터를 교체
            array[left], array[right] = array[right], array[left]
    # 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬 수행
    quick_sort(array, start, right - 1)
    quick_sort(array, right + 1, end)

quick_sort(array, 0, len(array) - 1)
print(array)
```

```python
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array):
    # 리스트가 하나 이하의 원소만을 담고 있다면 종료
    if len(array) <= 1:
        return array

    pivot = array[0] # 피벗은 첫 번째 원소
    tail = array[1:] # 피벗을 제외한 리스트

    left_side = [x for x in tail if x <= pivot] # 분할된 왼쪽 부분
    right_side = [x for x in tail if x > pivot] # 분할된 오른쪽 부분

    # 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬을 수행하고, 전체 리스트를 반환
    return quick_sort(left_side) + [pivot] + quick_sort(right_side)

print(quick_sort(array))
```

