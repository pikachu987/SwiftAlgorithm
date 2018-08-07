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
      }
  }
  let endDate = Date()
  let timer = endDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
  print("종료")
  print("총 \(text.count)글자 - 걸린시간: \(timer)초")
}

let text = self.getText()
print(text)
self.bruteForce(Array(text), pattern: Array("Goodight"))


```
```swift
659039번째~659046번째 글자: Goodight
660910번째~660917번째 글자: Goodight
756124번째~756131번째 글자: Goodight
1179039번째~1179046번째 글자: Goodight
2207343번째~2207350번째 글자: Goodight
2853726번째~2853733번째 글자: Goodight
2882829번째~2882836번째 글자: Goodight
3243709번째~3243716번째 글자: Goodight
3282353번째~3282360번째 글자: Goodight
3350139번째~3350146번째 글자: Goodight
3350192번째~3350199번째 글자: Goodight
3373008번째~3373015번째 글자: Goodight
3607344번째~3607351번째 글자: Goodight
3609590번째~3609597번째 글자: Goodight
3643929번째~3643936번째 글자: Goodight
3659086번째~3659093번째 글자: Goodight
종료
총 3665494글자 - 걸린시간: 0.269752025604248초
```
