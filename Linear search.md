-  一個一個對比(to first and last)
- sequential search
## Binary search
- 在一串排序好的資料搜尋
- 每次切兩半取中位數
- 保留還在範圍的那一半
- 反覆縮小上下界直到找到目標
- 若找不到目標，下界極為插入點
- time => O(logN)
---
#### 適用範圍
 - data are order
 - before order Big O > O(NlogN)
### Linear 
 target > nums[i] => go down
 target <nums[i]  => return
 target == nums[i] => return
 go to the end  => return
 => time BigO(N)
### Binary
 if nums[mi] >target => goal is between low and mid
 if nums[mi] < target => goal is between mid and up
 反覆調整直到相等或兩者交錯
 every time lo,up update to change mid
	lo,hi=0,len(nums)-1
	while lo<=hi:
		mi=(lo+hi)//2
	if nums[i] == target:
		return m
	elif nums[mi] >target:
		hi=mi-1
	else:
		lo=mi+1
return lo
### eg.278 first bad version
-  find the bad version
- using Binary search
- if mid is bad , not return mid
	- setting high to mid
- elif 1-mid is ok
	- let lo setting m+1 to search
#### Problem solving

- LET lo=1 ,hi=n
- get mi=(hi+lo)//2
- if is bad version
	- check mi is 1 or mi-1 is not bad version, return mi
	- hi set to mi-1
- if is not bad version
	- let lo set to mi+1
- if version is ok, return none
``` python
	class Solution:
    def firstBadVersion(self, n: int) -> int:
        lo,hi=1,n
        while lo<=hi:
            mi=(lo+hi) // 2
            if isBadVersion(mi):
                if mi==1 or not isBadVersion(mi-1):
                    return mi
                hi=mi-1
            else:
                lo=mi+1
        return None
        
	
```

