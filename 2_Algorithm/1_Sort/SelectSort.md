# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 선택정렬(SelectSort)

```swift
func selectionSort(_ array: inout [Int]){
    for i in 0..<array.count{
        var tmp = i
        for j in i..<array.count{
            if array[tmp] > array[j]{//> ASC < DESC
                tmp = j
            }
        }
        (array[i], array[tmp]) = (array[tmp], array[i])
    }
}

var array = [5, 1, 2, 3, 4, 56, 12, 2, 3, 1, 7]
selectionSort(&array)
print(array)
```
```swift
[1, 1, 2, 2, 3, 3, 4, 5, 7, 12, 56]
```
