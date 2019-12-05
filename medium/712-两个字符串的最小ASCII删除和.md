## 信息卡片
* 题目来源：[两个字符串的最小ASCII删除和](https://leetcode-cn.com/problems/minimum-ascii-delete-sum-for-two-strings/)
* 时间：2019-12-05



## 题目描述
给定两个字符串s1, s2，找到使两个字符串相等所需删除字符的ASCII值的最小和。

>**示例 1:**<br>
输入: s1 = "sea", s2 = "eat" <br>
输出: 231 <br>
>**解释:** <br>
在 "sea" 中删除 "s" 并将 "s" 的值(115)加入总和。 <br>
在 "eat" 中删除 "t" 并将 116 加入总和。 <br>
结束时，两个字符串相等，115 + 116 = 231 就是符合条件的最小和。

>**示例 2:** <br>
输入: s1 = "delete", s2 = "leet" <br>
输出: 403 <br>
>**解释:** <br>
在 "delete" 中删除 "dee" 字符串变成 "let"， <br>
将 100[d]+101[e]+101[e] 加入总和。在 "leet" 中删除 "e" 将 101[e] 加入总和。<br>
结束时，两个字符串都等于 "let"，结果即为 100+101+101+101 = 403 。 <br>
如果改为将两个字符串转换为 "lee" 或 "eet"，我们会得到 433 或 417 的结果，比答案更大。

>**注意:** <br>
0 < s1.length, s2.length <= 1000。 <br>
所有字符串中的字符ASCII值在[97, 122]之间。

## 个人解法
```c
int max(int a, int b){
    return a > b ? a : b;
}

int minimumDeleteSum(char * s1, char * s2){
    int len1 = strlen(s1), len2 = strlen(s2);
    int** res = (int**)malloc((len1 + 1) * sizeof(int*));
    for(int i = 0; i < len1 + 1; i++){
        res[i] = (int*)malloc((len2 + 1) * sizeof(int));
    }
    for(int i = 0; i < len1 + 1; i++){
        res[i][0] = 0;
    }
    for(int i = 0; i < len2 + 1; i++){
        res[0][i] = 0;
    }

    for(int i = 0; i < len1; i++){
        for(int j = 0; j < len2; j++){
            if(s1[i] == s2[j]){
                res[i+1][j+1] = res[i][j] + 2 * s1[i];
            }
            else{
                res[i+1][j+1] = max(res[i+1][j], res[i][j+1]);
            }
        }
    }
    int t = 0;
    for(int i = 0; i < len1; i++){
        t += s1[i];
    }
    for(int i = 0; i < len2; i++){
        t += s2[i];
    }
    return t - res[len1][len2];
}

``` 



## 点评
与做最长公共子串其实一模一样的思路，使用动态规划，用dp[i][j]记录s1的前i位和s2的前j位最大公共子串的ASCII和，然后用总和减去它即可。有递推关系：<br>
if s1[i]==s2[j]: dp[i][j] = dp[i-1][j-1] + 2*s1[i]; <br>
else: dp[i][j] = max(dp[i-1][j], dp[i][j-1])
