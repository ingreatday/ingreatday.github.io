---
published: false
---
비교기반(comparison-based) 정렬 알고리즘에는 __선택 정렬(selection sort), 버블 정렬(bubble sort), 삽입 정렬(insertion sort), 쉘 정렬(shell sort), 퀵 정렬(quick sort), 합병 정렬(merge sort), 히프 정렬(heap sort)__ 이 있다.

모든 정렬마다 배열을 정렬하는 방식이 다르다. 선택 정렬을 먼저 알아보고자 한다.

**_선택 정렬 방식_**

정렬할 데이터가 배열 A\[n-1\]에 저장되어 있다고 할 때,

1\. n개의 원소 중에서 가장 작은 원소를 찾아 A\[0\]와 자리를 바꾼다. 

2\. A\[1\]부터  A\[n-1\]까지의 원소 중 가장 작은 원소를 찾아 A\[1\]과 자리를 바꾼다. 즉, 배열에서 두 번째로 작은 원소를 A\[1\]에 저장한다.

...

i. A\[i-1\]부터 A\[n-1\]까지, 남아있는 n-i+1개의 원소 중에서 가장 작은 것을 찾아 A\[i-1\]과 자리를 바꾼다.

이 단계를 n-1번 반복하면 데이터가 정렬된다.

A\[8\] = {30, 80, 10, 60, 20, 1, 100, 70} 이라고 했을 때 정렬되는 과정은 다음과 같다.

**0**  30 80 10 60 20 1 100 70

**1**  1 80 10 60 20 30 100 70

**2**  1 10 80 60 20 30 100 70

**3**  1 10 20 60 80 30 100 70

**4**  1 10 20 30 80 60 100 70

**5**  1 10 20 30 60 80 100 70

**6**  1 10 20 30 60 70 100 80

**7**  1 10 20 30 60 70 80 100

이렇게 오름차순으로 정렬된 것을 확인할 수 있다.

선택 정렬로 배열을 정렬하는 코드이다.

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

void SelectionSort(int arr\[\], int n) {
	for (int i = 0; i < n - 1; i++) {
		int minIndex = i;
		for (int j = i + 1; j < n; j++) {
			if (arr\[minIndex\] > arr\[j\])
				minIndex = j;
		}
		if(minIndex != i)
			swap(arr\[i\], arr\[minIndex\]);
	}
}

int main() {
	int arr\[8\] = { 30, 80, 10, 60, 20, 1, 100, 70 };
	SelectionSort(arr, 8);
	for (int i = 0; i < 8; i++) {
		cout << arr\[i\] << " ";
	}
	return 0;
}
```