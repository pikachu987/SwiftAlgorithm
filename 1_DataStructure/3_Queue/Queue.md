# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

### 큐(Queue)

#### [링크드리스트(LinkedList)](../1_List/LinkedList.md "LinkedList")

```swift
import UIKit

class Queue<E> {
    private var list = LinkedList<E>()

    var isEmpty: Bool {
        return self.list.isEmpty
    }

    var count: Int {
        return self.list.count
    }

    func enqueue(_ value: Node<E>) {
        self.list.append(value)
    }

    @discardableResult
    func dequeue() -> Node<E>? {
        return self.list.removeFirst()
    }
}

```
