# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "List")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

## 1. 자료구조(DataStruct)

### 1)리스트(List)

#### - [연결리스트(LinkedList)](./1_DataStructure/1_List/LinkedList.md "LinkedList")
- 노드와 노드가 연결되어 있다
- 노드의 포인트가 다음 노드와 연결을 담당하게 된다

> 배열과 연결리스트 비교

기능\리스트|배열|연결리스트
----|----|----
접근속도|O(1)|O(n)
추가,삭제속도(가장 앞)|-|O(1)
추가,삭제속도(가장 끝)|-|O(n)
추가,삭제속도(중간)|-|O(n)

#### - [이중연결리스트(DoubleLinkedList)](./1_DataStructure/1_List/DoubleLinkedList.md "DoubleLinkedList")
- 노드가 이전노드와 다음노드로 구성되어 있다
- 노드가 양방향으로 연결되어 있어서 양쪽으로 탐색 가능하다

#### - [환형연결리스트(CircularLinkedList)](./1_DataStructure/1_List/CircularLinkedList.md "CircularLinkedList")
- 노드가 환형으로 구성되어 있다


### 2)스택(Stack)

#### - [스택(Stack)](./1_DataStructure/2_Stack/Stack.md "Stack")
- FILO(First In, Last Out) 선입 후출. 먼저 데이터를 넣은것이 나중에 삭제됨
- Push로 데이터 추가
- Pop으로 데이터 삭제

#### - [스택계산기(StackCalculator)](./1_DataStructure/2_Stack/StackCalculator.md "StackCalculator")
- 공부중

### 3)큐(Queue)

#### - [큐(Queue)](./1_DataStructure/3_Queue/Queue.md "Queue")
- FIFO(First In, First Out) 선입 선출. 먼저 데이터를 넣은것이 먼저 삭제됨
- Enqueue로 데이터 추가
- Dequeue으로 데이터 삭제

#### - [순환큐(CircularQueue)](./1_DataStructure/3_Queue/CircularQueue.md "CircularQueue")
- 공부중

### 4)트리(Tree)

- 노드(Node): 트리의 구성요소 하나하
- 루트(Root): 유일한 시작노드
- 서브트리(Sub-Tree): 각 노드를 기준으로 그 노드가 루트가 되는 트리
- 단말노드(Terminal Node, Leaf Node): 자식이 없는 노드
- 중간노드(Branch Node): 적어도 하나의 자식을 가지는 노드
- 부모노드(Parent Node): 바로 위에 있는 노드
- 형제노드(Sibling Node): 같은 계층에 있는 노드
- 자식노드(Child Node): 바로 아래에 있는 노드
- 레벨(Level): 루트노드와 현재 노드를 연결하는 선의 수
- 높이(Height): 트리 최대 레벨 가장 아래의 노드 레벨
- 깊이(Depth): 루트에서 어떤 노드까지의 경로의 개수
- 차수(Degree): 노드의 자식 개수

#### - [트리(Tree)](./1_DataStructure/4_Tree/Tree.md "Tree")
- 왼쪽 자식 / 오른쪽 형제

#### - [이진트리(BinaryTree)](./1_DataStructure/4_Tree/BinaryTree.md "BinaryTree")

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

#### - [순차검색(SequentialSearch)](./2_Algorithm/2_Search/SequentialSearch.md "SequentialSearch")
- 순차적으로 비교해서 검색
- 시간복잡도 O(n)

#### - [전진이동법(MoveToFrontMethod)](./2_Algorithm/2_Search/MoveToFrontMethod.md "MoveToFrontMethod")
- 순차적으로 비교해서 검색
- 요소를 찾으면 요소를 뽑아 제일 앞으로 이동

#### - [전위법(TransposeMethod)](./2_Algorithm/2_Search/TransposeMethod.md "TransposeMethod")
- 순차적으로 비교해서 검색
- 요소를 찾으면 요소를 한칸 앞으로 이동

#### - [이진탐색(BinarySearch)](./2_Algorithm/2_Search/BinarySearch.md "BinarySearch")
- 데이터 집합의 중앙에 있는 요소를 골라서 비교
- 요소가 찾는 값보다 크면 중앙을 기준으로 왼쪽에 대해 새로 검색, 작으면 오른쪽
- 시간복잡도 O(logN)
- 데이터가 반드시 정렬되어 있어야함

#### - [이진탐색트리(BinarySearchTree)](./2_Algorithm/2_Search/BinarySearchTree.md "BinarySearchTree")
- 이진 탐색을 위한 이진 트리
- 왼쪽 자식 노드는 나보다 작고 오른쪽 자식 노드는 나보다 크다
- 노드를 삭제할때는 잎노드일때는 자신만 삭제
- 한쪽만 자식이 있을때는 자식과 교체
- 양쪽 다 자식이 있을때는 자기보다큰 자식의 최소노드를 구해서 최소노드를 삭제후 자신과 교체

#### - [레드블랙트리(BinarySearchTree)](./2_Algorithm/2_Search/BinarySearchTree.md "BinarySearchTree")
- 공부중
