# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

### 버블정렬(BubbleSort)

```swift
import UIKit

func bubbleSort(_ array: inout [Int]){
    for i in 0..<array.count-1{
        for j in 1..<array.count-i{
            if array[j-1] > array[j]{
                (array[j-1], array[j]) = (array[j], array[j-1])
            }
        }
    }
}

var array = [5, 1, 2, 3, 4, 56, 12, 2, 3, 1, 7]
bubbleSort(&array)
print(array)
```
```swift
[1, 1, 2, 2, 3, 3, 4, 5, 7, 12, 56]
```