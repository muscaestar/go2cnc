# 1375. 二进制字符串前缀一致的次数
- 没仔细看，一开始用二进制。。。太傻了
- 时间紧迫，先暴力了 超5%。。。。

# 题解
```go
func numTimesAllBlue(flips []int) int {
	cnt := 0
	n := len(flips)
	var binary = make([]bool, n)
	for i, v := range flips {
		flip(binary, v)
		res := isPrefConst(i+1, binary)
		if res {
			cnt++
		}
	}
	return cnt
}

func flip(binary []bool, fcode int) {
	binary[fcode-1] = !binary[fcode-1]
}

func isPrefConst(step int, binary []bool) bool {
	ans := true
	for i := 0; i < step; i++ {
		ans = ans && binary[i]
        if !ans {
            break
        }
	}
	return ans
}
```
