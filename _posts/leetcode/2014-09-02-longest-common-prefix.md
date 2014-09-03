---
layout: post
title: Leetcodelongest-common-prefix
description: No more description
category: Leetcode
---

*Subject* **[longest-common-prefix](https://oj.leetcode.com/problems/longest-common-prefix/)**

> Write a function to find the longest common prefix string amongst an array of strings.

*Solution:*

``` c++
class Solution {
public:
    string longestCommonPrefix(vector<string> &strs) {
        string ret;
        if(strs.size() < 1)
            return ret;
        int idx = 0;
        char ch;
        while(2) {
            if(idx == strs[0].length()) {
                return idx ? strs[0].substr(0, idx) : "";
            }
            ch = strs[0][idx];
            for(int i = 1; i<strs.size(); ++i) {
                if(strs[i].length() == idx || strs[i][idx] != ch) {
                    return idx ? strs[0].substr(0, idx) : "";
                }
            }
            ++idx;
        }
    }
};

```
