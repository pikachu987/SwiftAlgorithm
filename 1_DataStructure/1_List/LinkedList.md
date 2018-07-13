# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm)

### 연결리스트(LinkedList)

```swift
import UIKit

class Node<E> {
    var value: E

    var next: Node<E>?

    init(_ value: E) {
        self.value = value
    }
}

class LinkedList<E> {
    private var head: Node<E>?
    private var tail: Node<E>?
    private var _count = 0

    init() { }

    var count: Int {
        return self._count
    }

    var isEmpty: Bool {
        return self.head == nil
    }

    var first: Node<E>? {
        return self.head
    }

    var last: Node<E>? {
        return self.tail
    }


    func append(_ value: Node<E>) {
        if self.head == nil{ self.head = value }
        self.tail?.next = value
        self.tail = value
        self._count += 1
    }

    func insert(_ value: Node<E>, at: Int) {
        if at == 0 {
            value.next = self.head
            self.head = value
            if self.tail == nil { self.tail = self.head }
        }else {
            guard let node = self.object(at) else { return }
            value.next = node.next
            node.next = value
            if value.next == nil { self.tail = value }
        }
        self._count += 1
    }

    @discardableResult
    func removeFirst() -> Node<E>? {
        return self.remove(0)
    }

    @discardableResult
    func removeLast() -> Node<E>? {
        return self.remove(self.count-1)
    }

    @discardableResult
    func remove(_ at: Int) -> Node<E>? {
        if at > self.count-1 { return nil }
        var node: Node<E>?
        if at == 0 {
            node = self.head
            self.head = self.first?.next
            if self.head == nil { self.tail = nil }
        } else {
            var element = self.head
            for _ in 0..<at-1 {
                element = element?.next
            }
            node = element?.next
            element?.next = element?.next?.next
            if at == self.count-1 { self.tail = element }
        }
        if self.count != 0 { self._count -= 1 }
        return node
    }

    func removeAll() {
        self.head = nil
        self.tail = nil
        self._count = 0
    }

    func object(_ at: Int) -> Node<E>? {
        var node = self.head
        for _ in 0..<at {
            node = node?.next
        }
        return node
    }

}

extension LinkedList {
    public var description: String {
        var node = self.head
        var str = "["
        while node != nil {
            if let value = node?.value {
                str.append("\(str == "[" ? "\(value)" : ", \(value)")")
            }
            node = node?.next
        }
        str.append("]")
        return str
    }
}

var array = LinkedList<Int>()
array.append(Node(0))
array.append(Node(1))
array.append(Node(2))
array.append(Node(3))

```
