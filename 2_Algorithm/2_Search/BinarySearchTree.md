# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 이진탐색트리(BinarySearchTree)

```swift
class Node {
  var value: Int

  var left: Node?
  var right: Node?

  var minNode: Node? {
      if self.left == nil {
          return self
      } else {
          return self.left?.minNode
      }
  }

  init(_ value: Int) {
      self.value = value
  }
  func append(_ value: Int) {
      self.append(Node(value))
  }
  func append(_ node: Node) {
      if self.value > node.value {
          if let left = self.left {
              left.append(node)
          } else {
              self.left = node
          }
      } else if self.value < node.value {
          if let right = self.right {
              right.append(node)
          } else {
              self.right = node
          }
      }
  }

  func object(_ value: Int) -> Node? {
      if self.value > value {
          if let left = self.left {
              return left.object(value)
          } else {
              return nil
          }
      } else if self.value < value {
          if let right = self.right {
              return right.object(value)
          } else {
              return nil
          }
      } else {
          return self
      }
  }

  @discardableResult
  func remove(_ targetValue: Int) -> Node? {
      return self.remove(Node(targetValue))
  }

  @discardableResult
  func remove(_ targetNode: Node, parentNode: Node? = nil) -> Node? {
      if self.value > targetNode.value {
          if let left = self.left {
              return left.remove(targetNode, parentNode: self)
          } else {
              return nil
          }
      } else if self.value < targetNode.value {
          if let right = self.right {
              return right.remove(targetNode, parentNode: self)
          } else {
              return nil
          }
      } else {
          if self.left == nil && self.right == nil { /// 잎 노드
              if let parentLeft = parentNode?.left, parentLeft.value == self.value {
                  parentNode?.left = nil
              } else if let parentRight = parentNode?.right, parentRight.value == self.value {
                  parentNode?.right = nil
              }
          } else {
              if self.left != nil && self.right != nil { /// 양쪽다 자식이 있을경우
                  if let minNode = self.right?.minNode {
                      self.remove(minNode)
                      self.value = minNode.value
                  }
              } else { /// 한쪽만 자식이 있을 경우
                  var tempNode: Node?
                  if let left = self.left {
                      tempNode = left
                  } else if let right = self.right {
                      tempNode = right
                  }
                  if let parentLeft = parentNode?.left, parentLeft.value == self.value {
                      parentNode?.left = tempNode
                  } else if let parentRight = parentNode?.right, parentRight.value == self.value {
                      parentNode?.right = tempNode
                  }
              }
          }
      }
      return self
  }



  func inorder(_ txt: inout String) {
      self.left?.inorder(&txt)
      txt.append(txt == "" ? "\(self.value)" : ", \(self.value)")
      self.right?.inorder(&txt)
  }

  func inorderPrint() {
      var txt = ""
      inorder(&txt)
      txt.insert("[", at: txt.startIndex)
      txt.append("]")
      print(txt)
  }
}

let root = Node(50)
root.append(30)
root.append(60)
root.append(20)
root.append(70)
root.append(65)
root.append(34)
root.inorderPrint()
root.remove(65)
root.inorderPrint()
root.remove(20)
root.inorderPrint()
```
```swift
[20, 30, 34, 50, 60, 65, 70]
[20, 30, 34, 50, 60, 70]
[30, 34, 50, 60, 70]
```
