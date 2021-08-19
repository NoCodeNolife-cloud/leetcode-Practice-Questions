输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

 

示例 1：

输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
示例 2：

输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]


限制：

0 <= matrix.length <= 100
0 <= matrix[i].length <= 100

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int state=1;
        vector<int>res;
        if(matrix.size()==0){
            return res;
        }
        int posx=0,posy=0;
        vector<vector<bool>>visit(matrix.size(),vector<bool>(matrix[0].size(),false));
        for(int i=0;i<matrix.size()*matrix[0].size();){
            if(state==1){
                while(posy<matrix[0].size() && visit[posx][posy]==false){
                    visit[posx][posy]=true;
                    res.push_back(matrix[posx][posy]);
                    posy++;
                    i++;
                }
                posy--;
                posx++;
                state=2;
            }else if(state==2){
                while(posx<matrix.size() && visit[posx][posy]==false){
                    visit[posx][posy]=true;
                    res.push_back(matrix[posx][posy]);
                    posx++;
                    i++;
                }
                posx--;
                posy--;
                state=3;
            }else if(state==3){
                while(posy>=0 && visit[posx][posy]==false){
                    visit[posx][posy]=true;
                    res.push_back(matrix[posx][posy]);
                    posy--;
                    i++;
                }
                posy++;
                posx--;
                state=4;
            }else if(state==4){
                while(posx>=0 && visit[posx][posy]==false){
                    visit[posx][posy]=true;
                    res.push_back(matrix[posx][posy]);
                    posx--;
                    i++;
                }
                posx++;
                posy++;
                state=1;
            }
        }
        return res;
    }
};
```

