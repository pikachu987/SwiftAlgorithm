# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 전수조사법(BruteForce)

```swift
func getText() -> String{
  do {
      guard let path = Bundle.main.path(forResource: "example", ofType: "txt") else{ return "" }
      guard let url = URL(string: path) else { return "" }
      return try String(contentsOfFile: url.absoluteString)
  } catch { return "" }
}

func bruteForce(_ text: [Character], pattern: [Character]) {
  if text.count == 0 {
      print("text가 없습니다.")
      return
  }
  if pattern.count == 0 {
      print("pattern이 없습니다.")
      return
  }
  var cnt = 0
  let startDate = Date()
  for i in 0..<text.count-1 { /// 전체 텍스트를 반복
      var j = 0
      var valueStr = ""

      /// 패턴 텍스트를 반복하면서 text의 i+j번째와 패턴의 j번째를 비교한다.
      while j < pattern.count && text[i+j] == pattern[j] {
          valueStr += "\(pattern[j])"
          j += 1
          /// 텍스트의 카운트가 i+j번보다 작으면 빠져나간다
          if text.count <= i+j { break }
      }
      /// 텍스트와 패턴이 같을때마다 j가 올라가서 j가 패턴의 글자 길이와 같으면 매칭이 됨
      if j == pattern.count {
          print("\(i)번째~\(i+j-1)번째 글자: \(valueStr)")
          cnt += 1
      }
  }
  let endDate = Date()
  let timer = endDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
  print("종료")
  print("총 \(text.count)글자 - 걸린시간: \(timer)초, 찾은 패턴: \(cnt)")
}

let text = getText()
print(text)
bruteForce(Array(text), pattern: Array("good"))
```
```swift
824번째~827번째 글자: good
15519번째~15522번째 글자: good
16814번째~16817번째 글자: good
20841번째~20844번째 글자: good
24922번째~24925번째 글자: good
...
3650846번째~3650849번째 글자: good
3651852번째~3651855번째 글자: good
3657369번째~3657372번째 글자: good
3660938번째~3660941번째 글자: good
3664802번째~3664805번째 글자: good
종료
총 3665494글자 - 걸린시간: 0.587503910064697초, 찾은 패턴: 1014
```
