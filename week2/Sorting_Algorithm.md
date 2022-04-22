# Sorting Alogrithm

### **작성자 강수지** <br><br>

정렬알고리즘이란 섞여 있는 여러 데이터를 순서대로 정렬하여 나열하는 알고리즘이다

시간복잡도에 따라 성능이 좌우되며 성능이 좋을수록 구현이 복잡하다

sorting 알고리즘의 Comparisons 방식 알고리즘 종류를 소개한다

## 정렬의 종류

### O(n²) 의 시간복잡도 ( 정렬할 자료의 수가 늘어나면 제곱에 비례하여 증가 )

- 버블 정렬 (Bubble Sort)
- 선택 정렬 (Selection Sort)
- 삽입 정렬 (Insertion Sort)

### O(nlogn) 의 시간복잡도

- 병합 정렬 (Merge Sort)
- 퀵 정렬 (Quick Sort)

---

## 버블정렬 ( bubble sort )
인접한 두 수를 비교하며 정렬하는 방식이다

앞에서부터 비교하여 큰 수를 뒤로 보내고 가장 큰 값이 뒤에 위치하도록 정렬한다

또는 뒤에서부터 비교하기도 한다

**시간복잡도는 O(n²) 공간복잡도는 O(1) 이다**

```python
array = [9,8,7,6,5,4,3,2,1]

def bubble_sort(array):
    n = len(array)
    for i in range(n - 1):
        for j in range(n - i - 1):
            if array[j] > array[j + 1]:
                array[j], array[j + 1] = array[j + 1], array[j]
        print(array)

print("before: ",array)
bubble_sort(array)
print("after:", array)
```

---

## 선택정렬 ( selection sort )

가장 작은 값을 맨 앞과 교환해나가는 방식이다

앞에서부터 정렬해나간다는 특징이 있다
 
**시간복잡도는 O(n²) 공간복잡도는 O(1) 이다**

```python
array = [8,4,6,2,9,1,3,7,5]

def selection_sort(array):
	n = len(array)
	for i in range(n):
		min_index = i
		for j in range(i + 1, n):
			if array[j] < array[min_index]:
				min_index = j
		array[i], array[min_index] =  array[min_index], array[i]
		print(array[:i+1])

print("before: ",array)
selection_sort(array)
print("after:", array)
```

---

## 삽입정렬 ( insertion sort )
정렬된 데이터 그룹을 늘려가며 추가되는 데이터를 알맞은 자리에 삽입하는 정렬이다

**시간복잡도는 O(n²) 공간복잡도는 O(1) 이다**

```python
array = [8,4,6,2,9,1,3,7,5]

def insertion_sort(array):
	n = len(array)
	for i in range(1, n):
		for j in range(i, 0, - 1):
			if array[j - 1] > array[j]:
				array[j - 1], array[j] = array[j], array[j - 1]
		print(array[:i+1])

print("before: ",array)
insertion_sort(array)
print("after:", array)
```

---

## 병합정렬 ( merge sort )
분할정복과 재귀를 반복하는 알고리즘이다

반으로 쪼개고 다시 합치는 과정에서 그룹을 만들어 정렬하게되며 이때 2n개의 공간이 필요하다

**시간복잡도는 O(nlogn) 공간복잡도는 O(n) 이다**

```python
array = [8,4,6,2,9,1,3,7,5]

def merge_sort(array):
	if len(array) < 2:
		return array
	mid = len(array) // 2
	low_arr = merge_sort(array[:mid])
	high_arr = merge_sort(array[mid:])

	merged_arr = []
	l = h = 0
	while l < len(low_arr) and h < len(high_arr):
		if low_arr[l] < high_arr[h]:
			merged_arr.append(low_arr[l])
			l += 1
		else:
			merged_arr.append(high_arr[h])
			h += 1
	merged_arr += low_arr[l:]
	merged_arr += high_arr[h:]
	print(merged_arr)
	return merged_arr

print("before: ",array)
array = merge_sort(array)
print("after:", array)
```

---

## 퀵정렬 ( quick sort )

병합정렬처럼 분할정복알고리즘으로 평균적으로 빠른 속도를 수행한다

추가적인 메모리 공간이 필요하지 않고 Pivot 이라는 기준을 설정하여 정렬한다

보통 정렬 내장 함수로 퀵정렬을 수행한다

**시간복잡도는 O(nlogn) 공간복잡도는 O(1) 이다**

```python
array = [8,4,6,2,5,1,3,7,9]

def quick_sort(array):
	if len(array) <= 1:
		return array
	pivot = len(array) // 2
	front_arr, pivot_arr, back_arr = [], [], []
	for value in array:
		if value < array[pivot]:
			front_arr.append(value)
		elif value > array[pivot]:
			back_arr.append(value)
		else:
			pivot_arr.append(value)
	print(front_arr, pivot_arr, back_arr)
	return quick_sort(front_arr) + quick_sort(pivot_arr) + quick_sort(back_arr)

print("before: ",array)
array = quick_sort(array)
print("after:", array)
```

주의할 점은 오름차순으로 정렬한다고 가정하면 pivot 이 설정되고 이를 기준으로 좌측엔 작은값 우측엔 큰값이 위치하도록 parition 된다

나뉜 배열을 다시 재귀적으로 퀵 정렬하면 또 partition 과정이 반복되는데 이때 pivot 으로 설정된 값을 다음 재귀과정에 포함시키지 않아야한다 ( 이미 자신의 위치가 선정됨 )

하지만 worst case 에서는O(n²) 이 나올 수 있다 !

위와 같이 오름차순으로 정렬한다고 가정했을때 pivot value 가 가장 작은 값 또는 가장 큰 값으로 설정되었을 경우이다

매 partition 마다 unbalanced parition 이 이루어지게 되므로 복잡도가 O(n²) 이 된다 !
