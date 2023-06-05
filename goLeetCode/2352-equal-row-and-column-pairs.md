# 2352. 相等行列对
- 每日一练。中等。第一次用go解题，go创建动态数组略微麻烦。
- 解法超40%，还能改进，今天先到这。
- [原题](https://leetcode.cn/problems/equal-row-and-column-pairs/)
## Code
```go
func equalPairs(grid [][]int) int {
    var cnt int
    n := len(grid)
    colCache := genColCache(grid)
    
    for i := 0; i < n; i++ {
        for j := 0; j < n; j++ {
            if equalArr(grid[i], colCache[j]) {
                cnt++
            }
        }
    }
    return cnt
}

func equalArr(x []int, y []int) bool {
    if len(x) != len(y) {
        return false
    }
    eq := true
    for i := 0; i < len(x); i++ {
        eq = eq && (x[i] == y[i])
    }
    return eq
}

func genColCache(grid [][]int) [][]int {
	n := len(grid)
	rst := make([][]int, n)
	for i := range rst {
		rst[i] = make([]int, n)
		for j := range rst[i] {
			rst[i][j] = grid[j][i]
		}
	}
	return rst
}
```
