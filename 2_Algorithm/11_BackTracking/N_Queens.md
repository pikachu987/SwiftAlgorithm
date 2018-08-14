# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### N개의 퀸(N Queens)

```swift
func findQueen(_ chess: inout [Int], row: Int, cnt: inout Int) {
  /// 현재 row를 검사, 만약 해당 row에서 다른 퀸에게 위협받고 있으면 n번째 열은 종료
  if isThreatened(chess, row: row) { return }
  /// row가 마지막까지 오면 n번째 열 성공
  if row == chess.count-1 {
      chessPrint(chess, cnt: cnt)
      cnt += 1
  } else {
      /// 열이 0부터 마지막열까지 반복
      for element in 0..<chess.count {
          /// 다음 로우에 값을 넣고 재귀 호출
          /// 값을 넣었는데 위협을 받으면 재귀 종료
          chess[row+1] = element
          findQueen(&chess, row: row+1, cnt: &cnt)
      }
  }
}

/// 가로,세로,사선 검사
func isThreatened(_ chess: [Int], row: Int) -> Bool {
  var currentRow = 0
  while currentRow < row {
      if chess[row] == chess[currentRow] || abs(chess[row] - chess[currentRow]) == abs(row - currentRow) {
          return true
      }
      currentRow += 1
  }
  return false
}

func chessPrint(_ chess: [Int], cnt: Int) {
  print("\(cnt) 번째 답")
  for i in chess {
      var text = ""
      for j in 0..<chess.count {
          if i == j {
              text.append("[Q]")
          } else {
              text.append("[ ]")
          }
      }
      print(text)
  }
  print("")
}

func queen(_ n: Int) {
  var cnt = 0
  var chess = [Int].init(repeating: -1, count: n)
  /// 체스 0열 0번째부터 퀸을 넣고 0열 n-1번째까지 퀸을 찾는다.
  for i in 0..<chess.count {
      chess[0] = i
      findQueen(&chess, row: 0, cnt: &cnt)
  }
  print("총 \(cnt)개의 답이 있습니다.")
}

queen(5)
```
```swift
0 번째 답
[Q][ ][ ][ ][ ]
[ ][ ][Q][ ][ ]
[ ][ ][ ][ ][Q]
[ ][Q][ ][ ][ ]
[ ][ ][ ][Q][ ]

1 번째 답
[Q][ ][ ][ ][ ]
[ ][ ][ ][Q][ ]
[ ][Q][ ][ ][ ]
[ ][ ][ ][ ][Q]
[ ][ ][Q][ ][ ]

2 번째 답
[ ][Q][ ][ ][ ]
[ ][ ][ ][Q][ ]
[Q][ ][ ][ ][ ]
[ ][ ][Q][ ][ ]
[ ][ ][ ][ ][Q]

3 번째 답
[ ][Q][ ][ ][ ]
[ ][ ][ ][ ][Q]
[ ][ ][Q][ ][ ]
[Q][ ][ ][ ][ ]
[ ][ ][ ][Q][ ]

4 번째 답
[ ][ ][Q][ ][ ]
[Q][ ][ ][ ][ ]
[ ][ ][ ][Q][ ]
[ ][Q][ ][ ][ ]
[ ][ ][ ][ ][Q]

5 번째 답
[ ][ ][Q][ ][ ]
[ ][ ][ ][ ][Q]
[ ][Q][ ][ ][ ]
[ ][ ][ ][Q][ ]
[Q][ ][ ][ ][ ]

6 번째 답
[ ][ ][ ][Q][ ]
[Q][ ][ ][ ][ ]
[ ][ ][Q][ ][ ]
[ ][ ][ ][ ][Q]
[ ][Q][ ][ ][ ]

7 번째 답
[ ][ ][ ][Q][ ]
[ ][Q][ ][ ][ ]
[ ][ ][ ][ ][Q]
[ ][ ][Q][ ][ ]
[Q][ ][ ][ ][ ]

8 번째 답
[ ][ ][ ][ ][Q]
[ ][Q][ ][ ][ ]
[ ][ ][ ][Q][ ]
[Q][ ][ ][ ][ ]
[ ][ ][Q][ ][ ]

9 번째 답
[ ][ ][ ][ ][Q]
[ ][ ][Q][ ][ ]
[Q][ ][ ][ ][ ]
[ ][ ][ ][Q][ ]
[ ][Q][ ][ ][ ]

총 10개의 답이 있습니다.
```
