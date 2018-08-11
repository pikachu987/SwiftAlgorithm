# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 보이어-무어 알고리즘(Boyer_Moore)

```swift
extension String.Index{
    func successor(in string:String)->String.Index{
        return string.index(after: self)
    }

    func predecessor(in string:String)->String.Index{
        return string.index(before: self)
    }

    func advance(_ offset:Int, `for` string:String)->String.Index{
        return string.index(self, offsetBy: offset)
    }
}

extension String {
    func boyerMoore(_ pattern: String) -> [String.Index] {
        var indexs = [String.Index]()
        let patternLength = pattern.count
        /// 패턴 스킵 이동 테이블
        var skipTable = [Character: Int]()
        for (i, c) in pattern.enumerated() {
            skipTable[c] = patternLength - i - 1
        }
        /// 패턴 마지막 문자
        let p = pattern.endIndex.predecessor(in: pattern)
        let lastChar = pattern[p]
        /// 패턴 인덱스
        var i = self.startIndex.advance(patternLength - 1, for: self)
        /// 문자를 찾을때까지
        func backwards() -> String.Index? {
            var q = p
            var j = i
            while q > pattern.startIndex {
                j = j.predecessor(in: self)
                q = q.predecessor(in: pattern)
                if self[j] != pattern[q] { return nil }
            }
            return j
        }
        while i < self.endIndex {
            let c = self[i]
            if c == lastChar {
                if let k = backwards() { indexs.append(k) }
                i = i.successor(in: self)
            } else {
                /// 문자가 같지 않으면 건너뛴다
                i = i.advance(skipTable[c] ?? patternLength, for: self)
            }
        }

        return indexs
    }
}
func getText() -> String{
  do {
      guard let path = Bundle.main.path(forResource: "example", ofType: "txt") else{ return "" }
      guard let url = URL(string: path) else { return "" }
      return try String(contentsOfFile: url.absoluteString)
  } catch { return "" }
}

let startDate = Date()

let text = getText()
print(text)
let pattern = "good"
let indexs = text.boyerMoore(pattern)
for (i, index) in indexs.enumerated() {
  print("\(i) - \(index.encodedOffset)번째~\(index.encodedOffset+pattern.count-1)번째")
}
let endDate = Date()
let timer = endDate.timeIntervalSince1970 - startDate.timeIntervalSince1970
print("총 \(text.count)글자에서 \(pattern) 패턴 찾기 - 걸린시간: \(timer)초, 찾은 패턴: \(indexs.count)")
```
```swift
0 - 824번째~827번째
1 - 15519번째~15522번째
2 - 16814번째~16817번째
3 - 20841번째~20844번째
4 - 24922번째~24925번째
...
1009 - 3650848번째~3650851번째
1010 - 3651854번째~3651857번째
1011 - 3657371번째~3657374번째
1012 - 3660940번째~3660943번째
1013 - 3664804번째~3664807번째
총 3665494글자에서 good 패턴 찾기 - 걸린시간: 0.98825216293335초, 찾은 패턴: 1014
```
