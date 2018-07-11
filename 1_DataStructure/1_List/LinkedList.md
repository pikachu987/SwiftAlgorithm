# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

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
            guard let node = self.object(at: at) else { return }
            value.next = node.next
            node.next = value
            if value.next == nil { self.tail = value }
        }
        self._count += 1
    }

    func removeFirst() {
        self.remove(at: 0)
    }

    func removeLast() {
        self.remove(at: self.count-1)
    }

    func remove(at: Int) {
        if at > self.count-1 { return }
        if at == 0 {
            self.head = self.first?.next
            if self.head == nil { self.tail = nil }
        } else {
            var node = self.head
            for _ in 0..<at-1 {
                node = node?.next
            }
            node?.next = node?.next?.next
            if at == self.count-1 { self.tail = node }
        }
        if self.count != 0 { self._count -= 1 }
    }

    func removeAll() {
        self.head = nil
        self.tail = nil
        self._count = 0
    }

    func object(at: Int) -> Node<E>? {
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
