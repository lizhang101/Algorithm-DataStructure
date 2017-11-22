# [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)
## Problem Description
Find the kth largest element in an unsorted array. __**Note**__ that it is the kth largest element in the sorted order, not the kth distinct element.

For example,
Given `[3,2,1,5,6,4]` and k = 2, return 5.

Note: 
You may assume k is always valid, 1 ≤ k ≤ array's length.

Credits:
Special thanks to @mithmatt for adding this problem and creating all test cases.

## [Solutions](https://leetcode.com/problems/kth-largest-element-in-an-array/discuss/)
1. sort and return kth largest element, O(N lg N) time + O(1) memory complexity
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length - k];
    }
}
```

2. use priority queue, O(N lg K) running time + O(K) memory
```
public int findKthLargest(int[] nums, int k) {
    final PriorityQueue<Integer> pq = new PriorityQueue<>();
    for(int val : nums) {
        pq.offer(val);

        if(pq.size() > k) {
            pq.poll();
        }
    }
    return pq.peek();
}
```

## Data structure / Algorithm / Java knowledge Used
- Arrays.sort()
- [priority Queue](http://www.geeksforgeeks.org/priority-queue-class-in-java-2/)

  The head of priority queue is the least element with respect to the specified ordering.

## Similar Problems
- [414. Third Maximum Number](https://leetcode.com/problems/third-maximum-number/description/)

