# 1171. 从链表中删去总和值为零的连续节点
- 一开始想偏了，试图用滑动窗口，滑动窗口需要有序值，不满足这个题
- 必须记录所有的累加，因此想到用一个数组记录每个node的到当前node的累加，只要出现0就可以切掉这部分，正解
    - 为了记录数组和链表node的对应关系，做了一个struct
- 官方题解有个新思路，比我的解法更跳跃一些，我觉得我的解法实用性也不赖，思路更容易理解些

## 解法
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

type AdderNode struct {
	Sum int
	Ori *ListNode
}

func removeZeroSumSublists(head *ListNode) *ListNode {
	rArr := make([]*AdderNode, 0, 1000)
	for ; head != nil; head = head.Next {
		rArr = append(rArr, &AdderNode{Ori: head})
		zero, idx := allAddTillZero(rArr, head.Val)
		if zero {
			rArr = rArr[:idx]
			if len(rArr) > 0 {
				ori := rArr[len(rArr)-1].Ori
				ori.Next = head.Next
			}
		}
	}
	if len(rArr) > 0 {
		return rArr[0].Ori
	} else {
		return nil
	}
}

func allAddTillZero(arr []*AdderNode, adder int) (bool, int) {
	for i, v := range arr {
		(*v).Sum += adder
		if (*v).Sum == 0 {
			return true, i
		}
	}
	return false, 0
}
```
