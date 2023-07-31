# Link:
[D - Tying Rope (atcoder.jp)](https://atcoder.jp/contests/abc293/tasks/abc293_d)

# initial thoughts:
- [?] If we think each rope as a node of a graph with 2 edges of blue and red color each, then the problem boils down into count the number of cycles in a graph

# OBSERVATIONS:
- DSU structure with cycle detection when 2 elements with same parent are introduced

# IMPLEMENTATION:
```python
class DSU:  
    def __init__(self, n):  
        self.parent = [i for i in range(n)]  
        self.rank = [0] * n  
        self.groups = n  
  
    def find(self, a):  
        if self.parent[a] != a:  
            self.parent[a] = self.find(self.parent[a])  
        return self.parent[a]  
  
    def union(self, a, b):  
        leader_a, leader_b = self.find(a), self.find(b)  
        if leader_b == leader_a:  
            return True        if self.rank[leader_a] > self.rank[leader_b]:  
            self.parent[leader_b] = leader_a  
  
        elif self.rank[leader_a] < self.rank[leader_b]:  
            self.parent[leader_a] = leader_b  
  
        else:  
            self.parent[leader_b] = leader_a  
            self.rank[leader_a] += 1  
        self.groups -= 1  
        return False  
  
  
def solve():  
    n, m = map(int, inp().split())  
    ropes = DSU(n)  
    cycles = 0  
    for _ in range(m):  
        a, _, b, _ = inp().split()  
        cycles += ropes.union(int(a) - 1, int(b) - 1)  
    out(f'{cycles} {ropes.groups - cycles}\n')
```