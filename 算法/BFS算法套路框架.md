# BFS算法套路框架（本质：在一幅图中找到从起点start到target的最近距离）

# 目录
  - [1. 常见场景](#1-常见场景)
  - [2. 框架](#2-框架)
  - [3. 例题](#3-例题)
  - [4. 双向BFS](#2-双向BFS)


## 1. 常见场景
- （1）走迷宫。
- （2）有两个单词，通过替换字母把其中一个变成另一个，每次只能替换一个字母。

## 2. 框架
  - **注意：C++要获取队首元素并且移除的话是分为两个步骤：先front()获取队首元素，再pop()移除队首元素**
  ```cpp
    int BFS(Node start, Node target) {
      Queue<Node> q;  // 核心数据结构
      unordered_set<Node> visited;  // 避免走回头路

      q.push(start);  // 将起点加入队列
      visited.insert(start);
      int step = 0;  // 记录扩散的步数

      while(!q.empty()) {
        int sz = q.size();
        /* 将当前队列中的所有节点向四周扩散 */
        for(int i = 0;i < sz; i++) {
          // 注
          Node cur = q.front(); // 获取队首元素
          q.pop();              // 移除队首元素
          if(cur is target) return step;
          for(Node x : cur.adj())  {
            if(x not in visited) {
              q.push(cur);
              visited.insert(cur);
            }
          }
        }
      }
    }
  ```

## 3. 例题
  

## 4. 双向BFS
