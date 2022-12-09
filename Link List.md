- unit => node
- initial => head
- every node has a data
- every node recording to next connect node
- single trace: data/next
#### common operation
- new => x=ListNode(val)
- insert => (x,insrt in a and b)
		x.next=b
		a.next=x
- remove (a ->x -> b x move out)
		a.next=b
#### traverse
	 ite=head
	 while ite:
		 print(ite.val)
		 ite=ite.next
### 適用範圍
-  較不在意單點存取
- (else using list/array)
- need time to create a new node is decreasing
- 操作太多在靠近頭/結尾
- (因為 search O(N))
### eg. 83. Remove Duplicates from Sorted List
- 先建立遍歷 node ite , 位置head相同
- 當 ite 還沒走到NIL時:
	- 先找 next node tmp, 往下走到值不相等
	-  將ite 的 next 接到 tmp
	- let ite 走到 tmp 
	- 反覆循環走完 link list , 回傳原先head
### sol:

```python
	class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        ite=head
        while ite:
            tmp=ite.next
            while tmp and tmp.val==ite.val:
                tmp=tmp.next
            ite.next=tmp
            ite=ite.next
        return head
		```
### 21. Merge Two Sorted Lists
 - merge two list
 - 若上升排序，較小值即可合併 new list
 - 值相等取其中一個即可
 - same with merge sort
### pro sol
 - 先設dummy node
 - 在設 prev node 做遍歷
 - 比較節點，將perv接next
 - L1,L2 需要往下走
 - 反覆到 2 Empty
 - prev.next
 - clummy next
#### sol
``` python
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy=ListNode()
        tail=dummy
        while l1 and l2:
            if l1.val < l2.val:
                tail.next=l1
                l1=l1.next
            else:
                tail.next=l2
                l2=l2.next
            tail=tail.next
        if l1:
            tail.next=l1
        if l2:
            tail.next=l2
        return dummy.next

```
