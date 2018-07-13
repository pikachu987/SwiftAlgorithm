# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm)

### 전진이동법(MoveToFrontMethod)

```swift
var array = [2, 3, 5, 12, 35, 24, 56, 78, 25]

func search(_ value: Int) -> Int {
    for (index, element) in array.enumerated() {
        if element == value {
            (array[0], array[index]) = (array[index], array[0])
            return index
        }
    }
    return -1
}

print(search(56))
print(search(56))
print(search(56))
print(search(2))
print(search(2))
print(search(56))
```
```swift
6
0
0
6
0
6
```
