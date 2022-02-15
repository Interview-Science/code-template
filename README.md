# code-template
Code template for coding interview

# Table of contents
- Binary search
    - lower_bound
        - pseudocode
        - Python3
        - Java
        - C++
    - upper_bound
        - pseudocode
        - Python3
        - Java
        - C++
- Sliding window
- Monotonic stack
- Prefix tree
- BFS
- DFS
- Rolling hash
- Topological sort
- Union Find

## Binary Search

### Template

Return the index of first valid element in nums

    BINARY_SEARCH(nums, target)
        // loop invariant: first valid element ∈ [left, right)
        left, right = 0, nums.length
        while left < right
            mid = left + (right - left) // 2
            if VALID(nums[mid], target)
                right = mid
            else
                left = mid + 1
        return left
        
### API: Lower Bound
Return the index of first element greater or equal to target

#### pseudocode

    // nums = [0, 2, 2, 2, 3, 4, 5], target = 2 return 1
    LOWER_BOUND(nums, target)
        left, right = 0, nums.length
        while left < right
            mid = left + (right - left) // 2
            if VALID(nums[mid], target)
                right = mid
            else
                left = mid + 1
        return left

    VALID(num, target)
        if num >= target
            return True
        return False


#### Python3
        
	class Solution:
        def lower_bound(self, nums: List[int], target: int) -> int:
            def valid(num, target):
                if num >= target:
                    return True
                return False

            left, right = 0, len(nums)
            while left < right:
                mid = left + (right - left) // 2
                if valid(nums[mid], target):
                    right = mid
                else:
                    left = mid + 1
            return left
    
#### Java

    class Solution {
        private boolean valid(int num, int target) {
            if (num >= target) {
                return true;
            }
            return false;
        }
        public int lowerBound(int[] nums, int target) {
            int left = 0, right = nums.length;
            while (left < right) {
                int mid = ((right - left) >> 1) + left;
                if (valid(nums[mid], target)) {
                    right = mid;
                } else {
                    left = mid + 1;
                }
            }
            return left;
        }
    }
    
#### C++

    class Solution {
    private:
        bool valid(int num, int target) {
            if (num >= target) {
                return true;
            }
            return false;
        }
    public:
        int searchInsert(vector<int>& nums, int target) {
            int left = 0, right = nums.size();
            while (left < right) {
                int mid = ((right - left) >> 1) + left;
                if (valid(nums[mid], target)) {
                    right = mid;
                } else {
                    left = mid + 1;
                }
            }
            return left;
        }
    };
      
### API: Upper Bound  
Return the index of first element greater to target

#### pseudocode

    // nums = [0, 2, 2, 2, 3, 4, 5], target = 2 return 4
    UPPER_BOUND(nums, target)
        // loop invariant: first valid element ∈ [left, right)
        left, right = 0, nums.length
        while left < right
            mid = left + (right - left) // 2
            if VALID(nums[mid], target)
                right = mid
            else
                left = mid + 1
        return left

    VALID(num, target)
		// the only different between LOWER_BOUND and UPPER_BOUND
		if num > target
			return True
		return False

#### Python3
        
	class Solution:
        def lower_bound(self, nums: List[int], target: int) -> int:
            def valid(num, target):
                if num > target:
                    return True
                return False

            left, right = 0, len(nums)
            while left < right:
                mid = left + (right - left) // 2
                if valid(nums[mid], target):
                    right = mid
                else:
                    left = mid + 1
            return left
    
#### Java

    class Solution {
        private boolean valid(int num, int target) {
            if (num > target) {
                return true;
            }
            return false;
        }
        public int lowerBound(int[] nums, int target) {
            int left = 0, right = nums.length;
            while (left < right) {
                int mid = ((right - left) >> 1) + left;
                if (valid(nums[mid], target)) {
                    right = mid;
                } else {
                    left = mid + 1;
                }
            }
            return left;
        }
    }
    
#### C++

    class Solution {
    private:
        bool valid(int num, int target) {
            if (num > target) {
                return true;
            }
            return false;
        }
    public:
        int searchInsert(vector<int>& nums, int target) {
            int left = 0, right = nums.size();
            while (left < right) {
                int mid = ((right - left) >> 1) + left;
                if (valid(nums[mid], target)) {
                    right = mid;
                } else {
                    left = mid + 1;
                }
            }
            return left;
        }
    };
