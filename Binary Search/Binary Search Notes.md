
### 1. Search a 2D matrix

![BS1](../assets/BS1.png)
 - ***DOUBLE BINARY SEARCH*** one to find which row to do BS in and another to actually do it
 - compare the `matrix[row][-1]` for last element in row and `matrix[row][0]` for 1st element in row

![BS1-soln](../assets/BS1-soln.png)

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        rows = len(matrix)
        cols = len(matrix[0])

        top, bot = 0,rows-1
        while top<=bot:
            row = (top+bot)//2
            if target > matrix[row][-1]:
                top = row+1
            elif target < matrix[row][0]:
                bot = row-1
            else:
                break
        
        if not top<=bot: # if number not in any of these rows 
            return False
        
        row = (top+bot)//2
        l,r = 0, cols-1
        while l<=r:
            mid = (l+r)//2
            if target == matrix[row][mid]:
                return True
            elif target > matrix[row][mid]:
                l=mid+1
            else:
                r=mid-1
        return False
```

---

### 2. Koko Eating Bananas

![BS2](../assets/BS2.png)
- condition is `len(piles) <= h` cuz 1 pile 1 hour max KoKo can eat even if pile has less bananas

![BS2-soln](../assets/BS2-soln.png)

```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        l,r  = 1, max(piles)
        res = r
        while l<=r:
            k = (l+r)//2
            hours = 0
            for p in piles:
                hours += math.ceil(p/k)
            
            if hours<=h:
                res = min(res,k)
                r=k-1
            else:
                l=k+1
        return res
```

---

### 3. Find Minimum in Rotated Sorted Array

![BS3](../assets/BS3.png)

