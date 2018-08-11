# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 피보나치(Fibonacci)

```swift
func fibonacci(_ n: Int) -> Double {
  if n == 0 || n == 1 { return Double(n) }
  var fibonacciTable = [Double].init(repeating: 0, count: n+1)
  fibonacciTable[0] = 0
  fibonacciTable[1] = 1
  for i in 2...n {
      fibonacciTable[i] = fibonacciTable[i-1] + fibonacciTable[i-2]
  }
  return fibonacciTable[n]
}
let startDate = Date()
let value = fibonacci(45)
let lastDate = Date()
let time = lastDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
print("value: \(value), time: \(time)")
```
```swift
value: 1134903170.0, time: 0.00279021263122559
```
