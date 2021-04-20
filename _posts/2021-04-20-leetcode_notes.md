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