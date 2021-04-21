# 题目描述
https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/
## 解题思路1 
首先我想到的方法，利用s.substr(a,b)截取字符串的一部分，例如s.sunstr(0,n)截取的是：从字符下标0开始截取n位字符，
那么剩下的字符就是s.substr(n,length-n),length指的是字符串的长度。（这里注意一下字符串的下标问题）
## 代码
```
class Solution {
public:
    string reverseLeftWords(string s, int n) {
        string s1=s.substr(0,n);  //截取前n位字符
        int length = s.length();  //求字符串的长度
        string s2=s.substr(n,length-n);  //截取剩下的字符串
        return s2+s1;  //把s2放在前面，s1放在后面，拼接字符串
    }
};
```
## 解题思路2
看到的另一种挺巧妙的解法，将字符拼接串起来，比如“abcdef”+“abcdef”=“abcdefabcdef”，如果要得到“cdefab”只要提取一下就可以（s.substr(n,len)）,
len是原始字符串的长度，也是拼接起来字符串长度的一半。
## 代码
```
class Solution {
public:
    string reverseLeftWords(string s, int n) {
            s+=s; //将s拼接到s后，得到累加的字符串
            int len=s.length()/2; //提取的字符串的长度大小
            return s.substr(n,len); //提取字符串
    }
};
```
