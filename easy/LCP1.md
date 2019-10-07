## 信息卡片
* 题目来源：[猜数字](https://leetcode-cn.com/problems/guess-numbers/)
* 时间：2019-10-6 



## 题目描述
> 小A 和 小B 在玩猜数字。小B 每次从 1, 2, 3 中随机选择一个，小A 每次也从 1, 2, 3中选择一个猜。他们一共进行三次这个游戏，请返回 小A 猜对了几次？ 



## 个人解法
```
int game(int* guess, int guessSize, int* answer, int answerSize){
    int right = 0;
    for(int i = 0; i < guessSize; i ++) {
        if(guess[i] == answer[i])
            right ++;
    }
    return right;
}
``` 



## 点评
一道非常简单的题，遍历整个数组一遍即可 
