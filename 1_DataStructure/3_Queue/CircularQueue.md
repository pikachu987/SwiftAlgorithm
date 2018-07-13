# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 순환큐(CircularQueue)

##### [연결리스트(LinkedList)](../1_List/LinkedList.md "LinkedList")

```swift
class Node<E> {
  var value: E

  init(_ value: E) {
      self.value = value
  }
}

class CircularQueue<E> {
  private var array: [Node<E>?]
  private var front: Int /// head
  private var rear: Int /// tail

  init(_ count: Int) {
      self.array = [Node<E>?].init(repeating: nil, count: count)
      self.front = 0
      self.rear = 0
  }

  func enqueue(_ value: E) {
      self.enqueue(Node(value))
  }
  func enqueue(_ value: Node<E>) {
      if self.isFull() {
          print("CircularQueue Full")
      } else {
          /// 후단이 array사이즈보다 커지만 다시 0이됨
          self.rear = (self.rear + 1) % self.array.count
          self.array[self.rear] = value
      }
  }

  func isFull() -> Bool {
      if self.front < self.rear { /// 후단이 더 클때
          /// 후단+1 - 전단이 array사이즈와 같으면 풀
          return (self.rear + 1) - self.front == self.array.count
      } else { /// 전단이 더 클때
          /// 후단 +1 이 전단과 같으면 풀
          return self.rear + 1 == self.front
      }
  }

  @discardableResult
  func dequeue() -> Node<E>? {
      if self.rear == self.front { /// 전단과 후단이 같으면 비어있음
          print("CircularQueue Empty")
          return nil
      } else {
          var value: Node<E>?
          if self.front == self.array.count - 1 {
              /// 전단이 array사이즈-1 이랑 같을때 전단을 0으로
              self.front = 0
          } else {
              /// 전단 증가하기
              self.front += 1
          }
          value = self.array[self.front]
          self.array[self.front] = nil
          return value
      }
  }
}

extension CircularQueue {
  var desctiption: String {
      let str = self.array.reduce("") { (result, node) -> String in
          let value = node == nil ? "nil" : "\(node!.value)"
          return result == "" ? value : "\(result), \(value)"
      }
      return "[\(str)], 전단: \(self.front), 후단: \(self.rear)"
  }
}

let queue = CircularQueue<Int>(5)
queue.enqueue(1)
print(queue.desctiption)
queue.enqueue(2)
print(queue.desctiption)
queue.enqueue(3)
print(queue.desctiption)
queue.enqueue(4)
print(queue.desctiption)
queue.enqueue(5)
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.enqueue(6)
print(queue.desctiption)
queue.enqueue(7)
print(queue.desctiption)
queue.enqueue(8)
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.dequeue()
print(queue.desctiption)
queue.enqueue(9)
print(queue.desctiption)
queue.enqueue(10)
print(queue.desctiption)
queue.enqueue(11)
print(queue.desctiption)
queue.enqueue(12)
print(queue.desctiption)
queue.enqueue(13)
print(queue.desctiption)
```
```swift
[nil, 1, nil, nil, nil], 전단: 0, 후단: 1
[nil, 1, 2, nil, nil], 전단: 0, 후단: 2
[nil, 1, 2, 3, nil], 전단: 0, 후단: 3
[nil, 1, 2, 3, 4], 전단: 0, 후단: 4
CircularQueue Full
[nil, 1, 2, 3, 4], 전단: 0, 후단: 4
[nil, nil, 2, 3, 4], 전단: 1, 후단: 4
[nil, nil, nil, 3, 4], 전단: 2, 후단: 4
[6, nil, nil, 3, 4], 전단: 2, 후단: 0
[6, 7, nil, 3, 4], 전단: 2, 후단: 1
CircularQueue Full
[6, 7, nil, 3, 4], 전단: 2, 후단: 1
[6, 7, nil, nil, 4], 전단: 3, 후단: 1
[6, 7, nil, nil, nil], 전단: 4, 후단: 1
[nil, 7, nil, nil, nil], 전단: 0, 후단: 1
[nil, nil, nil, nil, nil], 전단: 1, 후단: 1
CircularQueue Empty
[nil, nil, nil, nil, nil], 전단: 1, 후단: 1
[nil, nil, 9, nil, nil], 전단: 1, 후단: 2
[nil, nil, 9, 10, nil], 전단: 1, 후단: 3
[nil, nil, 9, 10, 11], 전단: 1, 후단: 4
[12, nil, 9, 10, 11], 전단: 1, 후단: 0
CircularQueue Full
[12, nil, 9, 10, 11], 전단: 1, 후단: 0
```
