# 题目描述
https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/
# 思路1 深度优先搜索DFS（当递归层数不大时用）
（1）在递归过程中，把递归到的节点当作根节点来看，此根节点的深度=左右节点深度的最大值+1（+1是把根节点本身加上）；   
（2）当不是根节点时（即递归到了不是叶节点的位置），返回0；
# 代码 
```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(!root) return 0;
        return max(maxDepth(root->left),maxDepth(root->right))+1;
    }
};
```
# 题目描述
https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/
# 思路2 广度优先搜索BFS
（1）首先判断是否有root节点，没有的话直接返回深度为0；
（2）若有root节点，则直接把root节点入队到队列q。
（3）当q不为空（q当然不为空，root在里面，有一个元素的），q的大小为1，弹出root；
（4）这时查看q的左右子节点，有的话入队；
（5）这是for循环结束，深度ans+1，第一层遍历结束；
（6）q不为空（若有左右子节点），这是q的长度变成了2；继续循环
# 代码 
```
/**
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==NULL) return 0;
        int ans=0;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty()){
            int now = q.size();
            for(int i=0; i<now; i++){
                TreeNode* node=q.front(); q.pop();
                if(node->left) q.push(node->left);
                if(node->right) q.push(node->right);
            }
            ans++;
        }
        return ans;
    }
};
```
