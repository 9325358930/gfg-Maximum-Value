# gfg-Maximum-Value
Problem of the day

Example 1:

Input:
        1
       / \
      2   3 
Output:
1 3
Explanation:
At 0 level, values of nodes are {1}
                 Maximum value is 1
At 1 level, values of nodes are {2,3}
                Maximum value is 3

/* Tree node structure  used in the program

struct Node
{
    int data;
    struct Node* left;
    struct Node* right;
}; */

class Solution {
  public:
    vector<int> maximumValue(Node* node) {
        //code here
        queue <Node*> que;
        vector<int> ans;
        que.push(node);
        while(que.size() > 0){
            int s = que.size();
            int m = 0;
            while(s--){
                Node* p = que.front();
                m = max(m, p->data);
                que.pop();
                if(p->left != NULL) que.push(p->left);
                if(p->right != NULL) que.push(p->right);
            }
            ans.push_back(m);
        }
        return ans;
    }
};
