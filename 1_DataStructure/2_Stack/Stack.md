# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 스택(Stack)

##### [연결리스트(LinkedList)](../1_List/LinkedList.md "LinkedList")

```swift
class Stack<E> {
    private var list = LinkedList<E>()

    var isEmpty: Bool {
        return self.list.isEmpty
    }

    var count: Int {
        return self.list.count
    }

    func push(_ value: Node<E>) {
        self.list.append(value)
    }

    @discardableResult
    func pop() -> Node<E>? {
        return self.list.removeLast()
    }
}

```
