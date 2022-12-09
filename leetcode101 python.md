## time/space complexity
- consider highest level 
- not to consider conntant
- imply =>big-O
- 若原本有 => tim com Big-O(1)
- Output a new one => Big-O(n)
### hash table intorduction
- pair of(key,value)
- one key pair one value 
- key will not same (could more in one) not limit one pair
- insert ,del,sort,aggrate =>O(1)
 - key  (hash function) buckets
	 - dictionary in python
	 - use {} or dict () initialize
	 - eg. map={k1:vi,k2:v2 }
	 - insert=>map[k3]=v3
	 - get val=> map.get(k3) or map[k3]
	 - del=> del.map[k3]
	 - map. __ contains_(key)
	 - key in map
	 - traverse dict=> for k,v in map item():
***
### how to use it
 1. data is not order
 2. no repeat data or need to stat quantity
 3. ant to use O(1)  to get data
 ***
 ### eg 1.two sum
	 return index 
	 list just one pair could combine sum
#### Bruce Force method
	 O(n^2)
	 每次固定一值
	  too slow
#### Problem slove
- check target-num[i] nas in dict
- if it exist get val indices return
- not exist => (num[i],i) return
``` python
	numMap={}
	for i in range(len(nums)):
		if target-nums[i] in numMap:
			return [i,numMap.get(target-num[i])]
		else:
			numMap[num[i]]=i
	return [-1,-1]		
	
```