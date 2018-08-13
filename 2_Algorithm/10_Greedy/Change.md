# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 거스름돈(Change)

```swift
let units = [10, 50, 100, 500, 1000, 5000, 10000, 50000]
func getChange(_ amount: Int) {
    let units = units.sorted(by: { $0 > $1 })
    var amount = amount
    var unitMap = [Int: Int]()
    for unit in units {
        let count = countCoins(amount, unit: unit)
        unitMap.updateValue(count, forKey: unit)
        amount -= count*unit
    }
    unitMap.keys.forEach { unit in
        if let count = unitMap[unit] {
            print("\(unit)원짜리 \(count)개")
        }
    }
}
/// 현재 단위의 동전과 현재 금액을 비교
func countCoins(_ amount: Int, unit: Int) -> Int {
    var amount = amount
    var unitCount = 0
    while amount >= unit {
        unitCount += 1
        amount -= unit
    }
    return unitCount
}
getChange(2890)
```
```swift
5000원짜리 0개
10원짜리 4개
500원짜리 1개
10000원짜리 0개
1000원짜리 2개
100원짜리 3개
50000원짜리 0개
50원짜리 1개
```
