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
# 解题思路2
既然数组元素的值不超过数组的下标,那就让数组下标对应的值和下标相等。   
### 主要分以下三种情况
1）若相等，则直接判断下一个
2）若不等，则把当前下标i对应的nums[i]值和下标为nums[i]的nums[nums[i]]值交换，
先判断nums[i]和nums[nums[i]]是否相等，若相等，则返回nums[i]，结束，若不等，则交换。   
# 代码部分
```
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
       int i=0;
        while(i<nums.size()){
            if(nums[i]==i) {
                i++;
                continue;
            }
            if(nums[i]!=nums[nums[i]]){
                swap(nums[i],nums[nums[i]]);//swap内部使用一个中间值交换两个数
            }
            else return nums[i];
        }
    return -1;
    }
};
```
# 复杂度分析
**时间复杂度：** 遍历数组占用O(N)。  
**空间复杂度：** 占用O(1)大小的空间。
