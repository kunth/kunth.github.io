---
layout: post
title: Leetcode clone-graph
description: No more description
category: Leetcode
---

*Subject* **[clone-graph](https://oj.leetcode.com/problems/clone-graph/)**

The first dfs is to create all the nodes, the second is to maintain the relationships between nodes.

**Taste the delicious dfs**

*Solution:*

``` c++
/**
 * Definition for undirected graph.
 * struct UndirectedGraphNode {
 *     int label;
 *     vector<UndirectedGraphNode *> neighbors;
 *     UndirectedGraphNode(int x) : label(x) {};
 * };
 */
class Solution {
private:
    unordered_map<UndirectedGraphNode*, UndirectedGraphNode*>dm;
    UndirectedGraphNode* dfs_create(UndirectedGraphNode* node) {
        if(!dm[node]) {
            dm[node] = new UndirectedGraphNode(node->label);
            for(int i = 0; i<node->neighbors.size(); ++i) {
                dfs_create(node->neighbors[i]);
            }
        }
        return dm[node];
    }

    void dfs_completeNeighbors(UndirectedGraphNode* node) {
        if(dm[node]->neighbors.empty()) {
           for(int i = 0; i<node->neighbors.size(); ++i) {
               dm[node]->neighbors.push_back(dm[node->neighbors[i]]);
               dfs_completeNeighbors(node->neighbors[i]);
           }
        }
    }
public:
    UndirectedGraphNode *cloneGraph(UndirectedGraphNode *node) {
        if(!node)
            return NULL;
        dm.clear();
        UndirectedGraphNode* ret = dfs_create(node);
        dfs_completeNeighbors(node);
        return ret;
    }
};
```
