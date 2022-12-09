### 遞迴解
- 重複recall 自己 (同一個function)
- 透過recall自己，將參數化簡，得到答案
### 迭代解
- 透過自己迴圈recall 自己
- 最後化解參數,得到解答
- care !! =>在開始有沒有可化簡的式子
	#### eg. 從n加到1
		sum= n+ sum(n-1)
			=n+n-1+sum(n-2)
- 遞迴: recall myself(容易思考)
- 迭代: for loop(不易推導)
- 迭代速度較快 (不用 call stack)
### eg. 101 symmetric tree
一個樹是否對稱，等考慮:
- root 是否存在，不存在視為True
- 左子樹右子樹是否對稱:
	- 兩者root同時存在or同時不存在,同時存在,值必相等
	- 同時存在且值相等的話，其左右子樹各自比較
	- 左子樹的左子樹對稱右子樹的右子樹，且左子樹的右子樹對稱右子樹的左子樹，則二元樹對稱
	- 比較root:
		- 均不存在 -> return true
		- 存在其一  -> return false
		- 均存在 -> 若值不相等 return false
	- 呼叫進行遞迴:
		- 兩者的左子要對稱對方的右子樹，右子樹也要對稱對方的左子樹才 return Ture
```python
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True
        return self.isSym(root.left,root.right)
    def isSym(self, l:TreeNode,r:TreeNode) -> bool:
        if not r and not l : 
            return True
        if not r or not l:
            return False
        if l.val!=r.val:
            return False
        return self.isSym(l.left,r.right)and self.isSym(l.right,r.left)
```
### 迭代法
- root 不存在 回傳true
- 宣告一個 queue
	- 將左右節點依序放入queue:
	- 取出兩節 l,r 檢查是否相等，不相等 return false
	- 依序 l.eft,r.right,l.right,r.left 放入queue
	- 當整個迴圈END時未回傳false，則回傳true
   ```python
   from collections import deque
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True
        return self.isSym(root.left,root.right)
    def isSym(self, l:TreeNode,r:TreeNode) -> bool:
        if not r and not l : 
            return True
        if not r or not l:
            return False
        if l.val!=r.val:
            return False
        return self.isSym(l.left,r.right)and self.isSym(l.right,r.left)
       
            
```

### eg.617. Merge Two Binary Trees

 
	

