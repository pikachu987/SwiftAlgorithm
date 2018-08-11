# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 거듭 제곱(Exponentiation)

```swift
func power(_ num: Int, cnt: Int) -> Int{
  if cnt == 0 { return 1 }
  else if cnt == 1 { return num }
  else if num == 0 || num == 1 { return 1 }
  if cnt % 2 == 0 { /// 짝수
      let newNum = power(num, cnt: cnt/2)
      return newNum * newNum
  } else { /// 홀수
      let newNum = power(num, cnt: (cnt - 1)/2)
      return newNum * newNum * num
  }
}

print(power(2, cnt: 8))
print(power(2, cnt: 16))
print(power(2, cnt: 17))
print(power(2, cnt: 24))
print(power(2, cnt: 27))
print(power(4, cnt: 8))
print(power(16, cnt: 8))
```
```swift
256
65536
131072
16777216
134217728
65536
4294967296
```
