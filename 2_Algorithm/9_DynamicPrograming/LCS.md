# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 최장 공통 부분(LCS)

```swift
/**
최장 공통 부분 수열
두가지가 존재하는데
공통 부분 문자열(Longest Common Substring)
공통 부분 수열(Longest Common Subsequence)
이 있다.
공통 부분 문자열은
ABCDXYZ
BCDEYZ
에서 BCD이다.
공통 부분 수열은
ABCDXYZ
BCDEYZ
에서 BCDYZ이다.
**/
func lcs(_ strA: [Character], _ strB: [Character]) -> ([[Int]], Int) {
   let cnt = (strA.count > strB.count ? strA.count : strB.count) + 1
   var lcsTable = [[Int]].init(repeating: [Int].init(repeating: 0, count: cnt), count: cnt)

   /// 제일 위는 다 0
   for i in 0...strA.count {
       lcsTable[i][0] = 0
   }
   /// 제일 왼쪽은 다 0
   for i in 0...strB.count {
       lcsTable[0][i] = 0
   }

   /// 왼쪽 위 부터 오른쪽 아래까지 답을 구함
   /// 제일 작은거부터 제일 큰거까지
   for i in 1...strA.count {
       for j in 1...strB.count {
           /// 문자열 내 두 요소가 같을때
           if strA[i-1] == strB[j-1] {
               /// 이전 값 + 1
               lcsTable[i][j] = lcsTable[i-1][j-1] + 1
           } else {
               if lcsTable[i][j-1] >= lcsTable[i-1][j] {
                   lcsTable[i][j] = lcsTable[i][j-1]
               } else {
                   lcsTable[i][j] = lcsTable[i-1][j]
               }
           }
       }
   }
   printTable(strA, strB, table: lcsTable)
   return (lcsTable, lcsTable[strA.count][strB.count])
}

/// lcs의 값을 추적한다.
func traceBack(_ strA: [Character], _ strB: [Character], m: Int, n: Int, table: [[Int]], lcs: inout String) {
   /// m과 n이 0일떄 리턴
   if m == 0 || n == 0 { return }

   if table[m][n] > table[m][n-1] &&
       table[m][n] > table[m-1][n] &&
       table[m][n] > table[m-1][n-1] {
       /// 현재 위치한 셀의 값이 왼쪽, 왼쪽위, 위 보다 크면 현재 셀의 값을 string의 앞에 넣고 왼쪽 위로 이동
       lcs = "\(strA[m-1])\(lcs)"
       traceBack(strA, strB, m: m-1, n: n-1, table: table, lcs: &lcs)
   } else if table[m][n] > table[m-1][n] &&
       table[m][n] == table[m][n-1] {
       /// 현재 셀의 값이 위쪽 셀값보다 크고 왼쪽 셀의 값과 같을때 왼쪽으로 이동
       traceBack(strA, strB, m: m, n: n-1, table: table, lcs: &lcs)
   } else {
       /// 위로 이동
       traceBack(strA, strB, m: m-1, n: n, table: table, lcs: &lcs)
   }
}

/// 출력
func printTable(_ strA: [Character], _ strB: [Character], table: [[Int]]) {
   var tmpStr = strB.reduce("", { "\($0) \($1)" })
   tmpStr.removeFirst()
   print("    \(tmpStr)")
   for (idx, array) in table.enumerated() {
       var txt = (idx != 0 && strA.count > idx) ? "\(strA[idx-1]) " : "  "
       for value in array {
           txt = "\(txt)\(value),"
       }
       txt.removeLast()
       print(txt)
   }
}

let startDate = Date()
let aStr = "WELL COME HELLO WORLD."
let bStr = "VERY GOOD SWIFT WORLD."
let value = lcs(Array(aStr), Array(bStr))
var lcsStr = ""
traceBack(Array(aStr), Array(bStr), m: aStr.count, n: bStr.count, table: value.0, lcs: &lcsStr)
let lastDate = Date()
let time = lastDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
print("value: \(value.1), time: \(time)")
print("lcsStr: \(lcsStr)")
```
```swift
    V E R Y   G O O D   S W I F T   W O R L D .
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
W 0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,1,1,1,1,1,1
E 0,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
L 0,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,2,2,2
L 0,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,2,2,2
  0,0,1,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2
C 0,0,1,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2
O 0,0,1,1,1,2,2,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3
M 0,0,1,1,1,2,2,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3
E 0,0,1,1,1,2,2,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3,3
  0,0,1,1,1,2,2,3,3,3,4,4,4,4,4,4,4,4,4,4,4,4,4
H 0,0,1,1,1,2,2,3,3,3,4,4,4,4,4,4,4,4,4,4,4,4,4
E 0,0,1,1,1,2,2,3,3,3,4,4,4,4,4,4,4,4,4,4,4,4,4
L 0,0,1,1,1,2,2,3,3,3,4,4,4,4,4,4,4,4,4,4,5,5,5
L 0,0,1,1,1,2,2,3,3,3,4,4,4,4,4,4,4,4,4,4,5,5,5
O 0,0,1,1,1,2,2,3,4,4,4,4,4,4,4,4,4,4,5,5,5,5,5
  0,0,1,1,1,2,2,3,4,4,5,5,5,5,5,5,5,5,5,5,5,5,5
W 0,0,1,1,1,2,2,3,4,4,5,5,6,6,6,6,6,6,6,6,6,6,6
O 0,0,1,1,1,2,2,3,4,4,5,5,6,6,6,6,6,6,7,7,7,7,7
R 0,0,1,2,2,2,2,3,4,4,5,5,6,6,6,6,6,6,7,8,8,8,8
L 0,0,1,2,2,2,2,3,4,4,5,5,6,6,6,6,6,6,7,8,9,9,9
D 0,0,1,2,2,2,2,3,4,5,5,5,6,6,6,6,6,6,7,8,9,10,10
  0,0,1,2,2,2,2,3,4,5,5,5,6,6,6,6,6,6,7,8,9,10,11
value: 11, time: 0.0208401679992676
lcs: E OO WORLD.
```
