## Summary:
Given a sequence of strings, check whether they can be re-arranged into forming a sequence in which the next string can be obtained by changing one letter from the current word.

# INTUITION:
- Define a graph with nodes as the words, there exist a edge only if the nodes difference by at-most 1 character.
- Now choose a starting point and find if all other nodes can be visited from it.

# IMPLEMENTATION:
```python
def solve():

    n, m = map(int, inp().split())

    word_list = [inp().strip() for _ in range(n)]

    graph = [[] for _ in range(n)]

    for i in range(n):

        for j in range(1, n):

            if sum(a != b for a, b in zip(word_list[i], word_list[j])) == 1:

                graph[i].append(j), graph[j].append(i)

  

    def bfs(node):

        q, visited = [node], [False] * n

        visited[node] = True

        for node in q:

            for nei in graph[node]:

                if not visited[nei]:

                    visited[nei] = True

                    q.append(nei)

        return all(visited)

    for i in range(n):

        if bfs(i):

            print('Yes')

            return

    print('No')
```