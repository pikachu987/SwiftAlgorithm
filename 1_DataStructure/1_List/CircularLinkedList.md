# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 환형연결리스트(CircularLinkedList)

```swift
class Node<Int> {
    var value: Int

    var next: Node<Int>?

    init(_ value: Int) {
        self.value = value
    }
}

class CircularList {
    private var head: Node<Int>?

    init() { }

    func insertFirst(_ node: Node<Int>) {
        if self.head == nil {
            self.head = node
            self.head?.next = self.head
        } else {
            var tempNode = self.head
            while tempNode?.next?.value != self.head?.value {
                tempNode = tempNode?.next
            }
            node.next = tempNode?.next
            tempNode?.next = node
            self.head = node
        }
    }

    func insertLast(_ node: Node<Int>) {
        if self.head == nil {
            self.head = node
            self.head?.next = self.head
        } else {
            var tempNode = self.head
            while tempNode?.next?.value != self.head?.value {
                tempNode = tempNode?.next
            }
            node.next = tempNode?.next
            tempNode?.next = node
        }
    }

    func insertMiddle(_ preNode: Node<Int>, node: Node<Int>) {
        if self.head == nil {
            self.head = node
            self.head?.next = self.head
        } else {
            var tempNode = self.head
            while tempNode?.next?.value != preNode.value {
                tempNode = tempNode?.next
            }
            tempNode = tempNode?.next
            node.next = tempNode?.next
            tempNode?.next = node
        }
    }

    func deleteFirst() {
        var tempNode = self.head
        while tempNode?.next?.value != self.head?.value {
            tempNode = tempNode?.next
        }
        let old = tempNode?.next
        self.head = old?.next
        tempNode?.next = self.head
    }
}

extension CircularList {
    var description: String {
        var node = self.head
        var str = "["
        while node?.next?.value != self.head?.value {
            if let value = node?.value {
                str.append("\(str == "[" ? "\(value)" : ", \(value)")")
            }
            node = node?.next
        }
        if let node = node {
            str.append("\(str == "[" ? "\(node.value)" : ", \(node.value)")")
        }
        str.append("]")
        return str
    }
}

var array = CircularList()
array.insertFirst(Node(1))
array.insertFirst(Node(2))
array.insertFirst(Node(3))
let node4 = Node(4)
array.insertLast(node4)
array.insertLast(Node(5))
array.insertLast(Node(6))
array.insertMiddle(node4, node: Node(7))
array.insertLast(Node(8))
array.deleteFirst()
print(array.description)

```
