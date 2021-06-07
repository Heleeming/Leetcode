# 题目描述
https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/
# 解题思路1
1）既然找到任何一个重复的元素，那就直接使用**set（集合）**,因为set中存储的是**不重复的元素**。   
2）所以最基本的思想就是不一样的元素存储进set，一样的元素直接返回。  
3）set存储用法：**名称.insert(元素)**，set查找元素用法：**名称.count(元素)**（查找到重复元素返回1，否则返回0）。  
# 代码部分
```
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        set<int> rep;
        for(int num=0; num<=nums.size()-1; num++) {
            if(rep.count(nums[num])) return nums[num];
            rep.insert(nums[num]);
        }
        return -1;
    }
};
```
# 复杂度分析
**时间复杂度：** 遍历数组占用O(N)，HashSet添加与查找元素皆为*O*(1)。
**空间复杂度：** HashSet占用O(N)大小的空间。
