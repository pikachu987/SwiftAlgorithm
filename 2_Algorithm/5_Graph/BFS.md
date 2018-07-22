# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 너비우선탐색(BFS)

<img src="adjacency_1.png" width="300px"/>


인접 행렬에서의 너비 우선 탐색

```swift
extension Array {
    mutating func offer(_ value: Element) {
        self.append(value)
    }
    func element() -> Element? {
        return self.first
    }
    mutating func poll() -> Element? {
        let first = self.first
        self.removeFirst()
        return first
    }
}

let nodeCount = 6 /// 총 노드

var array = [[Int]].init(repeating: [Int](repeating: 0, count: nodeCount), count: nodeCount)

func changeLine(_ node1: Int, _ node2: Int) {
    array[node1][node2] = 1
    array[node2][node1] = 1 /// 무방향일때 반대도 바꿔줌
}
changeLine(0, 1) /// 0노드와 1노드가 연결
changeLine(0, 2) /// 0노드와 2노드가 연결
changeLine(1, 2) /// 1노드와 2노드가 연결
changeLine(1, 3) /// 1노드와 3노드가 연결
changeLine(2, 3) /// 2노드와 3노드가 연결
changeLine(2, 4) /// 2노드와 4노드가 연결
changeLine(3, 4) /// 3노드와 4노드가 연결
changeLine(3, 5) /// 3노드와 5노드가 연결


var visit = [Bool].init(repeating: false, count: nodeCount) /// 방문한

func bfs() {
    var text = "노드: "

    var queue = [Int]()
    queue.offer(0)
    visit[0] = true

    while !queue.isEmpty {
        if let temp = queue.poll() {
            text.append(" \(temp) ->")

            for j in 0...nodeCount-1 {
                if array[temp][j] == 1 && visit[j] == false {
                    queue.offer(j)
                    visit[j] = true
                }
            }
        }
    }
    print(text)
}

bfs()

```
```swift
노드:  0 -> 1 -> 2 -> 3 -> 4 -> 5 ->
```


인접 리스트에서의 너비 우선 탐색

```swift
extension Array {
    mutating func offer(_ value: Element) {
        self.append(value)
    }
    func element() -> Element? {
        return self.first
    }
    mutating func poll() -> Element? {
        let first = self.first
        self.removeFirst()
        return first
    }
}

let nodeCount = 6 /// 총 노드

var array = [[Int]](repeating: [Int](), count: nodeCount)
array[0].append(1)
array[0].append(2)
array[1].append(0)
array[1].append(2)
array[1].append(3)
array[2].append(0)
array[2].append(1)
array[2].append(3)
array[2].append(4)
array[3].append(1)
array[3].append(2)
array[3].append(4)
array[3].append(5)
array[4].append(2)
array[4].append(3)
array[5].append(3)


var visit = [Bool].init(repeating: false, count: nodeCount)
func bfs() {
    var text = "노드: "

    var queue = [Int]()
    var hash = [Int: Bool]()

    queue.offer(0)

    while !queue.isEmpty {
        if let temp = queue.poll() {
            visit[temp] = true
            text.append(" \(temp) ->")

            for j in array[temp] {
                if !(hash[j] ?? false) && visit[j] == false {
                    queue.offer(j)
                    hash.updateValue(true, forKey: j)
                }
            }
        }
    }
    print(text)
}

bfs()
```
```swift
노드:  0 -> 1 -> 2 -> 3 -> 4 -> 5 ->
```
