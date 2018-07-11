# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

### 스택(Stack)

##### [연결리스트(LinkedList)](../1_List/LinkedList.md "LinkedList")

```swift
import UIKit

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
