### What is Dynamic Programming
- 目標不容易透過簡單計算了解
- 但走到第n步的result，可用前面result表達
- 但最初result可以直接get
- 需要利用recursive來完成
使用範圍
- 問題可拆成重覆子問題
- 可將子問題的答案存入重覆使用
- 子問題的解是不應該改變
#### 62. unique path
- 不重覆方法數
- 無法往回走，只能向右或向下
- 走到終點的方法=走到終點left side一格方法+走到終點上面一格方法
- 碰到邊界的話，無法走過方法數為0
- 從起點start,start依然是一個方法
###### hint
- 宣告一個二微陣列
- 分別將dp最left和最top row/col設為一
- 由左到右，由上到下為:
	- dp [i]  [j]= dp [i-1]  [j]  +dp [i]  [j-1]
- loop結束後，最後一格為答案:
	- return dp [-1]  [-1] 
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp=[[0 for i in range(n)]for j in range(m)]
        for i in range(m):
            dp[i][0]=1
        for j in range(n):
            dp[0][j]=1
        for i in range(1,m):
            for j in range(1,n):
                dp[i][j]=dp[i-1][j]+dp[i][j-1]
        return dp[m-1][n-1]
```
### 198. House Robber
- if rob i-1 house, could not steal the i house
- if setting to steal to the number i houses, and max profit rob[ i ]
	- rob [i] =max(num[i]+rob[i-2],rob[i-1])
	- rob[0]=num[0]
	- rob[1]=max(num[0],num[1])
- hint:
	- 初始化rob串列，長度為nums的長度
	- rob[0]=nums[0]
	- rob[1]=max(nums[0],nums[1])
	- continue loop i=2 to i-1:
	- using prior record rob[i]=max(num[i]+rob[i-2],rob[i-1])
	- retrun rob[-1] or rob[l-1]
``` python
class Solution:

    def rob(self, nums: List[int]) -> int:

        l= len(nums)

        if l==0:

            return 0

        if l==1:

            return nums[0]

        rob=[0]*l

        rob[0],rob[1]=nums[0],max(nums[0],nums[1])

        for i in range (2,l):

            rob[i]=max(nums[i]+rob[i-2],rob[i-1])

        return rob[l-1]
```

#### 213. House Robber II
- arrange in a circle
- 意思是首尾相連非排列直線
- 地0 棟跟第 l-1會互相影響，因連結而無法拆成子問題
- 嘗試分開狀況討論
	- 偷第0棟:
		- 第l-1不可偷
		- 結束在l-2
	- 不偷第0棟:
		- 可偷l-1棟
	- compare 偷第0棟 and 不偷第0棟
##### hint
- 初始化 prev,curr 均為nums[0]
- 進行 loop i=22到 l-2:
- 使用 temp and prev 暫記 prev 和curr 後，curr=max(prev,tmp+nums[i])
	- record res=cur
- 不偷第0 棟:
- 初始化 prev,curr為0,num[1]
- 進行loop i=2 到 l-1: 
- 最後比較 curr，prev取max
``` python
class Solution:

    def rob(self, nums: List[int]) -> int:

        l=len(nums)

        if l==0:

            return 0

        if l==1:

            return nums[0]

        #don't rob 0 first ->result=rob[l-1]

        #rob[i]=max(nums[i]+rob[i-2],ron[i-1])

        prev,curr=0,nums[1]

        for i in range(2,l):

            tmp,prev=prev,curr

            curr=max(nums[i]+tmp,prev)

        res=curr

        #rob 0 -> res=rob[l-2]

        prev,curr=nums[0],nums[0]

        for i in range (2,l-1):

            tmp,prev=prev,curr

            curr=max(nums[i]+tmp,prev)

        return max(res,curr)

```
