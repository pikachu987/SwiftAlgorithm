# [SwiftAlgorithm](https://github.com/pikachu987/SwiftAlgorithm "SwiftAlgorithm")

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Read the Docs](https://img.shields.io/readthedocs/pip.svg)](https://github.com/pikachu987/SwiftAlgorithm)
[![GitHub stars](https://img.shields.io/github/stars/badges/shields.svg?style=social&label=Stars)](https://github.com/pikachu987/SwiftAlgorithm/stargazers)

### 미로(Maze)

```swift
struct Point {
  var x = 0
  var y = 0
}

enum Direction {
  case north, south, east, west
  static var array: [Direction] {
      return [.north, .south, .east, .west]
  }
}

var maze: [[String]] = [
  ["#", "G", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#"],
  ["#", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", "#"],
  ["#", "#", "#", "#", " ", "#", "#", "#", "#", "#", "#", "#", "#", "#", " ", "#"],
  ["#", " ", " ", " ", " ", "#", "#", "#", " ", " ", " ", " ", " ", " ", " ", "#"],
  ["#", " ", "#", "#", " ", "#", "#", "#", " ", "#", "#", " ", "#", "#", "#", "#"],
  ["#", " ", "#", "#", " ", "#", "#", "#", " ", " ", "#", " ", "#", "#", "#", "#"],
  ["#", " ", "#", "#", "#", "#", "#", "#", "#", "#", "#", " ", " ", " ", " ", "#"],
  ["#", " ", " ", " ", " ", " ", " ", " ", " ", "#", "#", "#", "#", "#", " ", "#"],
  ["#", " ", "#", "#", "#", "#", "#", " ", "#", "#", "#", "#", "#", "#", " ", "#"],
  ["#", " ", "#", " ", " ", " ", "#", " ", "#", " ", "S", " ", " ", "#", " ", "#"],
  ["#", "#", "#", " ", "#", " ", "#", "#", "#", " ", "#", "#", " ", "#", " ", "#"],
  ["#", " ", "#", " ", "#", " ", " ", " ", " ", " ", " ", " ", " ", "#", " ", "#"],
  ["#", " ", "#", " ", "#", "#", "#", "#", "#", "#", "#", "#", " ", "#", " ", "#"],
  ["#", " ", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", " ", "#", " ", "#"],
  ["#", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", " ", "#"],
  ["#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#", "#"],
]

/// 출력
func mazePrint() {
  for element in maze {
      var text = ""
      for value in element {
          text = "\(text)\(value)"
      }
      print(text)
  }
}

@discardableResult
func moveTo(_ maze: inout [[String]], point: inout Point, direction: Direction) -> Bool {
  if maze[point.y][point.x] == "G" { /// G면 골
      return true
  }
  /// 현재 지나왔다는걸 표시
  maze[point.y][point.x] = "+"
  for i in Direction.array {
      var next = Point()
      if getNextStep(&maze, point: &point, direction: i, next: &next) { /// 지나온길이나 경계를 안넘었을때
          if moveTo(&maze, point: &next, direction: i) { /// 다시 사방으로 moveTo
              /// 골이면 리턴
              return true
          }
      }
  }
  /// 모든 방향이 실패했으니 이방향이 아님. 다시 움직일수 있는 길로 표시하고 리턴
  maze[point.y][point.x] = " "
  return false
}

func getNextStep(_ maze: inout [[String]], point: inout Point, direction: Direction, next: inout Point) -> Bool {
  switch direction {
      /// 경계를 넘으면 false
  case .north:
      next.x = point.x
      next.y = point.y - 1
      if next.y == -1 { return false }
  case .south:
      next.x = point.x
      next.y = point.y + 1
      if next.y == maze.count { return false }
  case .west:
      next.x = point.x - 1
      next.y = point.y
      if next.x == -1 { return false }
  case .east:
      next.x = point.x + 1
      next.y = point.y
      if next.y == maze[0].count { return false }
  }
  /// 지나온길이나 벽이면 false
  if maze[next.y][next.x] == "#" { return false }
  if maze[next.y][next.x] == "+" { return false }
  return true
}

func solve(_ maze: inout [[String]]) {
  var point = Point()

  /// 시작점 찾음
  for i in 0..<maze.count {
      for j in 0..<maze[i].count {
          if maze[i][j] == "S" {
              point.x = j
              point.y = i
              break
          }
      }
  }
  let tempPoint = point

  /// 북, 남, 동, 서 순으로 moveTo를 시도
  for i in Direction.array {
      var next = Point()
      if getNextStep(&maze, point: &point, direction: i, next: &next) { /// 지나온길이나 경계를 안넘었을때
          if moveTo(&maze, point: &next, direction: i) { /// 다시 사방으로 moveTo

          }
      }
  }
  maze[tempPoint.y][tempPoint.x] = "S"
}

mazePrint()
print()
solve(&maze)
mazePrint()
```
```swift
#G##############
#              #
#### ######### #
#    ###       #
# ## ### ## ####
# ## ###  # ####
# #########    #
#        ##### #
# ##### ###### #
# #   # # S  # #
### # ### ## # #
# # #        # #
# # ######## # #
# ########## # #
#              #
################

#G##############
#++++++++++++++#
#### #########+#
#    ###   ++++#
# ## ### ##+####
# ## ###  #+####
# #########++++#
#        #####+#
# ##### ######+#
# #   # # S++#+#
### # ### ##+#+#
# # #       +#+#
# # ########+#+#
# ##########+#+#
#           +++#
################
```
