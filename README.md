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
- 중위 표기법: 우리가 아는 수식 4 * 2 + 5 * ( 2 + 1 ) + 6 / 2
- 후위 표기법: 컴퓨터가 계산하기 쉬운 수식 4 2 * 5 2 1 + * + 6 2 / +
- 연산자 우선순위
- " * " , " / "
- " + " , " - "
- " ( " , " ) "
- 숫자는 list에 담고 연산자는 stack에 담는다.
- 연산자중 (이거나 스택이 비었을때는 stack에 담는다
- 연산자중 )가 나오면 ( 가 나오거나 빈값이 될때 까지 list로 넣는다
- 연산자가 stack의 마지막 연산자보다 가중치가 높으면 stack에 넣는다
- 연산자가 stack의 마지막 연산자보다 가중치가 낮으면 ( 가 나오거나 가중치보다 높은게 나올때나 빈값이 될때까지 list로 넣는다
- 남은 스택 연산자들을 list로 넣는다
- list에 있는 값, 연산자들을 다시 풀어서 값이면 stack에 넣는다.
- 연산자면 stack에 있는 값을 2번 뺀다. 먼저 뺀게 2번째 나중에 뺀게 1번째가 되고 계산후 값을 stack에 넣는다.

### 3)큐(Queue)

#### - [큐(Queue)](./1_DataStructure/3_Queue/Queue.md "Queue")
- FIFO(First In, First Out) 선입 선출. 먼저 데이터를 넣은것이 먼저 삭제됨
- Enqueue로 데이터 추가
- Dequeue으로 데이터 삭제

#### - [순환큐(CircularQueue)](./1_DataStructure/3_Queue/CircularQueue.md "CircularQueue")
- 선형큐를 구현하면 enqueue와 dequeue가 되면서 front가 점차 뒤로가게 된다.
- 메모리공간을 다 쓰면 다시 앞의 메모리공간에 enqueue, dequeue할수 있는 원형큐가 필요하다.
- 전단은 front, 후단은 rear로 표현
- full은 전단과 후단중 후단이 더 클때 후단+1 - 전단이 array사이즈와 같으면 풀 (+1 해주는거는 더미데이터)
- full은 전단과 후단중 전단이 더 클때 후단+1 이 전단과 같으면 풀
- enqueue를 했을때 풀이 아니면 rear을 증가시키고 real인덱스에 추가
- enqueue를 했을때 풀이 아니고 rear이 array의 사이즈-1이 되면 rear을 0으로 만들고 rear인덱스에 추가
- empty는 전단과 후단이 같을때
- dequeue를 했을때 empty가 아니고 전단이 array사이즈-1 이면 전단 0으로 만들고 전단 인덱스 삭제
- dequeue를 했을때 empty가 아니고 전단이 array사이즈-1 가 아니면 전단 증가하고 전단 인덱스 삭제

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

### 3)우선순위 큐와 힙(PriorityQueueHeap)

- FIFO 구조인 큐를 사용한다. 큐와 차이점은 데이터에 우선순위가 있다.
- 힙은 완전 이진트리의 특징을 가진다.
- 힙에서 루트는 가장 작은 데이터를 가진다. 자신 노드가 부모 노드보다 커야한다.
- 힙이 꽉 찾다면 크기조절을 한다.
- 삽입과 삭제는 시간복잡도 O(log N)

### 4)해시 테이블(HashTable)

- 해시 테이블은 Key에 Value를 저장하는 데이터 구조이다.
- 삽입, 삭제, 탐색시 O(1)의 시간복잡도를 가진다.
- 메모리를 미리 할당하기 때문에 공간 효율적이지 않다.
- 해시테이블은 근본적인 문제가 있는데 미리 공간을 만들어서 인덱스의 값이 중복이 될수 있다.
- 이 문제를 collision(충돌) 이라고 하는데 이 문제를 해결하는 방식이 있다.

#### Separate chaining
- LinkedList를 이용하는 방식인데 동일 index로 충돌이 발생하면 index가 가리키고 있는 Linked List에 노드를 추가해서 값을 추가한다.
- 데이터를 추출할때는 key에 대한 index를 구한 다음 index가 가리키고 있는 Linked List를 선형 검색한다.

#### Open Addressing
- 충돌이 났을때 빈공간을 사용하는 방법이다.
- Linear probing 방식은 index에 충돌이 났을때 index뒤에 있는 곳중 빈 곳을 찾아서 데이터를 넣는 방식이다.
- Resizing 방식은 더큰 크기의 array를 새로 만들고 새로운 array에 hash를 다시 계산해서 복사해준다.

### 5)그래프(Graph)

#### - [인접행렬(AdjacencyMatrix)](./2_Algorithm/5_Graph/AdjacencyMatrix.md "AdjacencyMatrix")
- 2차원 배열의 특성상 공간복잡도가 O(n2)이므로 메모리 낭비가 문제가 될 수 있다.
- 대부분의 인접행렬은 시간복잡도도 O(n2)이 된다.
- 무가중치 행렬에서는 [i]노드에서 [j]노드로 가는 간선이 있으면 1, 없으면 0이다.
- 가중치 행렬에서는 [i]노드에서 [j]노드 간선의 가중치를 입력한다.

#### - [인접리스트(AdjacencyList)](./2_Algorithm/5_Graph/AdjacencyList.md "AdjacencyList")
- 노드와 노드가 연결된곳만 데이터를 넣는다.
- 데이터의 순서는 무관
- 검색을 빨리해서 시간복잡도를 줄이려면 인접리스트를 쓴다.
- 인접행렬은 인덱스로 접근할수 있어서 작업이 번번하다면 인접행렬을 쓴다.

#### - [깊이우선탐색(DFS:Depth First Search)](./2_Algorithm/5_Graph/DFS.md "DFS")
- 현재 정점과 인접한 간선들을 하나씩 검사하고 아직 방문하지 않은 정점으로 향하는 간선이 있으면 그 간선을 따라감
- 더이상 갈곳이 없으면 마지막에 왔던 간선을 따라 뒤로 돌아가면서 탐색
- 일단 갈곳이 있으면 가고본다는 타입

#### - [깊이우선탐색 최단거리(DFS:Depth First Search)](./2_Algorithm/5_Graph/DFSDistance.md "DFS")


#### - [너비우선탐색(BFS:Breadth First Search)](./2_Algorithm/5_Graph/BFS.md "BFS")
- 인접한 정점을 발견하면 거길 탐색후 다시 돌아와서 다음 인접 정점을 탐색
- 깊이가 1인 모든정점을 방문후 그다음 깊이가 2인 정점을 방문
- 더이상 방문할 곳이 없으면 탐색을 마침
- 같은 깊이를 다 탐색후 다음 깊이를 다 탐색

#### - [너비우선탐색 최단거리(BFS:Breadth First Search)](./2_Algorithm/5_Graph/BFSDistance.md "BFS")

#### - 위상정렬

#### - 최소 신장 트리 - 프림

#### - 최소 신장 트리 - 크루스칼

#### - 최단 경로 탐색 - 다익스트라

#### - 최단 경로 탐색 - 플로이드 워샬


### 7)문자열 검색(String Search)

#### - [전수조사법(BruteForce)](./2_Algorithm/7_StringSearch/BruteForce.md "BruteForce")
- N의 길이를 가진 전체문자열과 M의 길이를 가진 패턴을 비교
- 시간복잡도는 O(N*M)
- 비효율적

#### - [라빈-카프 알고리즘(Rabin-Karp)](./2_Algorithm/7_StringSearch/Rabin_Karp.md "Rabin_Karp")
- 스트링을 ascii값과 같은 숫자값으로 바꾼 뒤 hash값을 계산해서 pattern과 매칭한다.
- hash값과 hash값이 같으면 단순 비교를 한다.
- H(S[i+1:i+M])은 바로 이전 위치 해시값 H(S[i:i+M-1])을 알면 O(1)에 계산할 수 있는 구조를 띈다.
- 전처리 시간복잡도는 O(m), 탐색 시간복잡도는 O(mn), 평균적으로 O(m+n)

#### - [KMP 알고리즘](./2_Algorithm/7_StringSearch/KMP.md "KMP")
- 이전에 비교한 정보를 활용하여 검색하는 방법
- 이전에 비교했던 정보로 비교할 필요 없는 부분을 건너뛴다.
- 접두사(prefix) == 접미사(suffix)가 될 수 있는 부분문자중 가장 긴 것의 길이 배열을 구한다.
- 시간복잡도는 O(n+m)

#### - [보이어-무어 알고리즘(Boyer-Moore)](./2_Algorithm/7_StringSearch/Boyer_Moore.md "Boyer_Moore")
- 이동은 왼쪽에서 오른쪽으로 하지만 문자열 비교를 오른쪽에서 왼쪽으로 비교함
- 대부분의 프로그램이 사용중
- 오른쪽 끝문자가 패턴에서 발견되지 않으면 패턴의 길이만큼 검색위치를 이동시켜 비교를 제거
- 나쁜 문자 이동(Bad Character Shift)과 착한 접미부 이동(Good Suffix Shift)가 있음
- 불일치가 발생하면 최대의 효율로 이동
- 나쁜문자이동: 패턴에서 나쁜문자를 찾고 찾아낸 패턴의 나쁜문자의 위치가 본문의 나쁜 문자 위치와 일치하게 패턴을 이동
- 착한접미부이동: 불일치가 일어났을때 착한 접미부와 동일한 문자열이 패턴의 착한 접미부 왼쪽에 존재하는경우
- 착한접미부이동: 착한 접미부가 패턴안에 존재하지는 않지만 착한 접미부의 접미부가 패턴의 접두부와 일치할때
- 전처리 시간/공간복잡도는 O(m+a)
- 탐색 시간복잡도 O(mn)
- 일반적으로 O(n) 보다 작음
- 최선의 경우 O(n/m)

### 8)분할 정복(Divide and Conquer)

#### - [거듭 제곱(Exponentiation)](./2_Algorithm/8_DivideAndConquer/Exponentiation.md "Exponentiation")
- 거듭제곱은 자기 자신을 지수의 크기만큼 곱셈을 해야한다.
- 예를들어 2의 8승은 2*2*2*2*2*2*2*2 이므로 O(n) 의 시간복잡도를 가지고있다.
- 이것을 분할정복 알고리즘으로 하면 ((2*2) * (2*2)) * ((2*2) * (2*2))로 된다.
- 지수가 홀수라면 ((2*2) * (2*2)) * ((2*2) * (2*2)) * 2 가 된다.
- 재귀로 처리를 하면 시간복잡도는 O(logN) 이 된다.

#### - [피보나치(Fibonacci)](./2_Algorithm/8_DivideAndConquer/Fibonacci.md "Fibonacci")
- 피보나치수열은 0 1 1 2 3 5 8 13 21 34 ..... 이렇게 앞의 두 숫자를 더해서 값이 나온것을 말한다.
- 일반적으로 피보나치 수열을 구할때는

> if n == 0 { return 0 }<br>
else if n == 1 || n == 2 { return 1 }<br>
fibonacci(n - 1) + fibonacci(n - 2)

- 이런식으로 나타낼 수 있다.
- 이 공식으로 하면 O(n^2) 의 시간복잡도가 걸린다. 45번째 피보나치 수를 구했을때 10초 이상이 나왔다.
- 행렬과 분할정복으로 구하면 O(logN) 의 시간복잡도가 걸린다. 45번째 피보나치 수를 구했을때 0.0005초가 나왔다.
- 100번째 피보나치 수를 구했을때 0.004초가 나왔다.
- 피보나치수를 행렬에 대입한 다음 그 행렬을 분할한 다음 곱한다.


### 9)동적 계획법(Dynamic Programing)

- 분할 정복은 문제를 위에서부터 아래로 분할 Top-Down
- 동적 계획법은 제일 작은 부분부터 상위에 있는 문제로 풀어나감 Bottom-Up
- 동적 계획법의 동작방식은
- 1. 문제를 부분 문제로 나눔
- 2. 가장 작은 부분 문제부터 해를 구한 뒤 테이블에 저장
- 3. 테이블에 저장되어 있는 부분 문제의 해를 이용하여 점차적으로 상위 부분 문제의 최적해를 구함

#### - [피보나치(Fibonacci)](./2_Algorithm/9_DynamicPrograming/Fibonacci.md "Fibonacci")
- 0번째는 0, 1번째는 1로 정의되어 있는 테이블에 저장한다.
- 2번째 부터는 미리 테이블에 저장되어있던 n-1과 n-2로 값을 구한 뒤 테이블에 저장
- 시간복잡도는 O(n)

#### - [최장 공통 부분(LCS)](./2_Algorithm/9_DynamicPrograming/LCS.md "LCS")
- 두개의 문자열중 공통으로 존재하는 부분 순서를 말한다.
- ABCDXYZ, BCDEYZ 두개의 글자중 공통 부분 수열은 BCDYZ 이다.
- 왼쪽과 제일 위는 다 0으로 넣는다.
- 왼쪽부터 오른쪽, 위쪽부터 아래쪽까지 반복을 해서
- 이전값과 비교를한다.
- 문자열의 길이를 알아내는건 시간복잡도 O(mn) 이다.


### 10)탐욕 알고리즘(Greedy)

- 1. 해 선택: 현재 상태에서 부분 문제의 최적해를 구한 뒤, 이를 부분해 집합에 추가
- 2. 실행 가능성 검사: 새로운 부분해 집합이 실행가능한지 확인. 문제의 제약 조건을 위반하지 않는지를 검사
- 3. 해 검사: 새로운 부분해 집합이 문제의 해가 되는지를 확인. 아직 전체 문제의 해가 완성되지 않았다면 다시 1. 번의 해 선택부터 시작

#### - [거스름돈 계산(Change)](./2_Algorithm/10_Greedy/Change.md "Change")
- 가장 큰 단위의 동전부터 그 단위가 금액에 비교해 최대가 될수 있는 갯수를 구한다.

#### - 크루스칼 최소 신장 트리

#### - 다익스트라 최단 경로 알고리즘

#### - 프림 최소 신장 트리

#### - 허프만 트리

### 11)백트래킹(BackTracking)

- 1. 해를 찾아 나가는 과정은 '루트'에서 부터 출발
- 2. 현재 위치한 부분해에서 선택 가능한 다음 부분해의 목록을 얻음
- 3. 2번에서 얻은 목록의 부분해들을 하나씩 방문
- 4. 방문한 부분해가 해가 요구하는 조건을 만족시키면 그자리에서 2,3번 과정을 수행하고 그렇지 않으면 이전 부분해로 돌아 나와 다른 부분해를 시도
- 5. 최종해를 얻을 때까지, 또는 모든 경우의 수를 확인해도 해가 없을을 확인했을 때까지 2~4번과정 반복

#### - [미로탈출(Maze)](./2_Algorithm/11_BackTracking/Maze.md "Maze")
- 시작점을 S 골을 G 벽을 # 지나온길을 +
- S를 현재위치로 놓고 이동방향을 북, 남, 동, 서로 시작
- 현재 위치에서 가고자 하는 방향에 대해 이동 가능한지 확인
- 이동 가능향 방향이면 이동
- 다시 북, 남, 동, 서로 이동 시작
- 사방으로 이동이 안되면 이전 위치로 돌아감
- 출구를 찾거나 미로 내 모든 길을 방문할때 까지 반복

#### - N_Queens

### 12) 기타(ETC)

#### - 정렬 - 이미 정렬되어 있는 경우 필요없는 비교를 수행하지 않고 함수를 종료할수 있게 수정

#### - 정렬 - 병합정렬을 재귀없이

#### - 팩토리얼을 분할정복으로

#### - 백트래킹 스도쿠

#### - 부분집합(DP)

#### - 동전 거스름돈

#### - 배낭(Knapsack)(DP)

#### - 최대 공약수(Greatest Common Divisor:GCD)
- 두 정수의 약수 중에서 가장 큰 공통의 약수(나누어 지는 수)
- 유클리드 호제법 (GCD 구하기)

#### - 최소 공배수 계산 (LCM)
- 두 정수 A,B 일때 A=GCD*a, B=GCD*b (a,b는 서로소)
- A*B = (GCD*GCD)* a*b, A*B/GCD = GCD*a*b (최소 공배수)

#### - 소수 구하기
- 2 ~ sqrt(N) 까지 정수로 나누어 보는 방법(에라토스테네스의 체 (Optimized Sieve of Erathosthenes))
- 기타 방법들 정리 : http://soyoja.com/160

#### - 미로 탐색
- Right hand on wall 오른손을 미로 벽에 대고 움직임
- 저장된 좌표리스트에서 중복되는 좌표 부분 잘라냄

#### - 하노이의 탑 (재귀 호출)
#### - Flood Fill : 그래픽에서 색칠하기
#### - Fractal Tree : 일정패턴으로 반복으로 나무 모양 그리기
#### - 파일 찾기 : 파일을 찾기 시작하는데 서브 폴더 모두 뒤지기

#### 서로소 집합(disjoint-sets)

#### 완전 검색(Brute-force)
-순열(loop)
 서로 다른 n개 중 r 뽑아 나열하는 것(순서가 있음)
 nPr = n*(n-1)* (n-2)* (n-r+1), 5P2 = 5*4
 생성 방법 loop, 재귀
-부분집합(power set)
 집합에 포함된 원소를 선택하는 것
 생성 방법 binary counting, 재귀
 또 다른 방법
 동전 거스름돈 탐색, 전체 탐색
 예) knapsack(Brute-force)
-조합
 서로 다른 n개 중 r개를 순서없이 골라 내는 것
 nCr = n!/((n-r!)* r!), nCr = n-1Cr-1+n-1Cr, nC0 = 1
 생성 방법 재귀
-외판원 문제(TSP)
