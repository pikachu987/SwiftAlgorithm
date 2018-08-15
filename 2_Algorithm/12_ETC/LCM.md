# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 최소 공배수(LCM)

```swift
func gcd(_ a: Int, _ b: Int) -> Int {
  var a = a
  var b = b
  var r = 0
  while b != 0 {
      r = a%b
      a = b
      b = r
  }
  return a
}

func lcm(_ a: Int, _ b: Int) -> Int {
  return a * b / gcd(a, b)
}

print(lcm(20, 4))
print(lcm(200, 4))
print(lcm(4, 4))
print(lcm(4, 5))
print(lcm(2, 9))
print(lcm(24, 12))
print(lcm(60, 48))
```
```swift
20
200
4
20
18
24
240
```
