# LINK:
- [[D - Unicyclic Components (atcoder.jp)](https://atcoder.jp/contests/abc292/tasks/abc292_d)]

# IMPLEMENTATION:
```python
import sys  
  
class DSU:  
    def __init__(self, n):  
        self.parent = list(range(n))  
        self.rank = [0] * n  
  
    def find(self, node):  
        if self.parent[node] != node:  
            self.parent[node] = self.find(self.parent[node])  
        return self.parent[node]  
  
    def union(self, a, b):  
        leader_a, leader_b = self.find(a), self.find(b)  
        if leader_a == leader_b:  
            return        if self.rank[leader_a] < self.rank[leader_b]:  
            self.parent[leader_a] = leader_b  
        elif self.rank[leader_a] > self.rank[leader_b]:  
            self.parent[leader_b] = leader_a  
        else:  
            self.parent[leader_b] = leader_a  
            self.rank[leader_a] += 1  
  
  
inp, out, flush = sys.stdin.readline, sys.stdout.write, sys.stdout.flush  
  
n, m = map(int, inp().split())  
graph, ed = DSU(n), list()  
for _ in range(m):  
    v, u = map(int, inp().split())  
    ed.append(v - 1)  
    graph.union(v - 1, u - 1)  
nodes, edges = [0] * n, [0] * n  
for i in range(n):  
    nodes[graph.find(i)] += 1  
for j in range(m):  
    edges[graph.find(ed[j])] += 1  
if nodes == edges:  
    out(f'Yes\n')  
else:  
    out(f'No\n')
```