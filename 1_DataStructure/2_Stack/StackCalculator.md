# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 스택계산기(StackCalculator)

#### [연결리스트(LinkedList)](../1_List/LinkedList.md "LinkedList")

중위표기법, 후위표기법

```swift

enum Equation: String {
    case `default` = ""
    case plus = "+"
    case minus = "-"
    case multiply = "*"
    case division = "/"
    case bracketsOpen = "("
    case bracketsClose = ")"

    var weight: Int {
        switch self {
        case .multiply, .division:
            return 9
        case .plus, .minus:
            return 7
        case .bracketsOpen:
            return 5
        default:
            return -1
        }
    }

    static func type(_ value: String) -> Equation {
        if value == Equation.plus.rawValue {
            return Equation.plus
        } else if value == Equation.minus.rawValue {
            return Equation.minus
        } else if value == Equation.multiply.rawValue {
            return Equation.multiply
        } else if value == Equation.division.rawValue {
            return Equation.division
        } else if value == Equation.bracketsOpen.rawValue {
            return Equation.bracketsOpen
        } else if value == Equation.bracketsClose.rawValue {
            return Equation.bracketsClose
        } else {
            return Equation.default
        }
    }

    func cal(_ value1: Int?,_ value2: Int?) -> Int {
        guard let value1 = value1, let value2 = value2 else { return 0 }
        if self == .plus { return value1 + value2 }
        else if self == .minus { return value1 - value2 }
        else if self == .multiply { return value1 * value2 }
        else if self == .division { return value1 / value2 }
        return 0
    }
}

class Stack<E> {
    private var array = [E]()

    var stackArray: [E] {
        return self.array
    }

    var isEmpty: Bool {
        return self.array.isEmpty
    }

    func push(_ value: E){
        self.array.append(value)
    }

    @discardableResult
    func pop() -> E? {
        if self.array.last != nil {
            let value = self.array.last
            self.array.removeLast()
            return value
        } else {
            return nil
        }
    }

    func peek() -> E? {
        return self.array.last
    }
}

extension String {
    func substring(from:Int = 0, length: Int) -> String {
        let range = self.index(self.startIndex, offsetBy: from)..<self.index(self.startIndex, offsetBy: from+length)
        return String(self[range])
    }

    var regularExpression: [String]? {
        do {
            let regex = try NSRegularExpression(pattern: "(\\d+|\\*|\\/|\\+|\\-|\\(|\\))", options: [])
            let matches = regex.matches(in: self, options: [], range: NSRange(location: 0, length: self.count))
            let values = matches.map({ self.substring(from: $0.range.location, length: $0.range.length) })
            return values.isEmpty ? nil : values
        } catch let err {
            print(err)
            return nil
        }
    }
}

func calculator(_ value: String) -> Int? {
  guard let values = value.regularExpression else { return nil }
  var list = [String]()
  let stack = Stack<Equation>()

  for element in values {
      let type = Equation.type(element)
      if type == .default { /// 숫자
          list.append(element)
      } else { /// 연산자
          if type == .bracketsOpen || stack.isEmpty { /// ( 이거나 스택이 비었을때
              stack.push(type)
          } else if type == .bracketsClose { /// ) 일때 다음 ( 가 아닐때까지 list으로 넣음
              if var equation = stack.pop() {
                  while !stack.isEmpty && equation != Equation.bracketsOpen {
                      list.append(equation.rawValue)
                      if let temp = stack.pop() {
                          equation = temp
                      }
                  }
              }
          } else if type.weight > (stack.peek()?.weight ?? -1) { /// 새로 추가되는 연산자의 가중치가 스택 맨위 가중치보다 높으면 추가
              stack.push(type)
          } else { /// 새로 추가되는 연산자의 가중치가 스택 맨위 가중치보다 낮으면 list로 옴긴다
              while !stack.isEmpty && stack.peek() != Equation.bracketsOpen && type.weight <= (stack.peek()?.weight ?? -1) {
                  if let temp = stack.pop() {
                      list.append(temp.rawValue)
                  }
              }
              stack.push(type)
          }
      }
  }

  /// 남은 스택 연산자들을 list로 옴긴다
  while !stack.isEmpty {
      if let temp = stack.pop() {
          list.append(temp.rawValue)
      }
  }

  print(list)

  let calculateStack = Stack<Int>()

  for element in list {
      let type = Equation.type(element)
      if type == .default { /// 값
          if let value = Int(element) {
              calculateStack.push(value)
          }
      } else { /// 연산자
          let value2 = calculateStack.pop() /// 제일뒤에값이 2번
          let value1 = calculateStack.pop() /// 그다음값이 1번
          calculateStack.push(type.cal(value1, value2))
      }
  }

  return calculateStack.pop()
}


let temp = "4*2+5*(2+1)+6/2"
print(calculator(temp))
```
```swift
["4", "2", "*", "5", "2", "1", "+", "*", "+", "6", "2", "/", "+"]
Optional(26)
```
