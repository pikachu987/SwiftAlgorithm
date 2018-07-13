# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm)

### 이중연결리스트(DoubleLinkedList)

```swift
import UIKit

class Node<E> {
    var value: E

    weak var prev: Node<E>?
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
        if let tail = self.tail {
            value.prev = tail
            tail.next = value
        } else {
            self.head = value
        }
        self.tail = value
        self._count += 1
    }

    func insert(_ value: Node<E>, at: Int) {
        if at > self.count { return }
        if at == 0 {
            self.head?.next?.prev = value
            value.next = self.head
            self.head = value
        } else if at == self.count {
            self.tail?.next = value
            value.prev = self.tail
            self.tail = value
        } else {
            let node = self.object(at)
            let prev = node?.prev
            prev?.next = value
            value.prev = prev

            value.next = node
            node?.prev = value
        }
        if self.tail == nil { self.tail = value }
        self._count += 1
    }


    @discardableResult
    func removeFirst() -> Node<E>? {
        return self.remove(at: 0)
    }

    @discardableResult
    func removeLast() -> Node<E>? {
        return self.remove(at: self.count-1)
    }

    @discardableResult
    func remove(at: Int) -> Node<E>? {
        if at > self.count { return nil }
        var node: Node<E>?
        if at == 0 {
            node = self.head
            self.head = self.head?.next
            self.head?.prev = nil
            node?.next = nil
        } else if at == self.count-1 {
            node = self.tail
            self.tail = self.tail?.prev
            self.tail?.next = nil
        } else {
            let element = self.object(at)
            node = element
            let prev = element?.prev
            let next = element?.next
            prev?.next = next
            next?.prev = prev
        }
        if self.head == nil {
            self.tail = nil
        }
        self._count -= 1
        return node
    }

    func removeAll() {
        self.head = nil
        self.tail = nil
        self._count = 0
    }

    func object(_ at: Int) -> Node<E>? {
        if at < self.count/2{
            var node = self.head
            for _ in 0..<at{
                node = node?.next
            }
            return node
        } else {
            var node = self.tail
            for _ in (0..<self.count-at-1).reversed() {
                node = node?.prev
            }
            return node
        }
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
