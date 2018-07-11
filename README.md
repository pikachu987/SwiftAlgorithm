# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "List")

## 1. 자료구조(DataStruct)
### 1)리스트(List)

#### - [연결리스트(LinkedList)](./1_DataStructure/1_List/LinkedList.md "LinkedList")
- 노드와 노드가 연결되어 있다
- 노드의 포인트가 다음 노드와 연결을 담당하게 된다

> 배열과 연결리스트 비교

-|배열|연결리스트
----|----|----
접근속도|O(1)|O(n)
추가,삭제속도(가장 앞)|-|O(1)
추가,삭제속도(가장 끝)|-|O(n)
추가,삭제속도(중간)|-|O(n)

## 2. 알고리즘(Algorithm)
### 1)정렬(Sort)

#### - [버블정렬(BubbleSort)](./2_Algorithm/1_Sort/BubbleSort.md "BubbleSort")
- 연속된 두개 인덱스를 비교를 한다
- 시간 복잡도 O(n^2)
- 공간 복잡도 O(n)

#### - [삽입정렬(InsertSort)](./2_Algorithm/1_Sort/InsertSort.md "InsertSort")
- 두번째 인덱스부터 시작
- 비교 인덱스를 자신 -1로 잡음
- 저장변수와 비교인덱스 값을 비교
- 저장변수의 값이 더 작으면 현재 인덱스로 비교인덱스 값 저장
- 시간복잡도 최악 O(n^2) 최고 O(n)
- 공간복잡도 O(n)

#### - [선택정렬(SelectSort)](./2_Algorithm/1_Sort/SelectSort.md "SelectSort")
- 정렬되지 않은 인덱스 맨 앞에서 부터 배열중 가장 작은 값을 찾음
- 가장 작은 값을 찾으면 그 값을 현재 인덱스와 바꿔준다
- 시간복잡도는 전체 비교라 O(n^2)
- 공간복잡도는 O(n)

#### - [퀵정렬(QuickSort)](./2_Algorithm/1_Sort/QuickSort.md "QuickSort")
- 특정한 기준 Pivot을 잡아 Pivot보다 작으면 왼쪽, Pivot보다 크면 오른쪽으로 이동한다.
- 정렬이 될 때 까지 구별한 왼쪽과 오른쪽을 나누어서 분할처리한다.
- 재귀를 이용한 분할정복 알고리즘
- 시간복잡도는 O(n log n) 최악 O(n^2)
- 공간잡도는 O(n)

#### - [합병정렬(MergeSort)](./2_Algorithm/1_Sort/MergeSort.md "MergeSort")
- 리스트를 반으로 분할하고 분할된 리스트를 또 반으로 분할한다. 크기가 1이 될때까지 분할한다.
- 크기가 1이된 리스트를 소팅후 병합한다.
- 시간 복잡도는 O(n log n)
- 공간복잡도는 O(n)

### 2)검색(Search)
