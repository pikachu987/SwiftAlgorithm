# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

### 이진트리(BinaryTree)

```swift
class Node<E> {
    var value: E

    var left: Node<E>?
    var right: Node<E>?

    init(_ value: E) {
        self.value = value
    }
}

extension Node {
    // 전위순회
    func preorderPrint() {
        print("\(self.value)")
        self.left?.preorderPrint()
        self.right?.preorderPrint()
    }

    // 중위순회
    func inorderPrint() {
        self.left?.inorderPrint()
        print("\(self.value)")
        self.right?.inorderPrint()
    }

    // 후위순회
    func postorderPrint() {
        self.left?.postorderPrint()
        self.right?.postorderPrint()
        print("\(self.value)")
    }
}

let root = Node("ROOT")
let nodeA = Node("A")
let nodeB = Node("B")
let nodeC = Node("C")
let nodeD = Node("D")
let nodeE = Node("E")
let nodeF = Node("F")

root.left = nodeA
nodeA.left = nodeB
nodeA.right = nodeC
root.right = nodeD
nodeD.left = nodeE
nodeD.right = nodeF

print("preorder")
root.preorderPrint()
print("\ninorder")
root.inorderPrint()
print("\npostorder")
root.postorderPrint()
```
```swift
preorder
ROOT
A
B
C
D
E
F

inorder
B
A
C
ROOT
E
D
F

postorder
B
C
A
E
F
D
ROOT
```
