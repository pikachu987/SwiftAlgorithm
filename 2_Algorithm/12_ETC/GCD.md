# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 최대 공약수(GCD)

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

print(gcd(20, 4))
print(gcd(200, 4))
print(gcd(4, 4))
print(gcd(4, 5))
print(gcd(2, 9))
print(gcd(24, 12))
print(gcd(60, 48))
```
```swift
4
4
4
1
1
12
12
```
