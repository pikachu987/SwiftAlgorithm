# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

### 삽입정렬(InsertSort)

```swift
import UIKit

func insertSort(_ array: inout [Int]){
    for i in 1..<array.count{
        let key = array[i]
        var j = i-1
        while j >= 0 && key < array[j] {
            (array[j], array[j+1]) = (array[j+1], array[j])
            j -= 1
        }
        array[j+1] = key
    }
}

var array = [5, 1, 2, 3, 4, 56, 12, 2, 3, 1, 7]
insertSort(&array)
print(array)
```
```swift
[1, 1, 2, 2, 3, 3, 4, 5, 7, 12, 56]
```
