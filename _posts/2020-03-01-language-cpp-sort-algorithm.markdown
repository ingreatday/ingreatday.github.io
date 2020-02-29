---
layout: post
title: '[c++] sort algorithm'
subtitle: About sort algorithm(STL)
categories: language
tags: cpp sort algorithm stl
comments: true
<!--header-img: img/review/2020-01-22-review-book-tableau-1.jpg  -->
published: true
---

sort 함수는 알고리즘 헤더파일에서 제공하고, 주어진 범위내에서 원소들을 정렬한다. 이 함수는 기본적으로 오름차순 정렬을 수행한다.

함수의 형태는 이와 같다.
```cpp
template <class randomaccessiterator="">
  void sort (RandomAccessIterator first, RandomAccessIterator last);        //오름차순 정렬
template <class randomaccessiterator,="" class="" compare="">
  void sort (RandomAccessIterator first, RandomAccessIterator last, Compare comp);      //사용자 정의
</class></class>
```
먼저, 오름차순으로 정렬하는 예제를 보면 아래와 같다.
```cpp
#include <iosream>
#include <algorithm>
using namespace std;

int main() {
    int arr[9] = {3, 5, 6, 7, 2, 9, 1, 4, 8};
    sort(arr, arr + 9);
    for (int i = 0; i < 9; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```
위의 예제에서 출력값은 "1 2 3 4 5 6 7 8 9"가 된다. sort함수의 변수로 배열의 시작점 주소, 마지막 주소를 입력하면 주어진 배열을 정렬한다.
```cpp
#include <iosream>
#include <algorithm>
using namespace std;

bool cmp(int x, int y){
    return x < y;
}

int main() {
    int arr[9] = {3, 5, 6, 7, 2, 9, 1, 4, 8};
    sort(arr, arr + 9, cmp);
    //sort(arr, arr + 9, less<int>());      이것 또한 오름차순으로 정렬하겠다는 의미이다

    for (int i = 0; i < 9; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```
