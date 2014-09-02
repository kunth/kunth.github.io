---
layout: post
title: 【Leetcode】merge-intervals
description: No more description
category: Leetcode
---

[merge-intervals](https://oj.leetcode.com/problems/merge-intervals/)

> Given a collection of intervals, merge all overlapping intervals.

> For example,
> Given `[1,3]`,`[2,6]`,`[8,10]`,`[15,18]`,
> return `[1,6]`,`[8,10]`,`[15,18]`.

**Solution**

```c++
/**
 * Definition for an interval.
 * struct Interval {
 *     int start;
 *     int end;
 *     Interval() : start(0), end(0) {}
 *     Interval(int s, int e) : start(s), end(e) {}
 * };
 */

bool predicate(const Interval& lhs, const Interval& rhs) {
    if(lhs.start == rhs.start) {
        return lhs.end < rhs.end;
    }
    return lhs.start < rhs.start;
}

class Solution {
public:
    vector<Interval> merge(vector<Interval> &intervals) {
        vector<Interval> ans;
        if(intervals.empty()) {
            return ans;
        }
        sort(intervals.begin(), intervals.end(), predicate);
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
