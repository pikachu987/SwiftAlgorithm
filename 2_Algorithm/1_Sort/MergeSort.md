# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm)

### 퀵정렬(QuickSort)

```swift
import UIKit

func mergeSort(_ array: inout [Int], left: Int, right: Int){
    if left < right{
        let mid = (left + right) / 2
        mergeSort(&array, left: left, right: mid)
        mergeSort(&array, left: mid+1, right: right)
        merge(&array, left: left, mid: mid, right: right)
    }
}

func merge(_ array: inout [Int], left: Int, mid: Int, right: Int){
    var i = left
    var j = mid + 1
    var k = left /// 결과 배열의 인덱스
    var tmp = [Int](repeating: 0, count: array.count)

    /// left 부터 mid 까지의 블록과 mid+1 부터 right까지의 블록을 서로 비교
    while i <= mid && j <= right {
        if array[i] <= array[j]{ /// left index값이 right index 값보다 작으면 left index값을 결과에 복사
            tmp[k] = array[i]
            i = i+1
        }else{
            tmp[k] = array[j] /// 아니면 right index 값을 결과에 복사
            j = j+1
        }
        k = k+1
    }

    /// left 블록의 값은 다 처리되었는데 right 블록의 index가 아직 남아있을 경우
    /// right index를 순차적으로 결과에 복사
    while i <= mid {
        tmp[k] = array[i]
        k = k+1
        i = i+1
    }
    /// left 블록의 index가 아직 남아 있을경우 left index를 순차적으로 결과에 복사
    while j <= right {
        tmp[k] = array[j]
        k = k+1
        j = j+1
    }
    for i in left...right{
        array[i] = tmp[i]
    }
}

var array = [5, 1, 2, 3, 4, 56, 12, 2, 3, 1, 7]
mergeSort(&array, left: 0, right: array.count-1)
print(array)
```
```swift
[1, 1, 2, 2, 3, 3, 4, 5, 7, 12, 56]
```
