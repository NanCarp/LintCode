----
## 题目
![寻找峰值.png](http://upload-images.jianshu.io/upload_images/5343805-d04f56e8978ebdea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

----
## 分析
考虑使用二分查找，如果中间元素大于其相邻的后续元素，则中间元素左侧（包括中间元素）必然包含一个局部最大值，如果中间元素小于其相邻的后续元素，则中间元素右侧必然包含一个局部最大值。直到最后左边沿和右边沿相遇，我们找到所求峰值。  

---- 
## 代码  

```
public class Solution {
    /*
     * @param A: 整型数组
     * @return: 返回任意一个峰值的位置
     */
    public int findPeak(int[] A) {
        int start = 0; // 左侧起始元素
        int end = A.length -1; // 右侧终止元素
        
        while (start < end) { // 循环比较 start 与 end，相等时退出
            int mid = start + ( end - start) / 2;  // 中间元素
            
            if (A[mid] < A[mid + 1]) {
                // 中间元素小于其相邻的后续元素，
                // 则中间元素右侧（不包含 mid）必然包含一个局部最大值，
                // 起始位置设为 mid 右侧相邻元素
                start = mid + 1; 
            } else {
                // 中间元素大于于其相邻的后续元素，
                // 则中间元素左侧（包含 mid）必然包含一个局部最大值，
                // 终止位置设为 mid 
                end = mid;
            }
        }
        
        return start; // start 与 end 相遇，返回结果
    }
}
```

----
## 参考  

[[C++]LeetCode: 118 Find Peak Element (二分查找 寻找数组局部峰值)](http://blog.csdn.net/cinderella_niu/article/details/43056759)