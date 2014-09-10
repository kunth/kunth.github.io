---
layout: post
title: Leetcode substring-with-concatenation-of-all-words
description: No more description
category: Leetcode
---

*Subject* **[substring-with-concatenation-of-all-words](https://oj.leetcode.com/problems/substring-with-concatenation-of-all-words/)**

*Solution:*

The words in L may not be unique, e.g.
<img src = "/images/substring-with-concatenation-of-all-words.png" alt="" />

``` c++
class Solution {
public:
    vector<int> findSubstring(string S, vector<string> &L) {
        vector<int>ans;
        if(S.empty() || L.empty())
            return ans;
        int wordSz = L.size(), wordLen = L[0].length();
        int len = wordSz * wordLen;
        string word;
        bool tag;
        unordered_map<string, int>dm, lm;
        for(int i = 0; i<wordSz; ++i){
            ++lm[L[i]];
        }
        for(int i = 0; i + len <= S.length(); ++i) {
            dm.clear();
            tag = true;
            for(int j = 0; j < wordSz; ++j) {
                word = S.substr(i+j*wordLen, wordLen);
                if(dm[word] < lm[word]) {
                    ++dm[word];
                }else {
                    tag = false;
                    break;
                }
            }
            if(tag) {
                ans.push_back(i);
            }
        }
        return ans;
    }
};
```
