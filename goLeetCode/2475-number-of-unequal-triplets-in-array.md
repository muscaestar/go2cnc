# 2475. 数组中不等三元组的数目
简单。。。没啥好说的。
可以补充一个，虽说go可以在一个`:=`语句中声明赋值多个变量，但是这两个变量是不能有依赖的。
比如以下语句就无法编译：
```go
a := []int{11, 33}
i, b := 1, a[i] // Unresolved reference 'i' 无法编译
```

## 题解
```go
func unequalTriplets(nums []int) int {
    cnt := 0
    for i := 0; i < len(nums) - 2; i++ {
        ni := nums[i]
        for j := i+1; j < len(nums) - 1; j++ {
            nj := nums[j]
            if ni == nj {
                continue
            }
            for k := j+1; k < len(nums); k++ {
                nk := nums[k]
                if nj == nk || ni == nk {
                    continue
                }                
                cnt++                
            }
        }
    }
    return cnt
}
```
