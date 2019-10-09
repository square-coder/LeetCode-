## 信息卡片
* 题目来源：[TinyURL](https://leetcode-cn.com/problems/encode-and-decode-tinyurl/)
* 时间：2019-10-9

## 题目描述
>TinyURL是一种URL简化服务， 比如：当你输入一个URL https://leetcode.com/problems/design-tinyurl
时，它将返回一个简化的URL，http://tinyurl.com/4e9iAk. <br>
>要求：设计一个 TinyURL 的加密 encode 和解密 decode 的方法。你的加密和解密算法如何设计和运作是没有限制的，你只需要保证一个URL可以被加密成一个TinyURL，并且这个TinyURL可以用解密方法恢复成原本的URL。


## 个人解法
```c
/** Encodes a URL to a shortened URL. */
char* encode(char* longUrl) {
    return longUrl;
}

/** Decodes a shortened URL to its original URL. */
char* decode(char* shortUrl) {
    return shortUrl;
}

// Your functions will be called as such:
// char* s = encode(s);
// decode(s);
``` 



## 点评
在中等题中通过率最高的几道之一，虽然刷过去很简单，但其实很难。加密问题很复杂，题解的几种解法也不是很懂，以后有空再看看。

