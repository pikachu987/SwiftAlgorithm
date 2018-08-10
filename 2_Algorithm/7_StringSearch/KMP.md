# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### KMP 알고리즘(KMP)

```swift
func getText() -> String{
  do {
      guard let path = Bundle.main.path(forResource: "example", ofType: "txt") else{ return "" }
      guard let url = URL(string: path) else { return "" }
      return try String(contentsOfFile: url.absoluteString)
  } catch { return "" }
}

/// 첫글자 부터 prefix == suffix 될수 있는 최대의 길이를 구함
/// ABA = 1
/// ABCAB = 2
/// ABCABC = 3
/// ABCDABC = 3
func getPi(_ pattern: [Character]) -> [Int] {
  let m = pattern.count
  var j = 0
  /// 패턴의 길이만큼 array를 만들고 초기값 0 을 줌
  var pi = [Int].init(repeating: 0, count: m)

  /// 1부터 패턴의 길이까지 반복
  for i in 1..<m {
      /// j가 0보다 크고 패턴 i번째랑 패턴 j번째가 다르면 패턴 i번쨰랑 패턴 j 번째가 같아질때까지 반복
      /// 패턴 i번째랑 패턴 j번째가 같으면 넘어간다.
      while j > 0 && pattern[i] != pattern[j] {
          /// pi j-1번째로 j를 바꾼다.
          j = pi[j-1]
      }
      /// 패턴 i번째와 패턴 j번째가 같으면 j를 증가하고 pi i번째에 j를 넣는다
      if pattern[i] == pattern[j] {
          j += 1
          pi[i] = j
      }
  }
  return pi
}


func kmp(_ text: [Character], pattern: [Character]) {
  if text.count == 0 {
      print("text가 없습니다.")
      return
  }
  if pattern.count == 0 {
      print("pattern이 없습니다.")
      return
  }
  let startDate = Date()

  /// 매칭된 문자의 index를 담음
  var ans = [(Int, Int)]()
  var pi = getPi(pattern)

  let textCount = text.count
  let patternCount = pattern.count
  var j = 0

  for i in 0..<textCount {
      /// j가 0보다 크고 텍스트 i번째랑 패턴 j번째가 다르면 텍스트 i번쨰랑 패턴 j 번째가 같아질때까지 반복
      /// 패턴 i번째랑 패턴 j번째가 같으면 넘어간다.
      /// 일치했던 정보와 pi배열을 이용해서 중간 단계를 뛰어넘는 부분
      /// 한번만 j = p[j-1]하는게 아니라 while를 하는 이유는
      /// 주어진 정보로 최대한 중간 단계를 뛰어 넘기 위해 반복문을함
      /// 예를들어 ABABABC에서 ABC를 찾는다고하면 AB가 일단 일치했으니까 j가 증가함
      /// 그리고 첫AB에서 C가 없으니까 다음으로 넘어갈때 B로 가는게 아니라 다음 A로 뛰어넘는다.
      while j > 0 && text[i] != pattern[j] {
          /// pi j-1번째로 j를 바꾼다.
          j = pi[j-1]
      }
      /// 텍스트 i번째와 패턴 j번째가 같으면
      if text[i] == pattern[j] {
          /// j가 패턴길이와 같으면
          if j == patternCount-1 {
              /// 인덱스를 구한뒤 j를 pi[j]로 바꿈
              let index = i-patternCount+1
              ans.append((index, index+patternCount-1))
              j = pi[j]
          } else {
              j += 1
          }
      }
  }
  for (index, element) in ans.enumerated() {
      print("\(index) - \(element.0)번째~\(element.1)번째")
  }
  let endDate = Date()
  let timer = endDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
  print("총 \(text.count)글자에서 \(pattern) 패턴 찾기 - 걸린시간: \(timer)초, 찾은 패턴: \(ans.count)")
}

let text = getText()
print(text)

kmp(Array(text), pattern: Array("good"))
```
```swift
0 - 824번째~827번째
1 - 15519번째~15522번째
2 - 16814번째~16817번째
3 - 20841번째~20844번째
4 - 24922번째~24925번째
...
1009 - 3650846번째~3650849번째
1010 - 3651852번째~3651855번째
1011 - 3657369번째~3657372번째
1012 - 3660938번째~3660941번째
1013 - 3664802번째~3664805번째
총 3665494글자에서 ["g", "o", "o", "d"] 패턴 찾기 - 걸린시간: 0.341937065124512초, 찾은 패턴: 1014
```
