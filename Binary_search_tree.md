### def:
 - 除了二元樹外，對每個node:
	 - 左子樹的任一節點比跟節點小
	 - 右子樹任一節點比跟節點大
- 依上面特性，平衡時有助於SEARCH
- 中序順序會是由小排到大的陣列
#### 適用範圍
- 跟排序跟search 有關
- Insert time: o(logn)
#### eg 700.search in a binary search tree
problem sol:
 -    check root:
	 - not exist -> return root
	 - if val == root  ->return root (find ans)
- if val < root.val , search left subnodetree
- else recursive search roght subnodetree
```python
class Solution:

    def searchBST(self, root: TreeNode, val: int) -> TreeNode:

        if not root:

            return root

        if val==root.val:

            return root

        if val <root.val:

            return self.searchBST(root.left,val)

        else:

            return self.searchBST(root.right,val)

```

####  iteration
- let n=root to use check node
- build loop:
	 - if val=n.val -> return n
	 - if val is small -> n to left
	 - if val is bigger -> n to right
- break loop means root is empty or not find any node
- return n

```python
```python
class Solution:
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        n=root
        while n:
            if val==n.val:
                return n
            if val < n.val:
                n=n.left
            else:
                n=n.right
        return n


        
```

```