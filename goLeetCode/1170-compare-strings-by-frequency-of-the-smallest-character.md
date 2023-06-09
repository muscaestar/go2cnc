# 1170. 比较字符串最小字母出现频次
- 每日一题，中等
- 学习了go的rune
- 比较的时候尝试先排序，这样不用遍历中途就可以break
  - 但是实际因为遍历的数组最长也就10，最终遍历反而比排序更节省时间


# 解法
```go
func numSmallerByFrequency(queries []string, words []string) []int {
	ws := make([]int, len(words), len(words))
	for i, v := range words {
		ws[i] = f(v)
	}
	ans := make([]int, len(queries), len(queries))
	cntOfSmaller := func(in int) int {
		cnt := 0
		for _, v := range ws {
			if v > in {
				cnt++
			}
		}
		return cnt
	}

	for i, v := range queries {
		num := f(v)
		ans[i] = cntOfSmaller(num)
	}
	return ans
}

func f(s string) int {
	runes := []rune(s)
	leastCh := runes[0]
	cnt := 0
	for _, v := range runes {
		if v < leastCh {
			leastCh = v
			cnt = 1
		} else if v == leastCh {
			cnt++
		}
	}
	return cnt
}
```
