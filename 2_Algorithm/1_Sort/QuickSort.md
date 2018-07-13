# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 퀵정렬(QuickSort)

```swift
func quickSort(_ array: inout [Int], left: Int, right: Int){
    var left = left
    var right = right

    var pivot = array[left]
    let l_hold = left
    let r_hold = right
    while left < right {

        /// 값이 선택한 피봇과 같거나 크다면 이동할 필요가 없음
        while array[right] >= pivot && left < right {
            right -= 1
        }

        /// 그렇지 않고 값이 피봇보다 작다면 피봇의 위치에 현재 값을 넣는다
        if left != right{
            array[left] = array[right]
        }

        /// 왼쪽부터 현재위치까지 값을 읽어들이면서 피봇보다 큰 값이 있다면 값을 이동한다
        while array[left] <= pivot && left < right {
            left += 1
        }
        if left != right{
            array[right] = array[left]
            right -= 1
        }
    }

    /// 모든 스캔이 끝났다면 피봇값을 현재 위치에 입력한다. 이제 피봇을 기준으로 왼쪽에는 피봇보다 작거나 같은 값만 남음
    array[left] = pivot
    pivot = left
    left = l_hold
    right = r_hold

    /// 재귀
    if left < pivot{
        quickSort(&array, left: left, right: pivot-1)
    }
    if right > pivot{
        quickSort(&array, left: pivot+1, right: right)
    }
}

var array = [5, 1, 2, 3, 4, 56, 12, 2, 3, 1, 7]
quickSort(&array, left: 0, right: array.count-1)
print(array)
```
```swift
[1, 1, 2, 2, 3, 3, 4, 5, 7, 12, 56]
```
