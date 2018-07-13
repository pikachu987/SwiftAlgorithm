# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 검색(Search)

```swift
let array = [2, 3, 5, 12, 35, 24, 56, 78, 25]

func search(_ value: Int) -> Int {
    for (index, element) in array.enumerated() {
        if element == value {
            return index
        }
    }
    return -1
}

print(search(0))
print(search(5))
print(search(24))
print(search(25))
print(search(2))
```
```swift
-1
2
5
8
0
```
