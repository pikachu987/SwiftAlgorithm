# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm)

### 이진탐색(BinarySearch)

```swift
var array = [1, 3, 5, 8, 10, 12, 17, 56, 97, 130, 255, 549, 1823, 5999, 6023]

func search(_ value: Int, start: Int, end: Int) -> Int {
    let mid = (start + end) / 2
    let searchValue = array[mid]
    if searchValue > value {
        return search(value, start: start, end: mid - 1)
    } else if searchValue < value {
        return search(value, start: mid + 1, end: end)
    } else {
        return mid
    }
}

print(search(56, start: 0, end: array.count))
```
```swift
7
```
