# 삽입 정렬(Insertion Sort)

### 정의
삽입 정렬(Insertion Sort)은 간단하고 직관적인 정렬 알고리즘
배열을 정렬된 부분과 정렬되지 않은 부분으로 나누고, 정렬되지 않은 부분의 원소를 정렬된 부분에 적절한 위치에 삽입하여 전체 배열을 정렬

----

### 작동 방식
1. 배열의 첫 번째 요소는 이미 정렬된 부분으로 간주
2. 정렬되지 않은 부분의 첫 번째 요소를 정렬된 부분에 삽입할 위치를 찾음
3. 해당 위치에 원소를 삽입하고, 삽입한 위치 이후의 요소들을 한 칸씩 뒤로 이동
4. 정렬되지 않은 부분의 다음 요소를 선택하여 위의 과정을 반복
5. 모든 요소가 정렬될 때까지 위의 과정을 반복

---
```C++
#include <iostream>
#include <vector>
using namespace std;

// 삽입 정렬 함수
void insertionSort(vector<int>& arr) 
{
    int n = arr.size();
    for (int i = 1; i < n; ++i) 
    {
        int key = arr[i];
        int j = i - 1;
        // key를 정렬된 부분에 삽입할 적절한 위치 찾기
        while (j >= 0 && arr[j] > key)
        {
            arr[j + 1] = arr[j];
            --j;
        }
        arr[j + 1] = key; // key를 삽입
    }
}

int main()
{
    vector<int> arr = { 1, 4, 2, 3, 5, 6 };

    cout << "Original array: ";
    for (int num : arr)
    {
        cout << num << " ";
    }
    cout << endl;

    insertionSort(arr);

    cout << "Sorted array: ";
    for (int num : arr) 
    {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}

```

---
### 시간 복잡도
- 최선의 경우: O(N) - 이미 정렬된 배열에서 최적의 성능
- 평균, 최악의 경우: O(N^2) - 배열이 역순으로 정렬되어 있는 경우에 최악의 성능

----

### 장점
- 구현이 간단하고 이해하기 쉽습니다.
- 정렬되어 있는 부분이 크면 효율적으로 작동합니다.

---

### 단점
- 평균 및 최악의 경우에는 시간 복잡도가 비효율적
- 큰 배열에 대해서는 비효율적

---

### 적절한 상황
- 입력 크기가 작은 경우에 유용
- 이미 정렬된 데이터가 약간의 변화로 들어오는 경우에 효율적

