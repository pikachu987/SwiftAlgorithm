# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm)

### 트리(Tree)

```swift
class Node<E> {
    var value: E

    var leftChild: Node<E>?
    var rightSibling: Node<E>?

    init(_ value: E) {
        self.value = value
    }
}

extension Node {
    func append(_ node: Node<E>) {
        if self.leftChild == nil {
            self.leftChild = node
        } else {
            var tempNode = self.leftChild
            while tempNode?.rightSibling != nil {
                tempNode = tempNode?.rightSibling
            }
            tempNode?.rightSibling = node
        }
    }

    func printTree(_ depth: Int = 0) {
        var indentation = ""
        for _ in 0..<depth {
            indentation.append("-")
        }
        print("\(indentation)\(self.value)")
        self.leftChild?.printTree(depth + 1)
        self.rightSibling?.printTree(depth)
    }
}


let root = Node("ROOT")
let nodeA = Node("A")
let nodeB = Node("B")
let nodeC = Node("C")
let nodeD = Node("D")
let nodeE = Node("E")
let nodeF = Node("F")
let nodeG = Node("G")

root.append(nodeA)
nodeA.append(nodeB)
nodeA.append(nodeC)
nodeA.append(nodeD)
root.append(nodeE)
nodeC.append(nodeF)
nodeF.append(nodeG)
root.printTree()
```
```swift
ROOT
-A
--B
--C
---F
----G
--D
-E
```
