# Leetcode-
在刷题过程中自己的一些心得体会
解题思路
方法1：哈希表
(1)初始化一个空的哈希表a，用来存储nums中的元素（key）和key对应的value值（即key就是元素值，value就是下标值，nums[key]=value);
(2)用target-nums中的元素，并与a中的key比较，没有的话返回0，并把这个元素放到哈希表a中；
(3)有的话，将此时哈希表中的key值对应的value值（即下标）读出，同时也把i值读出到容器vector中；

代码


class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
       map<int,int> a;//初始化hash表，前一个int表示key（即存储nums中的元素），后一个int表示value（即存储元素对应的下标，也就是地址）
       vector<int> b(2,-1);//初始化一个vector，表示2个初始值为-1的整数容器，使用vector容器存储最终的输出结果
       for(int i=0; i<nums.size(); i++)
       {
           if(a.count(target-nums[i])>0)//在map中a.count(x)表示查找a中是否有x，如果没有则返回0，如果有则返回1，此时表示有（即>0）
           {
               b[0]=a[target-nums[i]];//弄懂a[nums[i]]=i，表示标记元素nums[i]的下标为i，同理反推：target-nums[i]的下标为a[target-nums[i]]；value等于a[key]
               b[1]=i;//i存储在b[1]中
                break;//找到直接break跳出循环，防止执行下面的语句

           }

            a[nums[i]]=i;//找不到就把这个元素和下面存进a中，让nums[i]的位置值为i


       }
       return b;

    }
};

解题思路
方法2：暴力求解

代码


class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
       
       int i,j;//在这里声明的原因是从return中得到i和j的数值，并且for循环内定义的i和j只能在循环内使用；
        for(int i=0; i<nums.size()-1; i++)//-1的原因是不用遍历到最后一个数字，应该到倒数第二个；
        {
            for(int j=i+1; j<nums.size(); j++)
            {
                if(nums[i]+nums[j]==target)
                 return {i, j};//找到后直接结束两个循环，因为答案要求一个答案，没必要继续找返回i和j的值，最终再用一个return输出；
            }
        }
        
        return {i,j};

    }
};
