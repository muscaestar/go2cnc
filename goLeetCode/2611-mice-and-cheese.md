# 2611. 老鼠和奶酪
- 每日一练。中等。贪心算法。用了go的排序包sort，对数组的排序是先转成切片再排。
- 解法还能改进，今天先到这。
- [原题](https://leetcode.cn/problems/mice-and-cheese/)
## Code
```go
import "sort"
func miceAndCheese(reward1 []int, reward2 []int, k int) int {
    sum := 0
    diff := make([]int, len(reward1))
    for i,_ := range reward2 {
        sum += reward2[i]
        diff[i] = reward1[i] - reward2[i]
    }

    sort.Sort(sort.Reverse(sort.IntSlice(diff)))

    for i := 0; i < k; i++ {
        sum += diff[i]
    }
    
    return sum
}
```
