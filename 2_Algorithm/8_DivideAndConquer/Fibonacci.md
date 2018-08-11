# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 피보나치(Fibonacci)

```swift
/**
피보나치 수로 행렬을 만들면
[ F2 F1 ]  =  [ 1 1 ]
[ F1 F0 ]     [ 1 0 ]
n번째 피보나치 수를 Fn이라고 하면
                       n
[ Fn+1 Fn   ] = [ 1 1 ]
[ Fn   Fn-1 ]   [ 1 0 ]
이렇게 나타낼 수 있다.

 n/2       n/2       n
A     *   A     =   A
의 식을 활용하면

                      n             n/2             n/2
[ Fn+1 Fn   ] = [ 1 1 ]   =   [ 1 1 ]     *    [ 1 1 ]
[ Fn   Fn-1 ]   [ 1 0 ]       [ 1 0 ]          [ 1 0 ]
이렇게 분할정복으로 나타낼 수 있다.
**/

struct Matrix {
   var data = [[Int]].init(repeating: [Int].init(repeating: 0, count: 2), count: 2)
   init() {
       self.data[0][0] = 1
       self.data[0][1] = 1
       self.data[1][0] = 1
       self.data[1][1] = 0
       /**
        2*2 의 행렬을 만들고
        [ F2 F1 ]  =  [ 1 1 ]
        [ F1 F0 ]     [ 1 0 ]
        피보나치 값을 대입한다.
        0 1 1 2
        **/
   }
}
/**
행렬의 곱셈

 [ a b ] * [ e f ] = [ ae+bg af+bh]
 [ c d ]   [ g h ]   [ ce+dg cf+dh]

ex) [ 5 6 ] * [ 1 2 ] = [ 5*1 + 6*3  5*2 + 6*4 ]
    [ 7 8 ]   [ 3 4 ]   [ 7*1 + 8*3  7*2 + 8*4 ]

     -----    --- ---
    | 5 6 |  | 1 | 2 |
     -----   |   |   |
    | 7 8 |  | 3 | 4 |
     -----    ___ ___
    이런식으로 곱셈이 된다.
**/
func multiply(_ aMatrix: Matrix, _ bMatrix: Matrix) -> Matrix {
   var cMatrix = Matrix()
   cMatrix.data[0][0] = aMatrix.data[0][0]*bMatrix.data[0][0] + aMatrix.data[0][1]*bMatrix.data[1][0]
   cMatrix.data[0][1] = aMatrix.data[0][0]*bMatrix.data[1][0] + aMatrix.data[0][1]*bMatrix.data[1][1]
   cMatrix.data[1][0] = aMatrix.data[1][0]*bMatrix.data[0][0] + aMatrix.data[1][1]*bMatrix.data[1][0]
   cMatrix.data[1][1] = aMatrix.data[1][0]*bMatrix.data[1][0] + aMatrix.data[1][1]*bMatrix.data[1][1]
   return cMatrix
}
func power(_ matrix: Matrix, n: Int) -> Matrix {
   var matrix = matrix
   if n > 1 {
       /// 1보다 클때 n을 반으로 분할한 뒤 재귀
       matrix = power(matrix, n: n/2)
       /// 행렬을 곱한다.
       matrix = multiply(matrix, matrix)

       /// 홀수일때 n이 1인 행렬을 한번 더 곱해준다.
       if n%2 == 1 {
           matrix = multiply(matrix, Matrix())
       }
   }
   return matrix
}

func fibonacci(_ n: Int) -> Int {
   if n == 0 { return 0 }
   let matrix = power(Matrix(), n: n)
   return matrix.data[0][1]
}

let startDate = Date()
let value = fibonacci(45)
let lastDate = Date()
let time = lastDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
print("value: \(value), time: \(time)")
```
```swift
value: 1134903170, time: 0.000518083572387695
```
