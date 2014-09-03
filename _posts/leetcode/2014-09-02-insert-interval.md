---
layout: post
title: 【Leetcode】insert-interval
description: No more description
category: Leetcode
---

*Subject* **[insert-interval](https://oj.leetcode.com/problems/insert-interval/)**

*Solution:*

``` c++
bool cmp(const Interval& lhs, const Interval& rhs){
    if(lhs.start == rhs.start) {
        return lhs.end < rhs.end;
    }
    return lhs.start < rhs.start;
}
 
class Solution {
public:
    vector<Interval> insert(vector<Interval> &intervals, Interval newInterval) {
        vector<Interval>ans;
        intervals.push_back(newInterval);
        sort(intervals.begin(), intervals.end(), cmp);
        ans.push_back(intervals[0]);
        for(int i = 1; i < intervals.size(); ++i) {
            if(intervals[i].start <= ans.back().end) {
                ans[ans.size()-1].end = max(intervals[i].end, ans.back().end);
            } else {
                ans.push_back(intervals[i]);
            }
        }
        return ans;
    }
};
```
