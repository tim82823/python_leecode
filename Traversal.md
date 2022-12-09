- 二元樹走訪:
	- pre-order:root ->left -> right
	- in-order: left -> root ->right
	- post-order: left -> right  ->  root
	- level -order: level to level
	- the first three DFS，Final one BFS 
#### 94. bInary inorder tree
##### HINT
-  If root is none, return
-  若ROOT的左節點存在，ROOT.LEFT 帶入遞迴
- 將ROOT的值附加上RES結果
- 若ROOT的右節點存在，ROOT.RIGHT 帶入遞迴
- 全數遞迴完畢，帶入RES即可
``` python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        self.res=[]
        def dfs(root):
            if not root:
                return
            if root.left:
                dfs(root.left)
            self.res.append(root.val)
            if root.right:
                dfs(root.right)
        dfs(root)
        return self.res
```
102. Binary tree level order traversal