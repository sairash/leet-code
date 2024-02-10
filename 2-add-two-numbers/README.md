## Add Two Numbers
**Difficulty:** Medium<br>

[LEETCODE_LINK](https://leetcode.com/problems/add-two-numbers/)

**Question:**

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

```
Example 1:
| Input: l1 = [2,4,3], l2 = [5,6,4]
| Output: [7,0,8]
| Explanation: 342 + 465 = 807.


Example 2:
| Input: l1 = [0], l2 = [0]
| Output: [0]

| Example 3:
| Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
| Output: [8,9,9,9,0,0,0,1]
```

**Solution:** Golang

``` go
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	ret := &ListNode{}
	carry := 0
	
	cur_pointer := ret

	for {
        val1 := 0
	    val2 := 0
		if l1 != nil {
			val1 = l1.Val
			l1 = l1.Next
		}

		if l2 != nil {
			val2 = l2.Val
			l2 = l2.Next
		} 
        
		cur_pointer.Val = (val1 + val2 + carry) % 10
		carry = (val1 + val2 + carry) / 10
		if l1 != nil || l2 != nil || carry != 0 {
			cur_pointer.Next = &ListNode{}
			cur_pointer = cur_pointer.Next
		} else {
			break
		}
	}
	return ret
}
```

**Performance:**
Runtime 2ms (Beats 93.78% users) <br>

![Performance](./performance.png)