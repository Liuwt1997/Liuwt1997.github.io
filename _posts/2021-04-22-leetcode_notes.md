---
layout: post
title: LeetCode题型总结
---
### 字典树（前缀树）（Trie树）

概念：是一种哈希树的变种。典型应用是用于统计，排序和保存大量的字符串（但不仅限于字符串），所以经常被搜索引擎系统用于文本词频统计。

<div align="center">
    <img src="/images/post/leetcode_notes/Trie.png" width="50%" height="50%">
</div>

1、根节点不包含字符，除根节点外每一个节点都只包含一个字符；  
2、从根节点到某一节点，路径上经过的字符连接起来，为该节点对应的字符串；  
3、每个节点的所有子节点包含的字符都不相同。
优点：利用字符串的公共前缀来减少查询时间，最大限度地减少无谓的字符串比较，查询效率比哈希树高。  

    208.实现前缀树

### 动态规划

状态定义:dp[i]代表什么意思？  
状态的转移：dp[i]=dp[i-1]+dp[i-2]......  
初始值：dp[0]、dp[1]等  

无后效性：当前的状态确定后，之后的状态转移与之前的状态无关

    91.解码方法：考虑清楚边界条件
    363.矩形区域不超过K的最大数值和：暴力+状态压缩
    368.最大整除子集：求方案数的题目多开一个数组记录状态从何转移而来，如g[i]定义为dp[i]是由哪个下标的状态转移而来，如果dp[i]=dp[j]+1。则有g[i]=j
    877.石子游戏
    887.鸡蛋掉落：经典高楼扔鸡蛋问题
    1035.不相交的线：最长公共子序列
    1269.停在原地的方案数

### 异或运算

    1310.子数组异或查询：前缀异或
    1486.数组异或操作
    1720.解码异或后的数组
    1734.解码异或后的排列

### 前缀和

    523.连续的子数组和
    525.连续数组：把原数组转换一下
