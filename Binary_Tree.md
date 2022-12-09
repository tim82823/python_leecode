- unit => node
- 根/左/右 節點
- 每個節點均有值
- 每個node有其左右節點
- NIL(None/ null)
- 左子樹/右子樹
- 樹拆分分支僅2個的時候(非字典樹)
- 二元搜尋樹前置
- 不在意大小關係(非二元搜尋樹)
### 100. Same Tree
	用遞迴
- 透過不斷 calling same function, 將Q化簡得answer
- 要確定的狀況的條件前後 connector
- exp: n+(n+1)+(n+2)+....?
def SumN(n):
	if n== 1:
		return 1
	else:
		 return n + SumN(n-1)
比較2棵二元樹是否相等,
		同等比較:
- root 是否同時存在 or 同時不存在，同時存在，值必相等
- 同時存在且值相等，子樹比較(left vs right)
- 左右子樹相等，則二元樹相等
### problem sol
- compare root:
	- 均不存在 -> true
	- 存在其一 ->false
	- 均存在 ->值 <> return false
- 呼叫進行遞迴:
	- 兩邊左右子樹相同 return true
#### sol :
``` python
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if  not p and not q:
            return True
        if not p or not q:
            return False
        return p.val==q.val and self.isSameTree(p.left,q.left) and self.isSameTree(p.right,q.right)
```
### 110. Balanced Binary Tree
- 左右子樹高度差1，且左右都是平衡二元樹
- 先算左右子樹深度
- 取一個子樹，等同於左右子樹深度漸大值
檢查
 - 算左/右子樹深度，檢查節點是否平衡
 - 若不平衡可記錄上一個值 
 - 或 return -1
### pro sol:
- 利用遞迴檢查深度
- 若 root 為 none -> return 0
- 計算右子樹深度，並取差值
- 若單邊深為-1  return -1
- 若相差 >+1 則 return-1
- 其他 return 1+max(1,r)
- 最後確認最終回傳值
	- -1 -> return false
	- else -> true
```python
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        
        def check(root:TreeNode)->int:
            if root==None:
                return 0
            l=check(root.left)
            r=check(root.right)
            if l==-1 or r==-1 or abs(l-r)>1:
                return -1
            return 1+max(l,r)
        return check(root)!=-1
```

### 617. Merge Two Binary Trees
		合併兩棵二元樹
		節點其一存在，我們可以採用節點
		節點同時存在，將其合併(加總)到其中一個
		節不存在，表示下無節點
### hint
- check 2 node t1,t2:
	- 均不存在 -> return node
	- 存在其一 -> return 該節點
	- 均存在 ->將值合併於t1(及t1跟t2的sum)
- call遞迴:
	- 左節點equal於呼叫自身遞迴帶入t1.left,t2.left之結果
	- 右節點同上
	- 最終return root
```python
class Solution:
    def mergeTrees(self, root1: TreeNode, root2: TreeNode) -> TreeNode:
        if not root1 and not root2 :
            return None
        if not root1 or not root2:
            return root1 or root2
        root1.val+=root2.val
        root1.left=self.mergeTrees(root1.left,root2.left)
        root1.right=self.mergeTrees(root1.right,root2.right)
        return root1
```