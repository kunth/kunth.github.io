---
layout: post
title: Leetcode valid-sudoku
description: No more description
category: Leetcode
---

*Subject* **[valid-sudoku](https://oj.leetcode.com/problems/valid-sudoku/)**

*Solution:*

``` c++
class Solution {
private:
    bool rowArr[9], colArr[9], nineGrid[9];
    bool checkRow(vector<vector<char> > &board, int row){
        if(rowArr[row])
            return true;
        vector<bool>vec(10, false);
        for(int i = 0; i<9; ++i) {
            if(board[row][i]=='.')
                    continue;
            if(vec[board[row][i]-'0'])
                return false;
            vec[board[row][i]-'0'] = true;
        }
        rowArr[row] = true;
        return true;
    }
    bool checkCol(vector<vector<char> > &board, int col) {
        if(colArr[col])
            return true;
        vector<bool>vec(10, false);
        for(int i = 0; i<9; ++i) {
            if(board[i][col]=='.')
                    continue;
            if(vec[board[i][col]-'0'])
                return false;
            vec[board[i][col]-'0'] = true;
        }
        colArr[col] = true;
        return true;
    }
    bool checkNineGrid(vector<vector<char> > &board, int row, int col) {
        int cnt = (row / 3)*3 + col / 3;
        if(nineGrid[cnt])
            return true;
        vector<bool>vec(10, false);
        for(int i = row / 3 * 3; i <= row / 3 * 3  + 2; ++i) {
            for(int j = col / 3 * 3; j <= col / 3 * 3 + 2; ++j) {
                if(board[i][j]=='.')
                    continue;
                if(vec[board[i][j]-'0'])
                    return false;
                vec[board[i][j]-'0'] = true;
            }
        }
        return true;
    }
public:
    bool isValidSudoku(vector<vector<char> > &board) {
        memset(rowArr, false, sizeof(rowArr));
        memset(colArr, false, sizeof(colArr));
        memset(nineGrid, false, sizeof(nineGrid));
        for(int i = 0; i<9; ++i) {
            for(int j = 0; j<9; ++j) {
                if(board[i][j]!='.') {
                    if(!checkRow(board, i) || !checkCol(board, j) || !checkNineGrid(board, i, j))
                        return false;
                }
            }
        }
        return true;
    }
};

```
