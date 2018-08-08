# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 라빈-카프 알고리즘(Rabin-Karp)

```swift
func getText() -> String{
  do {
      guard let path = Bundle.main.path(forResource: "example", ofType: "txt") else{ return "" }
      guard let url = URL(string: path) else { return "" }
      return try String(contentsOfFile: url.absoluteString)
  } catch { return "" }
}

func ascii(_ char: Character) -> Int {
  let value = String(char).unicodeScalars.compactMap { $0.isASCII ? $0.value : nil }.first
  if let value = value {
      return Int(value)
  }
  return 0
}

func hash(_ str: [Character], size: Int) -> Int {
  var hashValue = 0
  for i in 0..<size {
      hashValue += (ascii(str[i]) * Int(pow(2.0, Double(size - (1 + i)) )) )
  }
  return Int(hashValue)
}

func reHash(_ str: [Character], start: Int, size: Int, hashPrev: Int, coefficient: Int) -> Int {
  if start == 0 {
      return hashPrev
  }
  let prev = ascii(str[start + size - 1])
  let next = (hashPrev - coefficient * ascii(str[start - 1])) * 2
  return prev + next
}

func karpRabin(_ text: [Character], pattern: [Character]) {
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

  let coefficient = Int(pow(2.0, Double(pattern.count) - 1))

  let hashPattern = hash(pattern, size: pattern.count)
  var hashText = hash(text, size: pattern.count)

  for i in 0...text.count-pattern.count {
      hashText = reHash(text, start: i, size: pattern.count, hashPrev: hashText, coefficient: coefficient)
      if hashPattern == hashText {
          var j = 0
          for _ in 0..<pattern.count {
              if text[i+j] != pattern[j] {
                  break
              }
              j += 1
          }
          if j >= pattern.count {
              print("\(cnt) - \(i)번째~\(i + pattern.count - 1)번째")
              cnt += 1
          }
      }
  }

  let endDate = Date()
  let timer = endDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
  print("총 \(text.count)글자에서 \(pattern) 패턴 찾기 - 걸린시간: \(timer)초, 찾은 패턴: \(cnt)")
}

let text = getText()
print(text)

karpRabin(Array(text), pattern: Array("good"))
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
총 3665494글자에서 ["g", "o", "o", "d"] 패턴 찾기 - 걸린시간: 13.2748258113861초, 찾은 패턴: 1014


```
